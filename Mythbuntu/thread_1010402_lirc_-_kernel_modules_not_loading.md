---
title: "lirc - kernel modules not loading"
date: 2008-12-13
forum: Mythbuntu
---

### Post by Andycas on 2008-12-13
Ive done 3 fresh installs now but i cant make lirc work anymore.
"/etc/init.d/lirc restart verbose" gave me: 
```
* Unable to load LIRC kernel modules. Verify your
* selected kernel modules in /etc/lirc/hardware.conf
```
So i try forcing it with "lircd -n -d /dev/input/event6" and when i launch "irw", i get this:
```
lircd-0.8.3pre1[633]: lircd(userspace) ready
lircd-0.8.3pre1[633]: accepted new client on /dev/lircd
lircd-0.8.3pre1[633]: could not get hardware features
lircd-0.8.3pre1[633]: this device driver does not support the new LIRC interface
lircd-0.8.3pre1[633]: major number of /dev/input/event6 is 13
lircd-0.8.3pre1[633]: LIRC major number is 61
lircd-0.8.3pre1[633]: check if /dev/input/event6 is a LIRC device
lircd-0.8.3pre1[633]: caught signal
```
while "dmesg | grep -i lirc" gave me this:
```
[  277.113909] lirc_dev: IR Remote Control driver registered, major 61 
[  277.119417] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.
[ 2760.251223] lirc_dev: IR Remote Control driver registered, major 61
```

running "dpkg-reconfigure lirc-modules-source" doesnt give me any options, it just outputs this:
```
Removing all DKMS Modules
Done.
Adding Module to DKMS build system
Doing initial module build
Installing initial module
Done.
```
I have also tried following [this guide](https://help.ubuntu.com/community/InstallLirc/Hardy#Adding%20support%20for%20more%20remotes) to reinstall modules, but it still complains. Evtesting the remote was fine too, using volume buttons changes my system volume, so the ir receiver itself and the remote should be fine.

Im about to go insane with this - ive spent over 40 hours trying to figure this out but i just cant...
My TV tuner is **[COLOR="DarkRed"][SIZE="3"]Hauppauge HVR-1110.[/SIZE][/COLOR]**
Im running 8.04 ubuntu (8.10 was having same issue).

Edit: I managed to find out what was wrong. Turns out that i didnt even need the kernel modules so i had to change my hardware.conf a bit:
[COLOR="Red"][B]REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/ir" (default path should be something like /dev/input/event6)
LOAD_MODULES="false"[/B][/COLOR]

---

### Post by yogaman69 on 2009-08-09
you saved my life...

thanks

---

### Post by Point &amp; Click on 2010-06-23
Andycas - you're a star :KS

I had the same issue with Ubuntu 9.10, MythTV 0.23

All sorts of problems, I had to make a /var/run/lirc folder too...

Thanks for posting the solution!

---

### Post by Nausser on 2011-03-06
This guide got my lirc starting OK however, I do not have a "/dev/ir" device. I do have a "/dev/lircd" but adding that to "/etc/lirc/hardware.conf" did not help. I can now run irw but I still have zero output.

System:
Mythbuntu 10.10 running ver.24
HDPVR
MCEUSB (used for IR commands in the past)

Please let me know if you have any ideas.

---

### Post by Retepris on 2011-10-16
Andycas, thank you. I've spent countless hours on this and the hardware.conf changes you suggested worked! For others out there; you may also want to ensure that the batteries work in your remote; I inherited an old HP only to find through jimmy'n a battery from a garage door opener that the battery it came with was dead. I'm sure that slowed my progress getting this thing working!

---

