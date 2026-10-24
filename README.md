# Laboratorio 3: Diseño y Validación de Gramáticas

**Asignatura:** Teoría de la Computación (INFO1148)
**Carrera:** Ingeniería Civil en Informática
**Docente:** Marcos Lévano
**Integrantes:** José Sáez, Catalina Vergara

Este repositorio contiene los archivos de JFLAP 7.1 con la Gramática Libre de Contexto (GLC) del lenguaje de programación simplificado del laboratorio. La gramática, sus derivaciones y su análisis están explicados en el informe en PDF.

## Archivos

| Archivo | Reglas | Símbolo inicial | Uso |
|---|---|---|---|
| `GLC_Lab3.jff` | 24 | `S` | Gramática completa, con la extensión (declaración de variables). Analiza programas completos. |
| `GLC_Lab3_instr.jff` | 24 | `I` | Las mismas 24 reglas, con `I → A` como primera producción. Analiza instrucciones sueltas. |
| `GLC_Lab3_base.jff` | 20 | `S` | Gramática sin la extensión, solo para comparar. |

JFLAP 7.1 toma como símbolo inicial el lado izquierdo de la primera producción del archivo, por eso `GLC_Lab3.jff` y `GLC_Lab3_instr.jff` tienen la misma gramática pero distinto punto de partida.

## Cómo abrirlos

1. Abrir JFLAP 7.1.
2. Elegir **File → Open** y seleccionar el archivo `.jff` (o arrastrarlo a la ventana).
3. Para analizar una cadena: **Input → Brute Force Parse**, escribir la cadena de tokens en el campo *Input* y pulsar **Start**. JFLAP indica *String accepted!* o *String rejected!*. Con **Step** se dibuja el árbol de derivación.

## Codificación de símbolos

JFLAP 7.1 solo admite símbolos de un carácter, por lo que cada token del lenguaje se escribe con una letra:

| Token | JFLAP | Token | JFLAP |
|---|---|---|---|
| `Begin` | `b` | `entero` | `t` |
| `Programa` | `p` | `real` | `r` |
| `End` | `e` | identificador (ID) | `w` |
| `salida` | `o` | número (NUM) | `n` |
| `=`, `#`, `+`, `-`, `*`, `/`, `%` | iguales | comentario (COM) | `x` |

Cualquier identificador se escribe `w` y cualquier número `n`.

## Ejemplos

Con `GLC_Lab3.jff` (programas completos):

- `bpww=w#e` → `Begin Programa demo w = w # End` (aceptada)

Con `GLC_Lab3_instr.jff` (instrucciones):

- `w=w+w#` → `z = x + y #` (aceptada)
- `ow#` → `salida z #` (aceptada)
- `wn#` → `x 10 #` (rechazada)

La correspondencia completa entre la notación del informe y la de JFLAP está en la sección 2.2 e) del informe.
