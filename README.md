# check_linux_mtu
Nagios and Icinga2 plugin to check the MTU of an interface on a Linux host and throw and alarm if the configured MTU deviates from the desired MTU.

## Dependencies
This plugin requires:
  - Python3

## How it works
The plugin reads the configured MTU from `/sys/class/net/<interface-name>/mtu`. An alarm is raised if the configured MTU does not match the desired MTU.

## Performance data
This plugin provides the following metrics:
  - `mtu`: configured MTU
  - `desired_mtu`: desired MTU

## Usage
See the examples below or execute the plugin with -h/--help.

## Examples
Just provide the configured MTU:
```
./check_linux_mtu -d eth0
CONFIGURED MTU OK - Configured value is 1500. | mtu=1500
```

Check that the configured MTU matches the desired MTU:
```
./check_linux_mtu -d eth0 --desired-mtu 9000
CONFIGURED MTU CRTITCAL - Configured value is 1500, while the desired value is 9000 | mtu=1500 desired_mtu=9000
```
