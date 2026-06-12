---
title: "Hauppauge HVR 1100 remote control"
date: 2007-07-09
forum: Multimedia &amp; Video
---

### Post by Andcor on 2007-07-09
Hi everyone
Does anyone know how to make lircd recognise my hvr 1100 remote control?
I have read that I should use the lirc_i2c driver, but it fails to make a device special file in /dev/lirc*.
I also have installed a lirc_imon remote control which works fine and is been recogniced automaticly.

Any help appreciated

Andreas

---

### Post by Venom81 on 2007-07-20
Hi there,

the hvr 1100 doesn't need any special modules. all you have to do is a little config.

the remote is used on "/dev/input/eventX" where X is the number that points to the remote. make sure the cx88_dvb module is loaded else the device isn't created. to do so enter "lsmod | grep cx88_dvb" in console. if nothing is shown there enter "sudo modprobe cx88_dvb". to automatically load the module on startup edit "/etc/modules" and add "cx88_dvb" in a new line.

you can find out what devicenumber to use by entering "cat /proc/bus/input/devices" in console.
there u should find something like

> 
I: Bus=0001 Vendor=0070 Product=9402 Version=0001
N: Name="cx88 IR (Hauppauge WinTV-HVR110"
P: Phys=pci-0000:01:07.0/ir0
S: Sysfs=/class/input/input3
H: Handlers=kbd event3
B: EV=100003
B: KEY=100fc312 214a80200000000 0 18000 41a800004801 9e168000000000 10000ffc


on my machine for example the remote is located in /dev/input/event3 as seen in the line starting with H:

now edit "/etc/lirc/hardware.conf" and do the following changes:

> 
DRIVER="dev/input"
DEVICE="/dev/input/event3"


note that the device has to be the one appropriate for your system.

next step is to edit "/etc/lirc/lircd.conf" and create a remote profile for the hauppauge remote. i found one here: [Gentoo Wiki]("http://gentoo-wiki.com/HARDWARE_HVR_1100#Lirc_configuration").

after the remote profile is created u can start the lirc daemon and use kdelirc or other software to use the remote.

hope i could help you since i'm a beginner.

---

