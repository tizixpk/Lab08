# Tarea: Procesos - PowerShell

Una vez vistos los procesos, vamos a realizar una serie de scripts que nos permitirán obtener información acerca de los procesos y realizar acciones sobre ellos.

``` powershell
Get-Process
Stop-Process
```

Referencias:

* [Get-Process](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.management/get-process?view=powershell-6)
* [Stop-Process](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.management/stop-process?view=powershell-6)


# Ejercicio 1

Realiza un Script que obtenga el los detalles del proceso cuyo nombre sea `MicrosoftEdge`

## Respuesta 1:
Get-Process -Name MicrosoftEdge | Select-Object *

# Ejercicio 2

Realiza un Script que muestre todos los procesos cuyo nombre sea `svchost`

## Respuesta 2:
Get-Process -Name svchost

¿Qué hace este proceso? ¿Porqué hay tantos?
**svchost.exe es un proceso genérico de alojamiento de servicios en Windows. Es fundamental para la ejecución de servicios del sistema operativo y servicios de red. Windows utiliza múltiples instancias de svchost.exe para separar los servicios y mejorar la estabilidad y seguridad del sistema. Cada instancia de svchost.exe agrupa servicios relacionados, lo que explica por qué hay múltiples instancias ejecutándose simultáneamente.**

# Ejercicio 3

Realiza un Script que muestre la ruta al ejecutable del proceso de `MicrosoftEdge`

## Respuesta 3:
Get-Process -Name MicrosoftEdge | Select-Object -ExpandProperty Path

# Ejercicio 4

Realiza un Script que detenga el proceso del Bloc de notas

## Respuesta 4:
Stop-Process -Name notepad

# Ejercicio 5

Realiza un script que muestre **tan solo** el tiempo de la CPU de un proceso dado (por ejemplo `notepad`). 

## Respuesta 5:
(Get-Process -Name notepad).CPUTime

# Ejercicio 6

¿Qué muestra el siguiente script?

## Respuesta 6:
** Obtiene una lista de todos los procesos en ejecución en el sistema, Filtra los procesos para aquellos que tienen un título de ventana principal no nulo o vacío. Esto significa que solo se mostrarán los procesos que tienen una ventana visible y Formatea la salida de los procesos seleccionados mostrando el ID del proceso (id), el nombre del proceso (name) y el título de la ventana principal (mainWindowTitle) en formato de lista.**

``` powershell
Get-Process | where {$_.mainWindowTitle} | Format-List id, name, mainwindowtitle 
```
