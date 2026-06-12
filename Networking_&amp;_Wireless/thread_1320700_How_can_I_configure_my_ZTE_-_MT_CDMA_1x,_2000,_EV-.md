---
title: "How can I configure my ZTE - MT CDMA 1x, 2000, EV-DO modem"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by Tsega on 2009-11-09
I have a new ZTE - MT CDMA 1x, 2000, EV-DO modem. It works properly on Windows cause it has the drivers and the dialer installed automatically, but how do I use that with Ubuntu. I have wvdial installed, but I'm afraid the modem is not detected what should I do? Thanks for reading this...

---

### Post by Tsega on 2009-11-12
Help Please!

---

### Post by pdc on 2009-11-12
plug it into your Ubuntu;

type 

> lsusb in a terminal and then 

> sudo tail -f /var/log/messages 

and copy and paste the results back here

---

### Post by Tsega on 2009-11-12
Here is what I've got:

```
Nov 13 01:26:25 tsega kernel: [   64.048028] usb 2-2: new full speed USB device using uhci_hcd and address 2
Nov 13 01:26:25 tsega kernel: [   64.281461] usb 2-2: configuration #1 chosen from 1 choice
Nov 13 01:26:25 tsega kernel: [   64.368693] Initializing USB Mass Storage driver...
Nov 13 01:26:25 tsega kernel: [   64.395185] scsi2 : SCSI emulation for USB Mass Storage devices
Nov 13 01:26:25 tsega kernel: [   64.406315] usbcore: registered new interface driver usb-storage
Nov 13 01:26:25 tsega kernel: [   64.406319] USB Mass Storage support registered.
Nov 13 01:26:30 tsega kernel: [   69.408285] scsi 2:0:0:0: Direct-Access     ZTE      USB Storage FFF1 2.31 PQ: 0 ANSI: 2
Nov 13 01:26:30 tsega kernel: [   69.442363] sd 2:0:0:0: [sdb] Attached SCSI removable disk
Nov 13 01:26:30 tsega kernel: [   69.442440] sd 2:0:0:0: Attached scsi generic sg2 type 0

```

---

### Post by Tsega on 2009-11-13
From what I can see, the modem has been detected as a usb storage device, which it is as well, so I think what I need to do is change the initial state of the device to be the modem state. After seeing the results what should I be doing next?

---

### Post by pdc on 2009-11-13
You gave me the 

> sudo -f /var/log/messages

but not 

> lsusb        the lsusb command helps identify your modem

Yes; it is being seen as a zeroCD device:

**three ways to change it to a modem:** (happy to be corrected by others)

1) issue the command "sudo eject /dev/sr0" and that seems to flip it from zeroCD to modem

2) install usb_modeswitch

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

3) or install another piece of software ozerocdoff
[http://www.pharscape.org/ozerocdoff.html](http://www.pharscape.org/ozerocdoff.html)


in post #2 here

[http://ubuntuforums.org/showthread.php?t=1305931](http://ubuntuforums.org/showthread.php?t=1305931)

djtoon-nz describes how to do step 1) detailed above

let us know what you choose and how you get along

I guess if you tell us which version of Ubuntu you are using:

9.10 (recently released) has had problems with 3g Modems; running karmic updates drags in new fixes for some of these;

if you are running 9.04 it had a good track record with 3G modems

---

### Post by Tsega on 2009-11-14
pcd sorry about the missing info: here it is

the command

> 
lsusb


resulted in:

```

Bus 001 Device 001: ID 1d6b: 0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b: 0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 19d2: fff1 
Bus 002 Device 001: ID 1d6b: 0001 Linux Foundation 1.1 root hub

```

I use Ubuntu 9.04 Jaunty Jacklope
My modem model is ZTE AC2736

What else? Oh yeah, I intend to use the first choice it looks much easier, and the post by djtoon-nz  looks like its a winner, I'll just go ahead and try it. I will write back my results...

---

### Post by Tsega on 2009-11-14
**CORRECTION** 

The last entry for the second command 

> 
sudo tail -f /var/log/messages


Gave out the results I posted previously, because I read this pst
[http://ubuntuforums.org/showthread.php?t=1302235](http://ubuntuforums.org/showthread.php?t=1302235), and did what it instructed. Meaning I was able to change the state of the modem using Windows. So when I was trying to do what you asked previously and what was instructed by djtoon-nz, I faced some problems. I changed the state back using Windows again, and tried the command that you gave me and so here are the results.

**no change with the command**
> 
lsusb


it yeilded
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 19d2:fff5  
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```


**However the command** 
> 
sudo tail -f /var/log/messages



yeilded this
```

Nov 14 14:36:50 tsega kernel: [ 1293.128352] sr: Sense Key : No Sense [current] 
Nov 14 14:36:50 tsega kernel: [ 1293.128355] sr: Add. Sense: No additional sense information
Nov 14 14:36:50 tsega kernel: [ 1293.809385] sr: Sense Key : No Sense [current] 
Nov 14 14:36:50 tsega kernel: [ 1293.809389] sr: Add. Sense: No additional sense information
Nov 14 14:36:50 tsega kernel: [ 1293.816372] sr: Sense Key : No Sense [current] 
Nov 14 14:36:50 tsega kernel: [ 1293.816376] sr: Add. Sense: No additional sense information
Nov 14 14:36:50 tsega kernel: [ 1293.824351] sr: Sense Key : No Sense [current] 
Nov 14 14:36:50 tsega kernel: [ 1293.824355] sr: Add. Sense: No additional sense information
Nov 14 14:36:50 tsega kernel: [ 1293.850381] sr: Sense Key : No Sense [current] 
Nov 14 14:36:50 tsega kernel: [ 1293.850385] sr: Add. Sense: No additional sense information

```

Now the modem appears as a **usb storage device when I plug it in but before it didn't. **

BTW when I issue the command 

> sudo eject /dev/sr0

My cd drive **ejects the CD tray**. Following the instructions by djtoon-nz and when I issue the command

> sudo modprobe -r usbserial

I get the **[COLOR="Red"]error[/COLOR]**

[QUOTE]MODULE usbserial does not exists[QUOTE]

or something like that. So what to do now? Sorry for the long post.

---

### Post by pdc on 2009-11-14
this post describes how the poster succeeded in getting the modem running on Ubuntu 9.04; that you have;

[http://techsk.blogspot.com/2009/09/installing-usb-modem-zte-ac2726-in.html](http://techsk.blogspot.com/2009/09/installing-usb-modem-zte-ac2726-in.html)

so the fff1 was where you wanted to be: that should be the modem state;

see how you go following his commands:



the usb_modeswitch version on the Ubuntu site 1.0.2 and is in the deb version, so easy to install

if you go to the debian site

[http://packages.debian.org/search?keywords=usb-modeswitch](http://packages.debian.org/search?keywords=usb-modeswitch)

as the guys who make the modeswitch programme suggest you can if you want; 

[http://www.draisberghof.de/usb_modeswitch/index.html#download](http://www.draisberghof.de/usb_modeswitch/index.html#download)

you can get the latest version 1.0.5 in the sid (unstable) link; the unstable just means latest packages; the modeswitch will be fine

let us know how you get along

---

### Post by Tsega on 2009-11-16
Yeppy!!! I got it! 

Well after almost 5 years, I got my Ubuntu to connect to the Internet!  pcd thanks a lot for all your help, here is what I did

1. I installed the usb_modeswitch (the deb package), it changes the state of the device automatically, sweet.

2. Somehow, I seem to have a problem with usbserial, which is also necessary for some of the commands, so I fixed that after reading this post [http://ubuntuforums.org/showthread.php?t=1147685](http://ubuntuforums.org/showthread.php?t=1147685).

3. The fix required that I restarted my system, and start the OS with a custom grub entry.

4. After that I needed wvdial, the Network manager didn't recongize my modem. I installed wvdial using Synaptic using a wireless connection at a local cafe.

5. then I changed the config file of wvdial

> 
sudo gedit /etc/wvdial.conf


and changed it to the following

> 
[Dialer Defaults]
Modem = /dev/ttyUSB0
Phone = #777
Username = etc
Password = etc
Baud = 460800
Stupid Mode = 1
New PPPD = 1
Tonline = 0


6. Saved the file and ran the command sudo wvdial, rigth then and there it just worked!!!

I hope get to build on this and find a good way of doing this more cleanly. Possibly with the Network Manager, or someother GUI tool. 

Well pcd, I would like to say thanks for all your help! **[COLOR="Green"]Thumbs up to you!!![/COLOR]**

---

### Post by pdc on 2009-11-16
well done; you have got a high degree of knowledge about linux and Ubuntu, and you have done very well, and been very patient! 

I will read more on the various pointers you offer; let us know as you refine or change things

---

