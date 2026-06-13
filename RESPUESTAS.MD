1. ¿Por qué necesitamos Loki además de Prometheus si ya tenemos /metrics?
Prometheus guarda métricas (números: CPU, memoria, peticiones). Loki guarda logs (texto: qué pasó y por qué). Las métricas te dicen que algo falló; los logs te dan el detalle y la causa. Son señales distintas y necesitan herramientas distintas.

2. ¿Qué ventaja aporta que las fuentes de datos estén aprovisionadas como código?
Que se recrean solas al arrancar Grafana, sin configurarlas a mano. Son versionables en Git, iguales para todo el equipo y libres de errores humanos. Eso es Infraestructura como Código.

3. ¿Por qué difieren "CPU contenedor" y "CPU host"? ¿Cuál usar para alertar sobre una app?
El contenedor mide solo esa app; el host mide la máquina entera (todos los procesos). Por eso pueden dar valores muy distintos. Para alertar sobre una app concreta uso la métrica por contenedor.

4. ¿Diferencia entre evaluation interval y pending period?
El evaluation interval es cada cuánto Grafana revisa la condición (ej. 10s). El pending period es cuánto tiempo debe seguir cumpliéndose antes de pasar a Firing (ej. 30s), para evitar falsas alarmas por picos cortos.