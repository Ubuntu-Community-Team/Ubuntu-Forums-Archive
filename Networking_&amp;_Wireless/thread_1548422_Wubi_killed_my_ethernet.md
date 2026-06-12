---
title: "Wubi killed my ethernet"
date: 2010-08-08
forum: Networking &amp; Wireless
---

### Post by Saya on 2010-08-08
I wanted to test 10.04 and downloaded Wubi to do so. Normal setup, it automatically picked the 64-bit version.
After booting into Wubi, installing my ATI drivers and restarting it did no longer connect to my ethernet.
A few reboots didn't help so I went back to Windows for troubleshooting.

However now Windows doesn't connect to the ethernet either. It's plain dead, Windows doesn't find any connections and the modem doesn't light the Ethernet cable LED. The modem itself works fine with wireless devices.

I have now tried everything including uninstalling Ubuntu, system restore, driver rollback, driver update, BIOS default settings, a different cable, a different modem etc. 

This is a 64-bit specific issue because I tested the 32-bit version of Wubi 10.04 a few months ago without problems.

Windows 7 x64
Wubi 10.04 x64
Gigabyte P55-UD3 with onboard Realtek RTL8111D LAN.

I'd like to get out of this without Ubuntu effectively having broken my hardware and my trust in it.

---

### Post by NFblaze on 2010-08-08
Try looking at you network devices and making sure it's not set to disabled.

This sounds like it might be a Windows issue, and those are infinitely ten times much harder to troubleshoot over the internet.

---

### Post by Saya on 2010-08-08
I have disabled/enabled/reset/ipconfig'd the adapter about 20 times. All I get is the good old "No operation can be performed on Local Area Connection while it has its media disconnected."

---

### Post by adde.k on 2010-08-08
> **Saya said:**
> I wanted to test 10.04 and downloaded Wubi to do so. Normal setup, it automatically picked the 64-bit version.
After booting into Wubi, installing my ATI drivers and restarting it did no longer connect to my ethernet.
A few reboots didn't help so I went back to Windows for troubleshooting.

However now Windows doesn't connect to the ethernet either. It's plain dead, Windows doesn't find any connections and the modem doesn't light the Ethernet cable LED. The modem itself works fine with wireless devices.

I have now tried everything including uninstalling Ubuntu, system restore, driver rollback, driver update, BIOS default settings, a different cable, a different modem etc. 

This is a 64-bit specific issue because I tested the 32-bit version of Wubi 10.04 a few months ago without problems.

Windows 7 x64
Wubi 10.04 x64
Gigabyte P55-UD3 with onboard Realtek RTL8111D LAN.

I'd like to get out of this without Ubuntu effectively having broken my hardware and my trust in it.
I've got kinda the same problem, drives me nut...

Discovered today that if I pull the power-cord out of the computer for a while when switching between Windows and Ubuntu it works, but a normal reboot does not... really silly...

I discovered this by accident, it was thunder and lightning outside this night and I pulled out computers etc, and sure was I surprised when everything worked when I booted my computer up... I where going to send my motherboard back to the shop, glad I didn't do that :D

Could it matters that I use 64bit windows and 32bit Ubuntu?

---

### Post by NFblaze on 2010-08-08
Media is disconnected?

Do you have a hardware switch or a software switch? You might have to enable that. Usually the hardware swtiches are somewhere on the computer and the software switch tends to be a Fn + F-key.

---

### Post by Saya on 2010-08-08
There are no hardware switches. The PC does not connect to the modem and the modem does not see the PC on the other end of the cable, though the modem and the network adapter evidently work. It isn't a cable problem either because I've tried several.

Something in Ubuntu somehow messed with the adapter.

---

### Post by NFblaze on 2010-08-08
What's your IP setting? Are they configured for Manual or Automatic DHCP?

---

### Post by Iowan on 2010-08-08
**ifconfig -a** shows the adapter? 
**sudo lshw -C network** recognize interface?

---

### Post by Saya on 2010-08-08
> **adde.k said:**
> Discovered today that if I pull the power-cord out of the computer for a while when switching between Windows and Ubuntu it works, but a normal reboot does not... really silly...
Awesomely enough, this worked. I pulled out everything, took a shower and now everything works again.
Kudos to you! (Swede? Tack!)

---

### Post by adde.k on 2010-08-08
> **Saya said:**
> Awesomely enough, this worked. I pulled out everything, took a shower and now everything works again.
Kudos to you! (Swede? Tack!)

Inga problem :D

---

### Post by lminier on 2010-10-20
Short version: it seems at least the 2.6.35 linux drivers put the realtek RTL8111D in a sad state, but if you keep the machine power off *and unplugged* for a little while, it should work again.

Long version: I'm also using a GA-P55A-UD3, but found users of Intel boards with the same ethernet chip (RTL8111D) are affected as well.  Today, I thought the ethernet adapter was fried because both Windows 7 and Ubuntu 10.10 reported no link on this interface, and no LED was turning on.  I tried turning the machine off, flashing the BIOS to the latest version, updating the driver from gigabyte (instead of using the builtin win7 one), updating to the latest version directly from Realtek, I also tried the Realtek diagnosis tools (both from Gigabyte and Realtek) and they reported that everything was fine, except no cable was plugged in.  I tried replacing the cable, connecting to another port, and even another switch.
  I finally came across this forum post and tried unplugging the power supply and devices for some minutes, and things were working again.

This looks like a bug in the linux or windows drivers.

---

### Post by lminier on 2010-11-08
There's actually an easy fix for this bug:
sudo modprobe -r r8169 && sudo modprobe r8169

This seems to only be needed once.

[https://bugs.launchpad.net/linux/+bug/672387](https://bugs.launchpad.net/linux/+bug/672387)

---

### Post by NiksaVel on 2010-11-18
Exactly the same problem with Gigabyte GA-890FX-UD5 board...   pulling the power cord brings it back to life as described

---

### Post by DrAspirin on 2010-11-21
I also have the same issue with Gigabyte GA-H55M-UD2H. I installed 10.10 and had major problems. I solved this by changing the NIC to 100Mbit duplex from Gigabit in Win 7 64 bit. This has worked for the last few weeks but the latest Ubuntu updates has broken it again - this time messing about with speeds and duplex makes no difference. That is the end of my Ubuntu experience for the time being and the disk installed with Win 7 only. Shame, I really did like the OS. I'll be back when this bug is fixed.  

Neil.

---

### Post by mnclayshooter on 2011-03-01
I realize this is a little old, but it seems that a few people I know also have the Gigabyte P55A-UD3 motherboard and have had ethernet problems.  100% of them were resolved by the complete power "reset".  Unplugging or switching off the power supply (not just the power switch you use to turn the machine on or off), then turning it back on/plugging it back in resolved the issue.  
 
Just wanted to add that as it seems the most of the people who've had this problem have had it after about 7 months and after doing a kernel update.

---

### Post by Aberanta on 2012-11-21
Incredible!! It just works :-D

The question now is if it will survive the next kernel update... sincerely... i'm scared...

Anyway, thanks for the "solution" :-)

---

### Post by wildmanne39 on 2012-11-21
Old thread closed.

---

