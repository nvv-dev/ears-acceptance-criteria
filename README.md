# ears-acceptance-criteria

> Requisitos que un tester puede convertir en pruebas sin preguntarle a nadie.

**Criterios de aceptación EARS** · Skill para agentes de código de la comunidad [nvvdev](https://github.com/nvv-dev). Funciona en Claude Code como plugin o como skill suelta, y en cualquier agente compatible con el formato abierto [`SKILL.md`](https://agentskills.io).

*English summary at the end.*

## Qué hace

Convierte requisitos vagos en criterios con los cinco patrones EARS ("Cuando X, el sistema debe Y", "Mientras…", "Si… entonces…", "Donde…"), cubre los caminos tristes, marca lo que hay que aclarar y asigna a cada tarea el comando que demuestra que está hecha.

## Objetivo

Specs verificables y tareas que el agente puede probar por sí mismo antes de abrir el PR.

## Cuándo usarla

- Al escribir historias de usuario o specs
- Al revisar una spec antes de planear

## Cuándo no

- Cambios internos sin comportamiento visible

## Ejemplo

```text
Escribe los criterios de aceptación en formato EARS para el flujo de recuperación de contraseña.
```

## Cómo se activa

Esta skill **se activa sola**: Claude Code lee su descripción y la carga cuando la tarea coincide. También puedes pedirla por nombre ("usa la skill ears-acceptance-criteria") o invocarla con `/ears-acceptance-criteria:ears-acceptance-criteria` (plugin) o `/ears-acceptance-criteria` (copiada a `.claude/skills/`).

## Instalación

### Opción 1: Claude Code, como plugin (recomendada)

Dentro de Claude Code:

```text
/plugin marketplace add nvv-dev/claude-plugins
/plugin install ears-acceptance-criteria@nvvdev
```

La primera línea agrega el catálogo de nvvdev una sola vez; la segunda instala esta skill. Si prefieres el paquete completo, instala `dev-workflow@nvvdev` en su lugar (incluye esta skill y las demás de [dev-workflow](https://github.com/nvv-dev/dev-workflow)); no instales los dos a la vez.

### Opción 2: Claude Code, copiando la skill

Para un solo proyecto (se comparte con tu equipo por git):

```bash
git clone --depth 1 https://github.com/nvv-dev/ears-acceptance-criteria.git /tmp/ears-acceptance-criteria
mkdir -p .claude/skills
cp -R /tmp/ears-acceptance-criteria/skills/ears-acceptance-criteria .claude/skills/
```

Para todos tus proyectos, cópiala en `~/.claude/skills/` en lugar de `.claude/skills/`.

### Opción 3: otros agentes

Copia la carpeta `skills/ears-acceptance-criteria/` en la carpeta de skills de tu agente (cada agente documenta la suya). Con la CLI [skills](https://github.com/vercel-labs/skills) de Vercel Labs:

```bash
DISABLE_TELEMETRY=1 npx skills add nvv-dev/ears-acceptance-criteria
```

### Verificar

Abre una sesión nueva y pregunta "¿qué skills tienes disponibles?"; `ears-acceptance-criteria` debe aparecer. Con el plugin, `/plugin` la muestra como instalada.

### Actualizar o desinstalar

- Plugin: `/plugin marketplace update nvvdev` para actualizar; `/plugin uninstall ears-acceptance-criteria@nvvdev` para quitarla.
- Copia manual: repite la copia para actualizar, o borra la carpeta `.claude/skills/ears-acceptance-criteria`.

Antes de instalar cualquier skill, incluida esta, conviene leerla: es un solo archivo, [`skills/ears-acceptance-criteria/SKILL.md`](skills/ears-acceptance-criteria/SKILL.md). Ver [vetting-external-skills](https://github.com/nvv-dev/vetting-external-skills).

## Contenido

| Ruta | Qué es |
|---|---|
| `skills/ears-acceptance-criteria/SKILL.md` | La skill: instrucciones en inglés para que los escáneres de seguridad las analicen completas; el agente responde en tu idioma |
| `.claude-plugin/plugin.json` | Manifiesto para instalarla como plugin |
| `.github/workflows/` | Validación de estructura y escaneo con SkillSpector en cada cambio |

## Contribuir

Este repo se **genera** desde [nvv-dev/dev-workflow](https://github.com/nvv-dev/dev-workflow), donde vive la versión canónica. Abre issues y PRs allí. La mejor contribución es un caso real en la sección *Known failures* de la skill, con la regla que lo evita.

## Origen

Escrita desde cero por nvvdev. Inspirada en: [Hainrixz/the-architect](https://github.com/Hainrixz/the-architect) (EARS criteria, verification command per step, clarification gates); EARS was created by Alistair Mavin et al..

## Licencia

MIT.

---

## English

**ears-acceptance-criteria** — Turns vague requirements into EARS acceptance criteria and gives every task a verification command.

Install in Claude Code with `/plugin marketplace add nvv-dev/claude-plugins` and `/plugin install ears-acceptance-criteria@nvvdev`, or copy `skills/ears-acceptance-criteria/` into `.claude/skills/` (project) or `~/.claude/skills/` (personal). Other agents: copy the folder into their skills directory, or run `DISABLE_TELEMETRY=1 npx skills add nvv-dev/ears-acceptance-criteria`. Loads automatically when the task matches its description. Canonical source: [nvv-dev/dev-workflow](https://github.com/nvv-dev/dev-workflow). License: MIT.
