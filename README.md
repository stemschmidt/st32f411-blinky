# Development environment in Docker Container for Zephyr 3.7.0 LTS3

Pre-Requisites:
- git installed
- vscode installed, with plugins "Remote Containers", "Cortex-Debug"
- Docker Desktop installed
- Segger J-Link GDB Server installed

How to use:
1. "git clone https://github.com/stemschmidt/st32f411-blinky.git"
2. "cd st32f411-blinky"
3. "code ." or open st32f411-blinky in VSCode
4. in VSCode, select "reopen folder in container" (see NOTE below)
5. after docker container has started, go to "TERMINAL" tab:
6. "west init -l application"
7. "west update" -> this will take some time to download all required modules
8. "source zephyr/zephyr-env.sh"
9. "cd application"
10. "west build -b nucleo_f411re" and wait for the build to finish...
11. on the host, launch the JLinkGDBServer (e.g "JLinkGDBServerCLExe -if swd -device nucleo_f411re -vd")
12. on the host, launch the JLinkRTTViewer to see debug log (e.g "JLinkRTTViewer", select "Connection to J-Link" -> "Existing session")
13. Select "Run and Debug" icon in activity bar in VSCode --> Download binary and start debugging by launching "JLink"

NOTE:
There is an issue with the order in which the plugins are loaded. A warning appears asking you to reload the window.
After reloading the window you will have to launch bash again: '$ bash'
