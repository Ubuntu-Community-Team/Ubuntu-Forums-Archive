---
title: "Dell Mini9 Karmic: no wired or wireless network"
date: 2010-03-25
forum: Networking &amp; Wireless
---

### Post by timmeh1234 on 2010-03-25
Hi all,
 
I know that similar problems have been posted about a lot here, but i can't seem to find the right answer :)
 
I have fresh installed 9.1 on a Dell mini9
Does not recognise wired or wireless networks
Ethernet port light does light-up on cable insertion
 
I have tried reinstalling dkms 2.1.0.1 and bcmwl 5.10.91.9 packages (from usb-install) and restarting, to no avail.
 
ifconfig gives:
Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
 
System:Network Tools shows loopback and "Unknown Interface (pan0)" that has a hardware address but is inactive.
 
lshw -C network gives:
*-network UNCLAIMED
description: Network controller
product: BCM4312 802.11b/g
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:03:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: latency =0
resources: memory:f0200000-f0203fff
 
nm-tool gives:
  State: disconnected
 
Any help would be appreciated, I'm a bit stuck and a bit of a noob :)

---

### Post by RedSingularity on 2010-03-25
ifconfig only gives you the Local Loopback?

---

### Post by timmeh1234 on 2010-03-26
> **RedSingularity said:**
> ifconfig only gives you the Local Loopback?
 
 
Yup, that's correct.

---

### Post by RedSingularity on 2010-03-26
Thats very odd.  It is not even seeing your cards.  

Post the output of lspci

---

### Post by timmeh1234 on 2010-03-26
> **RedSingularity said:**
>  Post the output of lspci
 
[SIZE=2]Hi RedS, here's lspci, thanks :)[/SIZE]
[FONT=Arial][SIZE=2] [/SIZE][/FONT]
[FONT=Arial][SIZE=2]00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT]
[FONT=Arial][SIZE=2]00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT]
[FONT=Arial][SIZE=2]00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT]
[FONT=Arial][SIZE=2]00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT]
[FONT=Arial][SIZE=2]00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT]
[FONT=Arial][SIZE=2]00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT]
[FONT=Arial][SIZE=2]00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT]
[FONT=Arial][SIZE=2]00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT]
[FONT=Arial][SIZE=2]00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT]
[FONT=Arial][SIZE=2]00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT]
[FONT=Arial][SIZE=2]00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT]
[FONT=Arial][SIZE=2]00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT]
[FONT=Arial][SIZE=2]00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT]
[FONT=Arial][SIZE=2]00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT]
[FONT=Arial][SIZE=2]00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT]
[FONT=Arial][SIZE=2]02:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT]
[FONT=Arial][SIZE=2]02:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT]
[FONT=Arial][SIZE=2]02:00.3 System peripheral: JMicron Technology Corp. MS Host Controller[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT]
[FONT=Arial][SIZE=2]03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)[/SIZE][/FONT]

---

### Post by RedSingularity on 2010-03-26
Ok first check in 

System>Admin>Hardware Drivers

See if you can activate it there.

---

### Post by revaew on 2010-03-26
could i possibly get some help? i have the same initial problem and my ethernet port doesnt even light up when i insert a cable. except im a complete newbie at anything linux (trying to get it to work with ubuntu 9.1) so i have absolutely no idea what im doing. but i have done the lspci check thing, but i am not sure what is next. any help would be great =)

---

### Post by timmeh1234 on 2010-03-27
> **RedSingularity said:**
> Ok first check in 
 
System>Admin>Hardware Drivers
 
See if you can activate it there.
 
The Broadcom STA wireless driver is there and is inactive. When i try to activate it, a message box pops up saying "downloading and installing driver" briefly. The box dissapears and nothing seems to have happened - the driver is still inactive. 
 
I've downloaded a copy of the driver from the broadcom website... I just don't know what to do with it :)
 
Thanks

---

### Post by RedSingularity on 2010-03-27
You cant use that driver from the site.  Its probably a windows .exe file.  Can you temporarily hook up to a wired network?  If you can then when you go to activate it it will work properly.

---

### Post by timmeh1234 on 2010-03-27
> **RedSingularity said:**
> You cant use that driver from the site. Its probably a windows .exe file. Can you temporarily hook up to a wired network? If you can then when you go to activate it it will work properly.
 
Hi RedS,
 
I can't seem to get a wired network either :(
The port lights up but that's it - see OP
 
The file from the broadcom site is linux specific tar
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

---

### Post by RedSingularity on 2010-03-27
Do you have network manager installed?

---

### Post by RedSingularity on 2010-03-27
Oh and looking at your other post it seems that the Wired connection is not recognized by "lspci".  Are you sure the interface is working properly?  Did you have windows on it previously with successful connections?

---

### Post by timmeh1234 on 2010-03-28
> **RedSingularity said:**
> Do you have network manager installed?
 
I have system-admin-network tools
 
The network devices listed are
 - loopback
 - Unknown interface pan0. This has a hardware address but is inactive
 
How do i get network manager?
 
The wired port has worked before. I had 9.04 installed and the ssd corrupted. I put in a new ssd - no problems with putting it in and installing 9.1 until this point. I spose i could have accidently bashed something when the case was open...
 
... but its a bit weird that the only 2 things not working are the wired and wireless network.

---

### Post by RedSingularity on 2010-03-28
Well the system is recognizing the wireless adapter under "lspci" unfortunately you need a wired connection to get the drivers for the wireless connection.  Now you may have bashed something but i suggest before we jump to conclusions you try and reinstall Ubuntu.  It may be a defect from the fresh install image.  If you reinstall ubuntu and still have problems then it probably is a hardware problem.

---

### Post by timmeh1234 on 2010-03-29
Well I think that the wired access is shagged.
 
I reinstalled 9.1, and even tried (gasp) installing vista in between, and neither recognised a wired network (of interest, vista didnt have drivers for the broadcom wireless either)
 
Is there a way to install the drivers in ubuntu without direct network access from the ubuntu computer? I have the tar drivers from broadcom.
 
The other option is to crack into the laptop case and look for stray staples...

---

### Post by bkratz on 2010-03-29
> **timmeh1234 said:**
> Well I think that the wired access is shagged.
 
I reinstalled 9.1, and even tried (gasp) installing vista in between, and neither recognised a wired network (of interest, vista didnt have drivers for the broadcom wireless either)
 
Is there a way to install the drivers in ubuntu without direct network access from the ubuntu computer? I have the tar drivers from broadcom.
 
The other option is to crack into the laptop case and look for stray staples...

Is this where you got the software?

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

If so, the readme file gives complete directions for installation.

---

### Post by timmeh1234 on 2010-03-29
Option 3: buy a $10 usb to ethernet adaptor, access wired network that way and fix broadcom wireless drivers with synaptic :)
 
thanks all for help

---

### Post by RedSingularity on 2010-03-29
No problem, hope you get it working :)

---

