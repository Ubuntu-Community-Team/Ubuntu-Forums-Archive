---
title: "Ubuntu can't find Wifi card"
date: 2010-01-22
forum: Networking &amp; Wireless
---

### Post by flash722 on 2010-01-22
Hello everyone,

Ubuntu 9.04 running on a Dell C640 with a Dell TrueMobile 1150 wireless card.  Works perfectly under XP.  Ubuntu can't find it.  Wired networking finds the internet perfectly (though I'm still working on getting samba set up correctly for file/print sharing on my XP LAN).

I'm thinking I need a driver, maybe?  Can't seem to locate one.

Suggestions?

Thanks in advance!

Adam

---

### Post by bkratz on 2010-01-22
Please go to the terminal   Applications>>Accessories>>Terminal
and type in

lspci (that is LSPCI in lowercase), copy/paste the output back here.

---

### Post by flash722 on 2010-01-22
Here you go....  Thanks for helping!

(hmmm...  doesn't appear to list the Wireless card...   methinks this is a clue...  :)  )

00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:01.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:01.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:03.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)

---

### Post by jml on 2010-01-22
The output indicates that Ubuntu does not "see" your wireless card.  According to the limited research I did, the TrueMobile 1150 uses the Hermes 3 chip set.  This chip set is reportedly well supported under Linux.  When you did your installation of Ubuntu, did you have the wireless card inserted into the laptop?  If not, the  problem may be that the required driver was not loaded during your install.  If the card was inserted during the install, then I am a bit stumped.  It's possible that Ubuntu may have dropped support for your card.  But that seems unlikely.  One idea is to boot from the live Ubuntu disc while your wireless card is plugged in.  Once at the desk top, see if the card shows up in network manager.  Then see if you can get it to connect.  Good luck.

Joe

---

### Post by bkratz on 2010-01-22
You might want to check and see if the wireless is enabled in the bios. Sometimes strange things happen and Windows doesn't always treat the wireless fairly, depending on how you shut it down and Ubuntu gets the blame!  Also, check if there is some keystroke or switch that needs to be on.

---

### Post by flash722 on 2010-01-22
WiFi card is turned on in the bios.  Remains so after shutting down XP.   A key combination?  Never heard of needing to do this before.  

Quite frustrating indeed.  I'm liking my Ubuntu setup but obviously a non-working WiFi is a deal-breaker...  :(   Also still can't XP to see the Ubuntu system on the network.  

Hoping some more people have suggestions on this one.  I'm still pretty new to Linux.


Adam

---

### Post by bkratz on 2010-01-22
> **flash722 said:**
> WiFi card is turned on in the bios.  Remains so after shutting down XP.   A key combination?  Never heard of needing to do this before.  

Quite frustrating indeed.  I'm liking my Ubuntu setup but obviously a non-working WiFi is a deal-breaker...  :(   Also still can't XP to see the Ubuntu system on the network.  

Hoping some more people have suggestions on this one.  I'm still pretty new to Linux.


Adam



Here is a quote explaining what I meant from another thread

"I was experiencing this exact issue with a Dell Inspiron 600m. After trying a couple of things, it turned out it was a pretty simle fix. Function Key (FN) + F2 turns on and off the wireless radio (the F2 key has a dark blue antenna icon on it next to the white F2 label). Pretty obvious, but I just wasn't thinking it could be something simple like that.

If anything is odd about it, the BIOS says the wireless radio is on, but a default Ubuntu install reports the radio off. Hitting FN + F2 fixed it immediately and the wireless access points SSIDs showed up."


This is how keystrokes can turn off the card.

---

### Post by flash722 on 2010-01-22
Hmmm...  thanks for the tip...  I"ll try it now...   interestingly enough, I tried the other suggestion again of booting into a live session from the CD...  THIS time it indeed recognizes the wireless card!  (I'm typing this using it).  I'll try the fn+f2 suggestion from my normal boot...  

Thanks SO much everyone!  What an awesome community!



Adam

---

### Post by flash722 on 2010-01-22
GO FIGURE!!!   Just booted back into Ubuntu and the wifi worked just fine...   the ONLY thing I can think of that I didn't mention earlier is that while I was checking the bios to be sure the card was enabled, I turned it off and then back on again....  maybe that made nice nice with the card...

....on to getting my samba sharing to work properly...  but I'll post that in the correct forum...  :)

Thanks!

Adam

---

### Post by flash722 on 2010-01-22
By the way...  card still doesn't show up in the list when I run the lspci command....  'but then...  I'm using it right now, so....  :)

---

### Post by bkratz on 2010-01-22
> **flash722 said:**
> By the way...  card still doesn't show up in the list when I run the lspci command....  'but then...  I'm using it right now, so....  :)

Glad to hear you got it working!  Still curious though perhaps the internal card is actually on the internal USB.

Just for grins try typing in

lsusb and see if it appears.

---

