---
title: "Struggling with wireless connection..."
date: 2010-03-01
forum: Networking &amp; Wireless
---

### Post by Captain_MDS on 2010-03-01
I'm computer illiterate so bear with me...I installed 9.10 (dual boot) on my Dell laptop Inspirion 1200 and was unable to connect to internet. I setup the wireless connection etc to no avail. I uninstalled Ubuntu and re-installed on a flash drive and still have the same problem. Is there a guide that will give me step by step instructions in setting up a wireless connection? After reviewing all the posts in all the various categories I've come to the conclusion that for dummies like me, windows might be the best choice to stick with. 
Thanks....

---

### Post by Mr.Ayres on 2010-03-01
I am having a similar problem. I am trying to use Mozilla Firefox browser. It will work if i am wired to the net but not if I am wireless.  

Any fixes?

Henri

---

### Post by Swagman on 2010-03-01
The very fact you managed to dual boot means your NOT computer illiterate.

Just keep googling & posting on here.

In relation to your problem.. I assume you tried left clicking on the network icon at the top of your screen to select what network ?

---

### Post by Captain_MDS on 2010-03-01
Thanks for the reply...yes I did, no network listed. I'm at work now and don't have access to my laptop so I won't be able to supply much info. If possible, give me some things to check or do this evening. Wireless works ok in XP (home edition).  I have a Dell wireless router (1397) and also wireless connection through my 2WIRE (AT&T) modem and both work fine in windows. I haven't setup a hardwired connection to the laptop, never a need as all I use the laptop for is internet.
Thanks.....

---

### Post by Captain_MDS on 2010-03-01
Found the following on a Google search...does it sound like a logical step to you to try?

9.10 Broadcom Wireless to Work
Perhaps this will help someone out there.

I was using Jaunty fine on my laptop (Dell e1705) with wireless working. I installed 9.10 beta and could not get it to work. In jaunty I was using the Broadcom Wireless driver that showed up in System > Administration > Hardware drivers.

When I installed 9.10 as a fresh install from the live cd, it would list only the Broadcom Wireless driver. I kept choosing "Activate" and entering my password, but it would never activate. Having no network connectivity, I was unable get any updates.

However this worked for me:

1) Open Synaptic Pacakage Manager
2) Ensure 9.10 LiveCd is in CD drive
3) Settings > Repositories > Ubuntu Software
4) Check the installable from cd and close
5) Refresh
6) Search for "bcmwl-kernel-source"
7) Mark for installation
Install it
9) Reboot computer

---

### Post by bkratz on 2010-03-01
> **Captain_MDS said:**
> Found the following on a Google search...does it sound like a logical step to you to try?

9.10 Broadcom Wireless to Work
Perhaps this will help someone out there.

I was using Jaunty fine on my laptop (Dell e1705) with wireless working. I installed 9.10 beta and could not get it to work. In jaunty I was using the Broadcom Wireless driver that showed up in System > Administration > Hardware drivers.

When I installed 9.10 as a fresh install from the live cd, it would list only the Broadcom Wireless driver. I kept choosing "Activate" and entering my password, but it would never activate. Having no network connectivity, I was unable get any updates.

However this worked for me:

1) Open Synaptic Pacakage Manager
2) Ensure 9.10 LiveCd is in CD drive
3) Settings > Repositories > Ubuntu Software
4) Check the installable from cd and close
5) Refresh
6) Search for "bcmwl-kernel-source"
7) Mark for installation
Install it
9) Reboot computer




Yes it does if your wireless uses the STA driver.  You should do an 

lspci
(LSPCI)
in the terminal, Applications>>Accessories>>Terminal and it should come back and say a bunch one of which should say something like BCM4312. If this is true you have the right methodology. If not post back the results of the command for inspection.

You should at least be aware that you might see something like what is demonstrated in posts 3 and 5 of the following:

[http://ubuntuforums.org/showthread.php?t=1414946&highlight=dell-laptop](http://ubuntuforums.org/showthread.php?t=1414946&highlight=dell-laptop)

But we will worry about that if it happens!

---

### Post by Captain_MDS on 2010-03-01
Thanks, I'll check it out tonight (US central time) and post results...

---

### Post by Captain_MDS on 2010-03-01
> **Captain_MDS said:**
> Thanks, I'll check it out tonight (US central time) and post results...

This is the result of lscpi....what next?

	 	 To run a command as administrator (user "root"), use "sudo <command>".
 See "man sudo_root" for details.
 

 ubuntu@ubuntu:~$ lspci
 00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
 00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
 00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
 00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
 00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
 00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
 00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
 00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
 00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
 00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
 00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
 00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
 00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
 02:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
 02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)
 03:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
 ubuntu@ubuntu:~$

---

### Post by bkratz on 2010-03-01
> **Captain_MDS said:**
> This is the result of lscpi....what next?

	 	 To run a command as administrator (user "root"), use "sudo <command>".
 See "man sudo_root" for details.
 

 ubuntu@ubuntu:~$ lspci
 00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
 00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
 00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
 00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
 00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
 00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
 00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
 00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
 00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
 00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
 00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
 00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
 00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
 02:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
 02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)
 03:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
 ubuntu@ubuntu:~$

This one is your wireless card.

 03:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

The directions you posted earlier were not for that card. I will find a good thread and post a link shortly.

---

### Post by bkratz on 2010-03-01
Here is a good description of what is needed.

[http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices)

See the section labeled 

Ubuntu/Debian

about 3/4 of the way down.

---

### Post by ebosco on 2010-03-02
i'm having similar problems.ma wireless adapter is detected but cannot detect any wireless network around although there are several.didnt have this problem with ubuntu9.04.this started when i installed ubuntu9.10.pls HELP

---

### Post by bkratz on 2010-03-02
> **ebosco said:**
> i'm having similar problems.ma wireless adapter is detected but cannot detect any wireless network around although there are several.didnt have this problem with ubuntu9.04.this started when i installed ubuntu9.10.pls HELP

Please start a new thread with the outputs of

```
lsusb
lspci
iwconfig
sudo iwlist scan
sudo lshw -C network
rfkill list
```

using code tags like above( the # symbol).

---

### Post by Captain_MDS on 2010-03-04
Couldn't get back to you sooner..been out of town. I assume that I'll need to be connected to the Internet (hardwired) to do this procedure listed in the article. Can you recommend a router / wireless card that would work with Ubuntu "out of the box". 
Thanks,
Captain_MDS

---

