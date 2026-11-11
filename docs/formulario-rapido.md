# 📐 Formulario · Diseño de Circuitos (Unidad 1)

> Todo lo que conviene tener a mano en una sola página. Los detalles y ejemplos están en cada semana.

[⬅️ Volver al índice](../README.md)

---

## 1. Conversiones y códigos (Semana 1)

| Qué | Regla |
|---|---|
| Decimal → binario | Dividir entre 2 y leer los restos **de abajo hacia arriba** |
| Binario → hexadecimal | Grupos de **4 bits** desde la derecha |
| Binario → octal | Grupos de **3 bits** desde la derecha |
| Negativo en complemento a dos | **Invertir los bits y sumar 1** |
| Rango con n bits (con signo) | de −2ⁿ⁻¹ a 2ⁿ⁻¹ − 1 (4 bits: −8 a +7 · 8 bits: −128 a +127) |
| Gray | Método del espejo: copiar al revés, anteponer 0 arriba y 1 abajo |
| ASCII | 7 bits = 128 caracteres (A = 65 = 0x41) |

## 2. Las 7 compuertas (Semana 1)

| Compuerta | Expresión | Vale 1 cuando… |
|---|:---:|---|
| NOT | `A'` | la entrada es 0 |
| AND | `A·B` | **todas** las entradas son 1 |
| OR | `A+B` | **al menos una** entrada es 1 |
| NAND | `(A·B)'` | **no** todas son 1 |
| NOR | `(A+B)'` | **ninguna** es 1 |
| XOR | `A⊕B` | las entradas son **distintas** |
| XNOR | `(A⊕B)'` | las entradas son **iguales** |

**Chip 74LS08:** 4 AND de 2 entradas · DIP-14 · pin 14 = +5 V · pin 7 = GND.

## 3. Álgebra de Boole (Semana 2)

**Precedencia:** NOT → AND → OR.

| Teorema | Forma OR | Forma AND |
|---|:---:|:---:|
| Identidad | `X + 0 = X` | `X·1 = X` |
| Complemento | `X + X' = 1` | `X·X' = 0` |
| Elemento nulo | `X + 1 = 1` | `X·0 = 0` |
| Idempotencia | `X + X = X` | `X·X = X` |
| Involución | `(X')' = X` | |
| Absorción | `X + XY = X` | `X(X+Y) = X` |
| Abs. del complemento | `X + X'Y = X + Y` | `X(X'+Y) = XY` |
| Adyacencia | `XY + XY' = X` | `(X+Y)(X+Y') = X` |
| Consenso | `XY + X'Z + YZ = XY + X'Z` | `(X+Y)(X'+Z)(Y+Z) = (X+Y)(X'+Z)` |
| Distributiva | `X(Y+Z) = XY + XZ` | `X + YZ = (X+Y)(X+Z)` |

**De Morgan:** `(AB)' = A' + B'` · `(A+B)' = A'B'` → «rompe la barra, cambia el operador».

## 4. Formas canónicas (Semana 2)

| Forma | Se leen las filas con… | Se une con… | Ejemplo |
|---|:---:|:---:|---|
| **SOP** (`Σm`) | **F = 1** | OR de minitérminos | `Σm(3,5,6,7)` |
| **POS** (`ΠM`) | **F = 0** | AND de maxitérminos | `ΠM(0,1,2,4)` |

- Minitérmino: variable en 1 → sin complemento; en 0 → complementada.
- Maxitérmino: variable en 0 → sin complemento; en 1 → complementada.
- `Mᵢ = (mᵢ)'`. Los índices de ΠM son los que **faltan** en Σm.

## 5. Mapas de Karnaugh (Semana 3)

| Regla | |
|---|---|
| Orden de filas/columnas | **Gray**: 00, 01, 11, 10 |
| Tamaño de grupo | 2ᵏ celdas (elimina k variables) |
| Forma | Rectangular, sin L ni diagonales |
| Tamaño | Lo más grande posible |
| Bordes | El mapa se enrolla (esquinas incluidas) |
| Leer grupo en SOP | constante en 1 → `A` · constante en 0 → `A'` · cambia → desaparece |
| Leer grupo en POS | lectura **invertida**: 0 → `A` · 1 → `A'`, y se unen con suma |
| Indiferentes (X) | Cuentan como 1 si agrandan un grupo; nunca se agrupan solas |

## 6. NAND / NOR (Semana 3)

| Función | Solo NAND | Solo NOR |
|:-:|:-:|:-:|
| NOT | `(A·A)'` | `(A+A)'` |
| AND | `((AB)')'` | `(A'+B')'` |
| OR | `(A'·B')'` | `((A+B)')'` |

**SOP mínima → NAND-NAND (7400, 7410)** · **POS mínima → NOR-NOR (7402)**. El literal que aparece solo entra complementado.

**Conversión:** doble negación → De Morgan → cada paréntesis es una NAND.

## 7. Circuitos aritméticos (Semana 4)

| Circuito | Fórmulas |
|---|---|
| Semisumador | `S = A⊕B` · `C = A·B` |
| Sumador completo | `S = A⊕B⊕Cin` · `Cout = AB + A·Cin + B·Cin` |
| Resta | `A − B = A + (−B)` · M = 1: `B⊕M` y `Cin = 1` |
| Overflow | `V = C3 ⊕ C4` (acarreo que entra ≠ acarreo que sale) |
| Retardo ripple | `≈ 2·n·10 ns` (4 bits: 80 ns · 16: 320 ns · 32: 640 ns) |
| Comparador `A = B` | XNOR por bit y AND de todas |
| Comparador `A > B` | Desde la izquierda: el primer bit distinto decide |

**Chips mencionados:** 7400 (NAND) · 7402 (NOR) · 7404 (NOT) · 7408 (AND) · 7410 (NAND de 3) · 7411 (AND de 3) · 7432 (OR) · 7483 (sumador de 4 bits) · 7485 (comparador).

---

[⬅️ Volver al índice](../README.md)
