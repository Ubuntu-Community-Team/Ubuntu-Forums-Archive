---
title: "lirc irman serial not working"
date: 2009-05-29
forum: Multimedia Software
---

### Post by dmclennan on 2009-05-29
Hi,
I've run out of ideas or input from install lirc Hardy, mythtv and lirc documentation and other posts on this forum.  I would appreciate any help or advice (thanks in advance) to get this working.  I have a Home Electronic Serial Infrared receiver.  This worked fine on Windows using serial port, Girder and UIR/IRMAN plugin. From this I know the serial port and remote are functioning and plugged in, etc. I have also verified BIOS has COM1 at 0x3f8, irq4, 16550A, which matches /dev/ttyS0.

I've installed lirc, selected homebrew serial receiver, and tried various combinations of device = /dev/ttyS0, /dev/lirc0 and driver = default, irman, blank....  Start/stop /etc/init.d/lirc.  The IR receiver has a red/green light that never lights up, telling me that it is not connected to the serial port. When I run irw and press remote keys, there is no response. I've also tried a couple different remotes.

Seems like the lirc is not talking to the serial port /dev/ttyS0.  I read somewhere (Feisty instlal lirc page?) that Ubuntu kernial serial port needs to be disabled, setserial UART none, but this is not referenced in the Hardy install guide. This may have been resoved with Jaunty.

For reference, a few config files, etc:

$ sudo /etc/init.d/lirc restart
 * Stopping remote control daemon(s): LIRC                                                                                       [ OK ] 
 * Loading LIRC modules                                                                                                          [ OK ] 
 * Starting remote control daemon(s) : LIRC                                                                                      [ OK ] 


$ dmesg | grep tty
[    0.004000] console [tty0] enabled
[    2.400584] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.400938] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

$ dmesg | grep lirc
[  545.121833] lirc_dev: IR Remote Control driver registered, major 61 
[  545.624051] lirc_serial: auto-detected active high receiver
[  545.624056] lirc_dev: lirc_register_plugin: sample_rate: 0




# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Home-brew (16x50 UART compatible serial port)"
#REMOTE_MODULES="lirc_dev lirc_serial"
REMOTE_MODULES=""
REMOTE_DRIVER="irman"
REMOTE_DEVICE="/dev/lirc0"
#REMOTE_DEVICE="/dev/ttyS0"
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"
#LOAD_MODULES="false"

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

/var/log/daemon.log:
May 29 15:55:33 don-desktop lircd-0.8.4a[7414]: accepted new client on /dev/lircd
May 29 15:55:33 don-desktop lircd-0.8.4a[7414]: could not open /dev/lirc0
May 29 15:55:33 don-desktop lircd-0.8.4a[7414]: irman_init(): Unknown error 515 
May 29 15:55:33 don-desktop lircd-0.8.4a[7414]: Failed to initialize hardware
May 29 16:06:56 don-desktop lircd-0.8.4a[7414]: removed client

Thank you
Don

---

### Post by lovinglinux on 2009-05-29
Try using 

```
LOAD_MODULES="lirc_dev lirc_serial"
```

Restart lirc and check if it works.

Also check if the file /etc/lirc/lircd.conf has a "include" line pointing to your configuration file properly and if the path is enclosed by quotes like this

```
include "/usr/share/lirc/remotes/pinnacle_systems/lircd.conf.pctv"
```

Please notice that the path above should not b the same, since my remote is different.

---

### Post by dmclennan on 2009-05-29
I made the changes you suggested with no change.  irw does not display remote codes.  I'm wondering if the /dev/lirc0 and /dev/ttyS0 are conflicting with each other and if there is something I need to do to reconfigure.  I appreciate your input and will keep trying!

---

