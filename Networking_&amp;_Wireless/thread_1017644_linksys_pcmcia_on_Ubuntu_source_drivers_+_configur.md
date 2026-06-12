---
title: "linksys pcmcia on Ubuntu source drivers + configure"
date: 2008-12-21
forum: Networking &amp; Wireless
---

### Post by thy1 on 2008-12-21
I'm using the latest Ubuntu and can't get my Linksys PCMCIA wireless card working.

I am completely new using this operating system - but learning fast, and love it!

I read somewhere that I need to download the RT61_Linux_STA_Drv1.0.4.0.tar.gz source drivers, but all links seem to be dead? Is this the correct route I am taking? If yes, where can I get this source drivers and what to do next?

Many Thanks!!!

---

### Post by ieee488 on 2008-12-21
It would be much easier for you to to tell us the model of your PCMCIA modem that you have, and then we can go from there.

---

### Post by thy1 on 2008-12-21
> **ieee488 said:**
> It would be much easier for you to to tell us the model of your PCMCIA modem that you have, and then we can go from there.

My bad! Thought they were very generic.

Linksys 2.4 Ghz Wireless-G 802.11g Notebook Adapter.

Many thanks!!

---

### Post by ieee488 on 2008-12-21
Sorry, that is not a model number, that is a description.

For example, a Linksys WPC100, etc.

---

### Post by thy1 on 2008-12-21
> **ieee488 said:**
> Sorry, that is not a model number, that is a description.

For example, a Linksys WPC100, etc.

Ahhhhhhhhhhhhhhhhhhhhhh - I'm so computer illiterate! But I refuse to go back to Windows! lol

WPC54G ver 5.

---

### Post by hockeyshifter on 2008-12-21
look on the back of the card. look for the model mo. ( mine is wpc11 ver. 4)
got to this page and look for futher instruction. 

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

i am having similar issues and you are not alone.. this appears to be a larger issue with the current kernel on ubuntu. 

have fun .. this is a very good OS but we always seem to be a step behind. 

next open a terminal from Applications > Accesories > Terminal 

type  lspci in the command line then post back the results. i can't read code yet but learn fast i will. LSPCI will tell us if your card is working 

later

---

### Post by thy1 on 2008-12-21
> 

type  lspci in the command line then post back the results. i can't read code yet but learn fast i will. LSPCI will tell us if your card is working 

later

I got a feeling but not certain that it hasn't picked up the card as the lights are not flashing on the PCMCIA card. Also got a duel boot of WinXP (will be deleted) which lights come on at the login screen and working fine.

I'm changing away from Windows because of Viruses and Spyware, after corrupted my NTFS Partition structure losing all my lovely holiday pictures!

So determined to get Ubuntu working now with my PCMCIA card. Here's my lspci - Thanks again:

liu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:00.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:00.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
07:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
j

---

### Post by dwanders on 2009-01-06
I was experiencing issues with my WPC11 Ver 3. Everything in XUbuntu 8.04 was working fine with the card - very nice old laptop perfect for web browsing only etc... 

I finally got around to doing a clean install of 8.10 and the card stopped working. 

I started messing about with the ndiswrapper stuff, and then the Linksys driver download - and got so annoyed with it all that I just got a different card. 

Just dont get why it was working fine in 8.04 and crapped out in 8.10 its a bummer though - cause I guarantee most users wont go out and get a card that is reported to work with Ubuntu, sadly they will run back to windows blaming Ubuntu for all their troubles.

---

