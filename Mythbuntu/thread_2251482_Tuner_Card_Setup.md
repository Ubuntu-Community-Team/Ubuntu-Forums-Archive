---
title: "Tuner Card Setup"
date: 2014-11-04
forum: Mythbuntu
---

### Post by jjauernig on 2014-11-04
When I type lspci my card shows up in the list.  When I go to the backend setup my card doesn't show up (can't pull down a menu at all, no mouse function)  Assuming I have to type something about my pcie tuner card to get the backend to recognize it.  Where do I find this info?!  Please help.

---

### Post by dannyboy79 on 2014-11-04
just having the card show up in lspci doesn't mean a driver was loaded for it. what does lspci report as the chipset for the card?

---

### Post by Mike_Brown on 2014-11-04
I have a similar problem. I have 2 Hauppauge HVR-1600 PCI TV cards. MythTV on sees 1 -- which means I can only record 1 show at a time. The driver is there because 1 card works.

I am well versed in Windows system administration (since Windows 3 and command line all the way back to DOS) and am learning how to operate in Ubuntu. Is there an app or command line way to see connected system components like 'System' in Windows Control Panel?

Thanks for any help.

---

### Post by dannyboy79 on 2014-11-04
not really that i'm aware of but you can view dmesg for important messages that are noted when the system is booting up. the command is simply
```
dmesg
```

if you want to know information about the pci bus you would use lspci but with verbose, that would be
```
lspci -vvv
```

if you want  to know about the usb sub system that command is simply
```
lsusb
```

there's the following log files that contain important info about the system and kernel
/var/log/sys.log
/var/log/kern.log

then there's lshw, which is used to list hardware info. to get all the info for every system it would
```
sudo lshw
```

most all linux commands have man pages, manuals so if you ever don't know what options to use with a command just issue
```
man lshw
```
and you can read the manual for lshw. Good luck.

(PS i know all of this stuff merely from using ubuntu since 2005)

---

### Post by jjauernig on 2014-11-04
[COLOR=#212121][FONT=Helvetica Neue]02:00.0 Multimedia video controller: Conexant Systems, Inc. CX23887/8 PCIe Broadcast Audio and Video Decoder with 3D Comb (rev 04)[/FONT][/COLOR]

---

### Post by jjauernig on 2014-11-04
Here is the card:  [http://www.hauppauge.com/site/products/data_hvr1250.html](http://www.hauppauge.com/site/products/data_hvr1250.html)

---

### Post by dannyboy79 on 2014-11-04
> **jjauernig said:**
> [COLOR=#212121][FONT=Helvetica Neue]02:00.0 Multimedia video controller: Conexant Systems, Inc. CX23887/8 PCIe Broadcast Audio and Video Decoder with 3D Comb (rev 04)[/FONT][/COLOR]
you should see messages reporting cx23887 in your dmesg.  if you don't then the driver isn't being loaded by the kernel

---

### Post by jjauernig on 2014-11-05
I found it in dmesg:[COLOR=#000000][FONT=sans-serif][   11.301266] cx23885_dev_checkrevision() Hardware revision = 0xd0
[   11.301273] cx23885[0]/0: found at 0000:03:00.0, rev: 4, irq: 17, latency: 0, mmio: 0xfe600000
[FONT=sans-serif][SIZE=3][COLOR=#000000]
I was trying this last night: [/COLOR][/SIZE][/FONT][COLOR=#222222][FONT=Verdana]http://ubuntuforums.org/printthread.php?t=1648472&pp=75.  I couldn't get it to work.  It is like certain commands are locked out in the Mythbuntu flavor.[/FONT][/COLOR]


[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]
Thanks again for your help.[/FONT][/COLOR]

---

### Post by dannyboy79 on 2014-11-05
i would say that thread is your best bet. [http://ubuntuforums.org/printthread.php?t=1648472&pp=75](http://ubuntuforums.org/printthread.php?t=1648472&pp=75)  it shows how to install the v4l-dvb driver IF your current installation isn't seeing the card properly.  until your system sees the card properly and loads the driver for it it's useless as mythtv won't be able to use it

---

### Post by jjauernig on 2014-11-05
Thank you dannyboy79 for your help.

---

