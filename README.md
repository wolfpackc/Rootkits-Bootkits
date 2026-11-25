# Rootkits y Bootkits

Serie de informes en PDF sobre arranque y persistencia en Windows, escrita desde el lado del red team y con la defensa siempre a mano. Sube por la cadena de arranque, del rootkit de kernel hasta el firmware UEFI, y cada apartado cierra con un recuadro "En palabras simples" que resume la idea sin tecnicismos.

Es material de estudio. Los fragmentos de código son pseudocódigo y los comandos de las figuras son ilustrativos, no herramientas funcionales. Los conceptos son públicos y están documentados desde hace años por Kaspersky, ESET y Microsoft, entre otros.

## Informes

Están en la carpeta `informes/`.

| Archivo | Páginas | De qué trata |
|---|---|---|
| `rootkits_bootkits_bloques1-3.pdf` | 10 | Bloques 1 a 3. Del rootkit de kernel al bootkit UEFI. |
| `rootkits_bootkits_bloque4.pdf` | 7 | Bloque 4. El salto al firmware. |

### Bloques 1 a 3

- Bloque 1, rootkit de kernel: cómo intercepta el sistema (SSDT, minifiltros de archivos y DKOM), el caso de la generación TDL3 y Festi, y cómo se detecta y se restaura un kernel comprometido.
- Bloque 2, arranque BIOS/MBR: la cadena de arranque clásica, por qué interesa atacarla, el caso de Petya y NotPetya, y la defensa y detección en ese modelo.
- Bloque 3, de la BIOS a UEFI: qué cambia con UEFI y cómo funciona Secure Boot con sus bases de datos.

### Bloque 4

Qué hace vulnerable a un firmware UEFI, cómo se inyecta código en él y por qué el objetivo final es la System Management Mode (SMM), el anillo -2, a la que ni Secure Boot ni el sistema operativo llegan a ver. Incluye:

- Una clasificación de las vulnerabilidades de firmware en cuatro familias: corrupción de memoria en DXE y PEI, protección de la flash mal configurada, TOCTOU en el guion de arranque S3 y fallos en el código de SMM.
- Las dos formas de dejar código en el firmware: añadir un driver DXE nuevo o parchear un componente que ya existe.
- Por qué SMM es tan atractivo y cómo se compromete en la práctica.

Los informes atribuyen cada caso a quien lo documentó (Kaspersky, ESET y otros), y el bloque 4 termina con la lista de fuentes consultadas.

## Uso

Los informes están pensados para estudiar y para defender. Si los usas en una charla o en un curso, cita las fuentes originales que mencionan los propios informes.
