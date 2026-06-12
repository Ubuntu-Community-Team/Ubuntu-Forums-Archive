---
title: "Broadcom problem on Compaq 6515b"
date: 2009-12-07
forum: Networking &amp; Wireless
---

### Post by stark222000 on 2009-12-07
I've looked all over the forums and i've found a bunch of things that supposedly solve my problem but nothing has worked. basically there is no driver for my computer so i have to get a new one to connect wirelessly. the problem with this computer is it has a touch button for turning on the wireless but it won't turn on and i can't seem to figure out how to solve the problem or install the driver. i'm running 9.10. help greatly appreciated.

---

### Post by lexfati on 2009-12-07
There are open source drivers for many Broadcom wireless cards.  Others require Broadcom's proprietary driver.  In order to determine which you need, we need to know your wireless card's specific info.

You can find this info by entering these commands into a terminal (the terminal can be found from the menu under Applications > Accessories > Terminal )

```
lspci | grep Broadcom
```
This will tell which card you have(if you don't get anything from this, try just lspci).

```
lspci -vnn | grep 14e4
``` This command will give an ID for your card, which will help determine if the free drivers support your card.  The [[COLOR="Blue"]b43[/COLOR]]("http://linuxwireless.org/en/users/Drivers/b43") site has more info.  

Please post your output from these commands so we know just what you have.

---

### Post by stark222000 on 2009-12-07
10:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)

EDIT:

and this is the second outcome from the other code

Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02)

---

### Post by lexfati on 2009-12-07
That appears to be an ethernet controller.  Most Broadcom wireless start with BCM43.  Maybe your wireless card is another brand.

Lets try lspci again without the 'grep'
```
lspci
``` unless your wireless card is a usb adapter, if so try 
```
lsusb
```

---

### Post by stark222000 on 2009-12-07
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Device 7914
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
02:04.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b6)
02:04.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 02)
10:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)

thats from the first code

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

and thats the usb one

---

### Post by lexfati on 2009-12-07
stark222000 - I'm looking, but I'm not recognizing anything in those lists as a wireless card.  At the moment I'm perplexed.  I've tried googling the [Compaq 6515b ]("http://h18000.www1.hp.com/products/quickspecs/12674_div/12674_div.HTML") and as you can see, a number of different wireless cards are listed.  

As best I can tell, the [proprietary driver]("http://www.broadcom.com/support/802.11/linux_sta.php")'s README  suggests it supports them.  I recall reading that this driver is included with Ubuntu.  Though I can't be certain because I don't use GNOME, I think you can look in System > Hardware to see if the driver is listed.

I'm curious why we aren't seeing a wireless card in your output lists, though.  In your first post you mentioned there is a power button for the wireless card?  I wonder if that makes any difference.

---

### Post by stark222000 on 2009-12-08
that very well could make a difference, earlier today i was having trouble installing ubuntu so i tried installing 9.04 and it asked me to download those proprietary things you were talking about while i was updating to 9.10 and when i restarted it ****** up my graphics card so i just got a new iso and reinstalled everything but now there is nothing in the hardware drivers. and yeah you have to touch this sensor thing which makes the light turn blue but it won't let me turn it on on ubuntu. i've tried a lot of things today to fix this so that may have something else to do with it.

---

### Post by lexfati on 2009-12-08
This thread includes a procedure for getting the wireless to work on a slew of HP machines, and the Compaq 6515b is included.  It does involve a lot of command line work, though.  It basically is a method for using the Windows drivers on Linux.    

[http://ubuntuforums.org/showthread.php?t=769990&highlight=compaq+6515b]("http://ubuntuforums.org/showthread.php?t=769990&highlight=compaq+6515b")

It does mention that switch for the wireless on these machines is a critical issue.  If the switch can be toggled, you may want to do that and try those commands again to see if you can get your wireless card to show up.

If you decide to try tackling this, best of luck.  Its time I sign off for the night, though.

---

### Post by stark222000 on 2009-12-08
yeah i went through that earlier today the only problem is i can't toggle the light

---

### Post by stark222000 on 2009-12-08
well i have pretty much figured out that that blue light is the reason that it doesn't recognise a wireless card. so my question now is is there any way for me to force turn it on in terminal? i don't know much about linux yet but can't i turn on all the usb controllers one by one and figure out which one controls the blue light one or am i completely wrong. or can i turn it on in BIOS or something? i tried in bios a little bit but i didn't really know what i was doing.

---

### Post by stark222000 on 2009-12-08
HOLY ******* **** I DID IT. sorry but i am way excited now. if you ever come across this problem again all i did was go into bios and turn off power save for WLAN and stuff and i went on windows to turn it on and when i came back on ubuntu it auto turned on. i am so happy thank you for all your hope though.

---

