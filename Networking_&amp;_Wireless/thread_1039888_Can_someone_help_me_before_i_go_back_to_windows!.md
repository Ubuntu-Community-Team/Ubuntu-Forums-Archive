---
title: "Can someone help me before i go back to windows!"
date: 2009-01-15
forum: Networking &amp; Wireless
---

### Post by strujillo.jr on 2009-01-15
Ok im getting so stressed!!! OK so i have a Dell Latitude D520 but no matter how hard i try, i can not get the Wireless to connect to the INternet. THe wireless light by the power button doesnt even turn on...if i do

```
lspci
```

i get

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
02:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

```
does anybody have anything that i could use! The very word NDISWRAPPER brings up horrible memories! Please help!!! oh and i run 8.10

---

### Post by kranny on 2009-01-15
did you try this [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

---

### Post by strujillo.jr on 2009-01-15
yes, so many times, im gonna do it again though cause i just reinstalled Ubuntu to start fresh, but ill retry this one last time.

---

### Post by Chas_E_Erath on 2009-01-15
> 
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)



Hi.  I use to have a broadcom wireless g-card - I think it was the same as yours.

I found this package:  b43-fwcutter  was vital.

In a nut shell - Broadcom won't do linux drivers, so a nice fellow out there wrote a utility that digs into the card and extracts the firmware. 

So, step 1 is to install that package.  I seem to recall that I had to do a little more work after that to get it to go (there was a Readme file with the nitty-gritty), but Ubuntu may have smoothed some of that out a bit since then.  

Hope that helps.
Chas.

---

### Post by melojo on 2009-01-15
Have a look at this post.  
[http://ubuntuforums.org/showpost.php?p=6077792&postcount=72](http://ubuntuforums.org/showpost.php?p=6077792&postcount=72)

---

### Post by BoneSaw on 2009-01-15
just as a check, your radio kill switch hasnt been activated has it?

the radio kill switch cuts out your wifi connectability. it will manifest itself as either a physical slider switch on the side, or a button (most likely utilizing the function [fn] button) on my dell inspiron 1505 its fn+f2. this cause me a giant amount of frustration when i first got this laptop as hit it by accident trying to run a command with alt+f2.

---

### Post by strujillo.jr on 2009-01-15
idk, its not working for some reason...urg!!! i think im just gonna give up on Ubuntu i swear i wanted linux so bad but i can never get this part to work!!! I get stuck at the "Downloading Firmware" section in [http://ubuntuforums.org/showpost.php?p=6077792&postcount=72](http://ubuntuforums.org/showpost.php?p=6077792&postcount=72)

and i keep getting stuck at unzipping the R151517.EXE file in [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

---

### Post by utnubuuser on 2009-01-15
Personal experience: Ubuntu just works.  An alternative that seems to have good hardware support: Sidux

---

### Post by melojo on 2009-01-16
> **strujillo.jr said:**
> idk, its not working for some reason...urg!!! i think im just gonna give up on Ubuntu i swear i wanted linux so bad but i can never get this part to work!!! I get stuck at the "Downloading Firmware" section in [http://ubuntuforums.org/showpost.php?p=6077792&postcount=72](http://ubuntuforums.org/showpost.php?p=6077792&postcount=72)

and i keep getting stuck at unzipping the R151517.EXE file in [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

You don't have to download as the post suggest that if you don't have an internet connection you can get the firmware off of the cd.

---

