---
title: "md300 udev rules freezes jaunty on boot, OK in intrepid"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by angustia on 2009-04-26
hi

i have a sony md300 modem and to make it work in ubuntu 8.10 i had to create to files:

/etc/modpobe.d/md300:
```
#Sony Ericsson MD300
alias md300 usbserial
options md300 vendor=0x0fce product=0xd0cf
```

/etc/udev/rules.d/50-md300modem.rules:
```
ACTION!="add", GOTO="3G_End"
BUS=="usb", SYSFS{idProduct}=="d0cf", SYSFS{idVendor}=="0fce", PROGRAM="/bin/sh -c 'echo 3 > /sys/%p/device/bConfigurationValue'"
LABEL="3G_END"
```

those two files let me use wvdial to connect to internet without much problems (the network applet seemed to not work with the modem, but wvdial was fine).

---------

now, i upgraded to 9.04, and at the first boot the kernel stopped at this line:
```

....
[   13.328858] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.328907] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.328956] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.329003] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.329052] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.375329] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   13.375470] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.408958] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input8
[   13.750444] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input9
[   13.795174] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input10
```

by trial and error i found out the 50-md300modem.rules was hanging the boot process (well, it was not hanged, if i plug the modem, messages appears about the new modem, but it keeps stopped without X or consoles)

if i erase that file, the next boot completes, and, if after logging in my account, i restore de rules file to /etc/udev/rules.d and run /etc/init.d/udev restart, the system runs normally and when i plug the modem, this is detected and the network applet offers me to connect without problems.

the downside right now is that i have to remember to delete the md300modem.rules file before shutdown or i will have to start looking for a live cd...

thanks for any help

excuse my english

---

### Post by djackd3 on 2009-04-27
Hi,
I have the same problem. If I wait 10 minutes, Ubuntu 9.04 finally boots. The threads udevd --deamon uses all the ressources of my processors.
I tried to stop it "sudo /etc/init.d/udev stop and I can work, but not a good idea to work like that...
I am still looking for a solution...
Thanks,
Djackd3

---

### Post by angustia on 2009-04-28
also, just some minutes after restarting udev and pluging the modem, appears 3-7 udevd in top, taking about of 99% of CPU usage.

those can be stopped with a "/etc/init.d/udev restart"

---

### Post by jaimefortega on 2009-05-05
Try using this file:
[http://launchpadlibrarian.net/24470904/50-md300modem.rules](http://launchpadlibrarian.net/24470904/50-md300modem.rules)
1) Replace the old file with this new one in /etc/udev/rules.d/
2) Restart udev: sudo /etc/init.d/udev restart
3) Plug the modem
4) you are ready :)
This file fixes this bug! at least for me!
I'm using Jaunty now!

I found the fix in:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/277613](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/277613)

---

### Post by angustia on 2009-05-19
At the end, the error was so simple and dificult to see:

in 50-md300modem.rules i've got:

ACTION!="add", GOTO="3G_End"
...
LABEL="3G_END"    <-- all uppercase

that explains why every time i plugged some usb stick or usbmodem, the CPU went to 100% with many udevd running in the background

now everything works perfectly

---

