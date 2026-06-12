---
title: "LIRC UART receiver problem"
date: 2012-03-24
forum: Mythbuntu
---

### Post by BiOzZ on 2012-03-24
i made a UIRT receiver and transmitter ... the transmitter hooked to DTR and receiver hooked to DCD pulled up via a 4.7K resistor from RTS and powered form a USB port's 5V rail ... i tested the receiver with a logic probe plugged in to the computer and my setup seams fine

and the transmitter works fine with my Motorola box 

i have it set up to use a Hauppauge remote

here is my hardware.conf file

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge"
REMOTE_MODULES="lirc_dev lirc_serial"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Comcast"
TRANSMITTER_MODULES="lirc_dev lirc_serial"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc1"
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="motorola/dctxxxx.conf"
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""

```

when i try mode2 i get 

```
mode2: could not get file information for /dev/lirc
mode2: default_init(): No such file or directory

```

when i try sudo mode2 -d /dev/lirc0
i get 
```
mode2: could not open /dev/lirc0
mode2: default_init(): Device or resource busy

```
when i try irw i get a hole lot of nothing

when i try cat /dev/ttyS0 i get

```
cat: /dev/ttyS0: Input/output error

```
same in root

when i try mode2 -d /dev/ttyS0 -H uirt2_raw

i get 
```
mode2: uirt2_raw: could not reset tty

```

im flat out of ideas at this point can you please help me?

```
biozz@MythBuntu:/etc/lirc$ lircd -v
lircd 0.9.0

biozz@MythBuntu:/etc/lirc$ uname -a
Linux MythBuntu 3.0.0-16-generic #29-Ubuntu SMP Tue Feb 14 12:49:42 UTC 2012 i686 i686 i386 GNU/Linux

```

if that helps anyone

---

