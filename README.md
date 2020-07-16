# projector-installer
[![JetBrains incubator project](https://jb.gg/badges/incubator.svg)](https://confluence.jetbrains.com/display/ALL/JetBrains+on+GitHub)
 

Install, configure and run JetBrains IDEs with Projector Server on Linux or in [WSL](https://docs.microsoft.com/windows/wsl/).

## Install
To use projector-installer you need machine with Linux (or WSL) and with Python 3.6 or higher.

### install from PyPi
```bash
pip3 install projector-installer 
```

### install from wheel file 
```bash
pip3 install projector_installer-VERSION-py3-none-any.whl
```
### install from source 
```bash 
git clone https://github.com/JetBrains/projector-installer.git
cd projector-installer
pip3 install -r requirements.txt 
pip3 install .
```

### install in virtual environment

```commandline

python3 -m venv venv
source ./venv/bin/activate 
pip3 install  projector-installer 
``` 

After that the command _projector_ is available. 

_NOTE:_ In fresh Linux installations the directory ```~/.local/bin```
can be missed in the ```PATH``` variable. If the ```projector``` command
is not available after installation, try to restart the terminal.


## Quick start 
First time you run projector, it automatically starts the installation.
Just run projector and follow the instructions. 
The script will run the installed IDE with projector-server and display URL to access it. 
Open this URL in your browser and use IDE as usual.

To run IDE again use _projector run_

To install a new IDE run _projector install_ 

## Get help 
General help: ```projector --help```:
 
Command or command group help: ```projector  command --help```:
```bash
projector run --help

projector config --help
```

Subcommand help: ```projector  group subcommand --help``` to get help.

```bash
projector config add --help
```

### Shortcut commands

To simplify usage most useful commands have shortcuts. In simple cases 
(when you have the only IDE installed, or you do not run several IDE instances simultaneously) 
it is enough to use a couple of shortcut commands, such as install and run.

- find  - find available IDEs (a shortcut for 'ide find')
 
- install - install IDE (a shortcut for 'ide install')

- run - run IDE (a shortcut for 'config run')


## Details 

Script has two groups of commands:

- IDE management commands intended to manage Projector-compatible IDEs.
  All such commands are prefixed with 'ide' keyword, for example:
    
    ```bash
    projector ide find 
    ``` 
   
finds all Projector-compatible IDEs. 
 
or:

```bash
   projector ide find goland
``` 
 
finds all Projector-compatible IDEs which have 'goland' in their names.

- config commands, intended to run and manage _configurations_, for example:
    ```bash 
    projector config run goland
   ``` 
    
runs the configuration with name 'goland'


### IDE commands
`projector ide find` - display all Projector-compatible IDEs

`projector ide find pattern` - display Projector-compatible IDEs whose names match the given pattern

`projector ide list` - display all installed IDEs

`projector ide list pattern` - display Projector-compatible IDEs whose names match the given pattern

`projector ide install` - select and install IDE interactively
 
`projector ide install ide_name` - install the specified IDE

`projector ide uninstall` - uninstall IDE interactively 

`projector ide uninstall ide_name` - uninstall the specified IDE 

### Config commands 
`projector config run` - run default or interactively selected configuration with Projector
 
`projector config run configuration` - run the specified configuration

`projector config list` - list all existing configurations
 
`projector config add` - add a new configuration

`projector config edit` - change an existing configuration

`projector config edit configuration` - change the specified configuration

`projector config remove` - select configuration and remove it 

`projector config remove config_name` - remove a configuration

`projector config rename from_config_name to_config_name` - rename an existing configuration

`projector config show` - show configuration details

## Build python wheel file
```bash
python3 setup.py bundle bdist_wheel
```

## Resolving WSL issues
WSL is new technology and sometimes there are problems with network interfaces forwarding from Linux to Windows system.
(Example: https://github.com/microsoft/WSL/issues/4636)

If you have issues with accessing Projector, running in WSL from browser, try the following: 

 -  From  PowerShell, running with admin privileges run: 
 ```Get-Service LxssManager | Restart-Service```
   