---
title: "atheros wifi help"
date: 2006-01-27
forum: Networking &amp; Wireless
---

### Post by nwcowboysfan on 2006-01-27
hi all,

i am in pretty desperate need of help. i recently followed the steps on the forum to install the ati graphics drivers on my laptop (including the section about copying the madwifi drivers over). in this process you have to remove the linux-restricted-modules, which i am assuming is where the drivers for my atheros wireless card use to live.

now my card will not come up at all, so i tried installing the madwifi-ng and the madwifi-old files via the thread on these forums. no luck. when doing:

sudo modprobe ath_pci
WARNING: Error inserting (/lib/modules/2.6.12.10-386/net/.ath_hal.ko): Invalid module format
WARNING: Could not open '/lib/modules/2.6.12.10-386/madwifi/wlan.ko': No such file or directory
.
.
.

any help would be greatly appreciated!!!!

---

### Post by nwcowboysfan on 2006-01-30
well, since i didn't see a reply i decided to go a different route. i tried using ndiswrapper with the windows net5211.inf drivers. dmesg gives me this output:

root@ubuntu:~# dmesg | grep ndis
[4294704.443000] ndiswrapper version 1.1 loaded (preempt=no,smp=no)
[4294704.535000] ndiswrapper: driver net5211 (,05/31/2003,2.4.0.71) loaded
[4294704.536000] ndiswrapper (NdisWriteErrorLogEntry:273): log: C000138B, count: 4 (db0b1220), return address: dcb6a277, entry: dcb6a660 offset: 4294966295
[4294704.536000] ndiswrapper (ndiswrapper_add_one_pci_dev:188): Windows driver couldn't initialize the device (C0010006)
[4294704.536000] ndiswrapper: probe of 0000:09:04.0 failed with error -22

root@ubuntu:~# ndiswrapper -l
Installed ndis drivers:
net5211 driver present, hardware present
root@ubuntu:~#

root@ubuntu:~# ifup wlan0
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
sit0: unknown hardware address type 776
Bind socket to interface: No such device
Failed to bring up wlan0.

if anyone could please help it would be greatly appreciated!

thanks to everyone who supports this community!

---

### Post by nwcowboysfan on 2006-02-01
should i post this somewhere else? or am i not getting a reply because my problem is too far gone to be helped?

thanks

---

### Post by firecat53 on 2006-02-01
Hey... search on my previous posts for some help on getting Madwifi and/or wpa compiled and working. I'd stay away from the madwifi-ng for now...look for the madwifi-old code on madwifi.org.  If you can't find it, or you have more trouble, let me know.

Good luck!  Scott

---

### Post by henshu70 on 2006-02-02
Hi there. My computer is Toshiba Satellite P20. When I installed Ubuntu 5.10 at first the wireless device was detected correctly. Than I reinstalled the NVIDIA driver and it was just gone. So I guess exactly the same problem here. After some search I found this very useful HOW TO on installing the madwifi drivers. Thought it may be helpful here:

[HOWTO: Latest madwifi svn snapshot]("http://ubuntuforums.org/showthread.php?t=105437&highlight=madwifi+ng")

Nevertheless I still haven't managed to get my wifi working (although it is detected). If anyone could be of any help I would very much appreciate.

---

### Post by Lambert on 2006-02-02
When you say it's not working, where is the breakdown? Logical steps are.

1. device is plugged in and recognized by os
2. driver is loaded and bound to driver
3. driver is functioninoning properly
4. association to ap
5. assignment of network info
6. configs in networking areas set properly

There's a link in my signature, both of them will lead you to a wirelesstroubleshootingguide on the wiki. Go there and walk through the steps. If it doesn't get you working, post back where you're stuck along with commands in that area.

With the -ng version, make sure you have the wifi0 base and a ath0 interface built on top of that with the wlanconfig create... command. (iwconfig command will show)

Since that howto was written there have been some updates to the driver and I haven't tested it with breezy, depending on what's found I might suggest (and need to change the howto ) to a snapshot instead of current.

---

### Post by nwcowboysfan on 2006-02-03
lambert....the walkthrough for madwifi worked great for me!! thanks so much!!
the only frustrating aspect left is my battery not being detected..any ideas on that??

henshu70....the only thing i needed to change, other than the changes suggested in the walkthrough, was in the /usr/src/madwifi-ng/hal/public/i386-elf.inc file. i changed the line

CC=     ${TOOLPREFIX}gcc
  to
CC=     ${TOOLPREFIX}gcc-3.4

you may want to give this a shot and see what happens.

thanks again to everyone!

---

### Post by Lambert on 2006-02-05
[quote=nwcowboysfan]
the only frustrating aspect left is my battery not being detected..any ideas on that??
[/quote]

All I can offer is this link or posting in the laptop section.

[https://wiki.ubuntu.com/ACPIBattery](https://wiki.ubuntu.com/ACPIBattery)

---

### Post by kk_davey on 2006-02-19
> sudo modprobe ath_pci
> WARNING: Error inserting (/lib/modules/2.6.12.10-386/net/.ath_hal.ko): Invalid
> module format
I've found in the past that invalide format is due to the gcc compiler being the wrong version. I changed the compiler version ito 3.4 (as someone else suggested) & the module format error was resolved. 

> WARNING: Could not open '/lib/modules/2.6.12.10-386/madwifi/wlan.ko': No such >
> file or directory
I also had this problem & found that for some reason in my /lib/modules/ directory there were 2 directories, 2.6.12.10-386 & 2.6.12. 
(Even though I hadn't recompiled my kernel, but I had followed the madwifi instruction to download headers when I already had the source, which I think created the extra directory.) 

If both of these directories are supporting the same kernel compilation then only 1 is required, and you can remove 1 or make a symbolic link so there is no confusion between them (my .ko files were being put in 2.6.12 by madwifi, but looked for in 2.6.12.10-386 by the modprobe command. Once I'd done this everything was fine. 

Hope that helps (first time I've ever posted an answer to someone's question so I don't know if I've been very clear.)

Good luck,
Katie

---

### Post by jimufa on 2006-02-19
milton@ubuntu:~/madwifi-ng$ sudo make
Makefile.inc:94: Default KERNELPATH not found, using /usr/src/linux
Makefile.inc:104: *** KERNELPATH: /usr/src/linux does not exist.  Alto.
what can i do?

---

### Post by dotman on 2006-02-23
[QUOTE=jimufa]milton@ubuntu:~/madwifi-ng$ sudo make
Makefile.inc:94: Default KERNELPATH not found, using /usr/src/linux
Makefile.inc:104: *** KERNELPATH: /usr/src/linux does not exist.  Alto.
what can i do?[/QUOTE]

do you have the kernel headers downloaded?

---

