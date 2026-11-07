# ALU de 4 bits en Logisim

Unidad aritmético-lógica de 4 bits que suma, resta y compara dos números, y muestra los resultados en displays de 7 segmentos. Proyecto final de **Diseño Digital** (Ingeniería de Sistemas, Universidad del Norte, 2026).

**Autores:** Jesús Contreras, Victor Mendoza y Juan Narváez

## Qué hace

- **Suma** de dos números de 4 bits con propagación de acarreo.
- **Resta** usando complemento a 2, reutilizando el sumador, con detección de signo.
- **Comparación** de A y B: enciende un LED para A = B, A > B o A < B.
- **Display de 7 segmentos** para ver el resultado de la suma o de la resta.
- **Multiplexor de selección** para elegir qué operación se muestra.

## Cómo está construido

El diseño es jerárquico: 11 subcircuitos que se reutilizan entre sí.

| Módulo | Función |
|---|---|
| `Main` | Circuito principal que conecta todo |
| `sumador_completo` → `sumador_4bit` | Sumador de 1 bit, encadenado 4 veces |
| `restador_completo` → `restador_4bit` | Resta por complemento a 2 |
| `comparador` → `comparador_4bit` | Lógica A = B, A > B, A < B |
| `led_comparador` | Lleva el resultado de la comparación a los LEDs |
| `selector` | Multiplexor que elige la operación a mostrar |
| `suma_7segmentoss`, `resta_7segmentoss` | Decodificadores a 7 segmentos |

Ecuación del sumador completo: `S = A ⊕ B ⊕ Cin`, `Cout = A·B + Cin·(A ⊕ B)`.

## Cómo abrirlo

1. Instala [Logisim-evolution](https://github.com/logisim-evolution/logisim-evolution) 4.0 o superior.
2. Abre `alu_4bits.circ`.
3. Cambia los pines de entrada A y B con la herramienta de mano y mira el resultado en los displays y LEDs.

## Archivos

- `alu_4bits.circ`: el circuito.
- `docs/presentacion.pptx`: presentación con la arquitectura, ecuaciones y conclusiones.
