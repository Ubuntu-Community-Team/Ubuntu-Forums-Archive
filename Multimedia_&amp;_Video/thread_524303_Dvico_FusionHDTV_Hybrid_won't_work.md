---
title: "Dvico FusionHDTV Hybrid won't work"
date: 2007-08-13
forum: Multimedia &amp; Video
---

### Post by Sumatie on 2007-08-13
Can anyone please help. I am trying to get my dvb-t pci card working in feisty. I have tried multiple sites and threads, updated firmware, loaded modules etc. but nothing seems to work. I also a twinhan 7045 usb tuner that works fine.

I am a relative newbie but can do most installs, just not this one. Anyone please!!

---

### Post by Sumatie on 2007-08-16
OK I believe that the Dvico Hybrid is support on linux kernels 2.6.17 and later so (to start with a clean slate) I did fresh install and upgraded to kernel version 2.6.22-9.

My system seems to find the card but does not identify it as a Dvico Hybrid (though it did once) instead if I run
```
$ dmesg | grep dvb
[   57.795459] cx2388x dvb driver version 0.0.6 loaded
[   57.795463] cx8802_register_driver() ->registering driver type=dvb access=shared
[   57.795469] cx88[0]/2: cx2388x based dvb card

```

or if I try 
```
$ ls -l /dev/dvb/adapter*
total 0
crw-rw---- 1 root video 212, 4 2007-08-16 16:24 demux0
crw-rw---- 1 root video 212, 5 2007-08-16 16:24 dvr0
crw-rw---- 1 root video 212, 3 2007-08-16 16:24 frontend0
crw-rw---- 1 root video 212, 7 2007-08-16 16:24 net0

```
I get this, I assume this means the card is being detected and loaded though I still can't use it!!

Anyone got any ideas?

---

### Post by Sumatie on 2007-08-17
I've done yet more digging and according to the LANANA site I'm missing to adapters Video0 and Audio0. Is there any way to manually load them? Could this be the problem?

---

### Post by stowe39 on 2007-10-05
Hi Sumatie

I'm running LinuxMce, which is based on Feisty.  I got my Dvico FusionHDTV Hybrid card running by 

CODE:
sudo nano /etc/modules

Then add this to the bottom of the list

cx88_dvb

then save and exit.

After a shutdown and reboot (not just a restart), I added the users mythtv and linuxmec to the groups 
in /etc/group for cdrom, audio, video, plugdev

Then I ran mythtv setup as root,

CODE:
sudo -s
mythtv-setup

 and was able to sucessfully find and save all the channels.

I haven't gotten the remote working yet - that's today's goal!

Cheers

Kym

---

### Post by m3tal666 on 2007-10-15
> **stowe39 said:**
> Hi Sumatie

I'm running LinuxMce, which is based on Feisty.  I got my Dvico FusionHDTV Hybrid card running by 

CODE:
sudo nano /etc/modules

Then add this to the bottom of the list

cx88_dvb

then save and exit.

After a shutdown and reboot (not just a restart), I added the users mythtv and linuxmec to the groups 
in /etc/group for cdrom, audio, video, plugdev

Then I ran mythtv setup as root,

CODE:
sudo -s
mythtv-setup

 and was able to sucessfully find and save all the channels.

I haven't gotten the remote working yet - that's today's goal!

Cheers

Kym

Cheers Kym, worked asap, as soon as i rebooted Kaffeine even downloaded and installed its DVB Gear and picked up my car as it did in Fedora...

Must say after many of drunken fight with my brother... i am starting to wein from Fedora Kubuntu

Cheers for the good advice

---

### Post by Sumatie on 2008-01-04
Hi me again now can't get Dvico Hybrid working in Gutsy...have tried the above and no avail.

Here is what is coming up. MythTV can find the card but not identify what it is just says generic. When I try to scan for chanels it tries and comes up with nothing no matter what I set the region to.

```
 ls -l /dev/dvb/adapter*
ls: /dev/dvb/adapter*: No such file or directory

```

```
 dmesg | grep dvb
[   64.782453] cx2388x dvb driver version 0.0.6 loaded
[   64.782457] cx8802_register_driver() ->registering driver type=dvb access=shared
```

Help please...

---

