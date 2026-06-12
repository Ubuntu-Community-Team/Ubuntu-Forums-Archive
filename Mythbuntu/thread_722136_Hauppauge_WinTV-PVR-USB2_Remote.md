---
title: "Hauppauge WinTV-PVR-USB2 Remote"
date: 2008-03-12
forum: Mythbuntu
---

### Post by lhommemagique on 2008-03-12
I would like to add to the documentation another remote that requires extra work once mythbuntu is installed, namely the the remote that comes with the Hauppauge WinTV-PVR-USB2 external tv card. 

There are four versions of this device. The first two versions do have a remote but do not have an IR-Blaster, the third is the so called Media Center Kit and also does not have an IR-Blaster, also it does not have a Hauppauge IR remote an instead is shipped with a  Windows Media Center remote control and a separate IR pod. The fourth version has both an IR-Blaster and a  Hauppauge IR remote. 

The remotes to the first two versions should work out of box by selecting the Hauppauge Tv Card option, similarly the third version should work if Windows Media Center Remotes (new version Philips et al.) is selected. It is the fourth version that requires extra work once mythbuntu is installed.

When using the fourth version one will need to select the Hauppauge Tv Card option but two IR devices will present themselves to LIRC and it will defult to the first one /dev/lirc0 (or /dev/lirc/0) but this one is either bogus or perhaps for the IR-Blaster the real one is  /dev/lirc1 (or /dev/lirc/1). So you will need to tell LIRC to use that one instead. You can do this by disabling the first one, or by passing "-d /dev/lirc1" when you start LIRC.

The easiest way I have found to do this is to edit /etc/lirc/hardware.conf
```
$ sudo nano /etc/lirc/hardware.conf 
```
and add the line
**LIRCD_ARGS="--device=/dev/lirc1"**
save and exit  then restart LIRC and run irw to test
```
$ sudo /etc/init.d/lirc restart
$ irw
```
 you should see output that is the same as Hauppauge PVR-350 remotes.
From here everything should work fine.

---

### Post by ghuber on 2008-03-13
I have been using the WinTV-PVR-USB2 with remote and blaster for about 6 months now.  I ran into the same problem as you with two lirc devices.  lirc0 and lirc1

I fixed it by changing the REMOTE_DEVICE line in /etc/lirc/hardware.conf

REMOTE_DEVICE="/dev/lirc1"


Different change but it gets the same thing done for you.

---

