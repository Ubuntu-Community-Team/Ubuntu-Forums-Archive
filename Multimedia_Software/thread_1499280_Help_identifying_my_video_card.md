---
title: "Help identifying my video card?"
date: 2010-06-01
forum: Multimedia Software
---

### Post by ispy on 2010-06-01
I don't have my video card registering in ubuntu 10.04 (or any of the previous 4 versions, for that matter; I'm just getting around to this)

Here's the output of lspci:

```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 651 Host (rev 02)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 Communication controller: Conexant Systems, Inc. HSF 56k HSFi Modem (rev 01)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter

```

Any help?

The computer is old, so I won't be surprised if there's nothing available anymore.

---

### Post by cbrunhaver on 2010-06-01
[http://www.uluga.ubuntuforums.org/showthread.php?t=1248930](http://www.uluga.ubuntuforums.org/showthread.php?t=1248930)

It looks like there is no DRI support, though I think 2D should still work, though it doesn't sound promising.

-Chris

---

### Post by drreed on 2010-06-01
Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter.

I believe this is an integrated (onboard) video chip that leads to a d-sub 
connector soldered to your motherboard, to which you connect your VGA display.

You don't have a video card. 

Have you opened the case to see what your VGA cable is actually connected to?

If it's an old computer then you could get by with just about any older dedicated graphics card that your motherboard would support. 
You may have a card in another computer, or a friend that has one gathering dust. It would get you by until you build your new system.
Choose an geforce or radeon, either one. Don't go hog-wld and buy the latest thing that in all appearances your system should support, because
it no doubt has an old bios that may not support the latest PCI 1.0 x 16 or the last of the AGP card produced. Try to find a working used card
from a friend.

---

### Post by ispy on 2010-06-01
That would explain why it's so slow. It's not actually my computer, so I can't open it up, but what you said is consistent with what I've seen in the documentation.

Do you know if there's a proprietary driver or anything I need to install? Or is it built into the kernel already?

---

### Post by cascade9 on 2010-06-01
It should work with the xserver-xorg-video-sis package, but you wont get any 3D, etc. 

Virtually anything would be better..if you've got a desktop machine, se if you can find a video card to fit it. I'd think it was  desktop but you've got a conexant modem installed.....I spose it still copuld be a  desktop, but if it was me, I'd be removing that useless thing straight away ;) 

> **drreed said:**
> Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter.

I believe this is an integrated (onboard) video chip that leads to a d-sub 
connector soldered to your motherboard, to which you connect your VGA display.

You don't have a video card. 

Have you opened the case to see what your VGA cable is actually connected to?

People tend to use 'card' for onboard video as well. 

BTW, you dont need to open the case, you can tell from the position of the VGA port- if it is parallel to the case, in with the USB/parallel/serial/ethernet/ps/2 etc ports, etc and close to the edge of the case then its onboard (in most cases). If its 90degrees to the motherboard, and has the destinctive makings of a slot around it, its a card.

---

### Post by ispy on 2010-06-01
@cbrunhaver Oh, that explains it. Alright, never mind. Time to upgrade the ram, since the owner isn't ready to scrap the computer yet. All she does with it is watch videos anyway.

---

### Post by ispy on 2010-06-01
It's impossible to find a 32 bit video card on newegg, so I looked around and found this.

[http://www.shopping.com/xPO-Sapphire-64MB-Sapphire-Radeon-9100-DDR-DVI-VGA-VIVO-AGP-100546-95547614](http://www.shopping.com/xPO-Sapphire-64MB-Sapphire-Radeon-9100-DDR-DVI-VGA-VIVO-AGP-100546-95547614)

Worth it? What significant improvement will I see if I install this?

---

### Post by cascade9 on 2010-06-01
> **ispy said:**
> It's impossible to find a 32 bit video card on newegg, so I looked around and found this.

[http://www.shopping.com/xPO-Sapphire-64MB-Sapphire-Radeon-9100-DDR-DVI-VGA-VIVO-AGP-100546-95547614](http://www.shopping.com/xPO-Sapphire-64MB-Sapphire-Radeon-9100-DDR-DVI-VGA-VIVO-AGP-100546-95547614)

Worth it? What significant improvement will I see if I install this?

32bit video card? :S Umm.....you probably want an AGP card (like the 9100 you linked above). As for that card, its out of ther frying pan, into the fire. The ATI 9XXX cards have no support from ATI anymore, and untill the open source drivers get a fair bit more work done to them, there will be no 3D there either. 

It would be an improvement over the SiS video, if only because you would get a bit more memory back (no more RAM sharing). But you would be better of with something like this- 

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814125249](http://www.newegg.com/Product/Product.aspx?Item=N82E16814125249)

A GF6200. Actually has current drivers. ;) 

Its just a pity that AGP cards are so expensive now, a PCIe card with more features, power etc is cheaper .

*edit- check you actually have an AGP slot before you go buying stuff.  ;)

---

### Post by ispy on 2010-06-01
I have an AGP slot, but it only supports 66Mhz, 32 bit cards. This is a very old computer.

It also has 2 PCI slots, but I need to check if those are available.

*edit: Looks like only one PCI slot is used.

---

### Post by cascade9 on 2010-06-01
All AGP slots are 66Mhz, 32bit (there was a draft for 64bit AGP but it never came out). 

The main issue yo will have with AGP is if its 1x, 2x, 4x or 8x. The original 1x and 2x solts were 3.3 volts, 4x was 1.5 volts, and 8x was 0.8 volts. 

What motherboard is it exactly? if you go console and enter- 

sudo lshw 

you will get the motherboard model, eg- 

```
*-core
       description: Motherboard
       product: MS-7388
       vendor: MICRO-STAR INTERNATIONAL CO.,LTD
       physical id: 0
       version: 1.0
       serial: To be filled by O.E.M.
       slot: To Be Filled By O.E.M.

```

---

### Post by ispy on 2010-06-01
This is it. Nothing in the manual about 1x, 2x, 4x, or 8x.

```
 *-core
       description: Motherboard
       product: MS-6769
       vendor: MICRO-STAR INTERNATIONAL CO., LTD
       physical id: 0

```

---

### Post by cascade9 on 2010-06-01
I was hoping it wouldnt be a MSI, the site is awful to navigate. Oh well, it could have been worse. 

Typical MSI, they haev several boards with the same number (MS-6769), see here- 

[http://www.msi.com/index.php?func=prodcpusupport&maincat_no=1&cat2_no=&cat3_no=&prod_no=539](http://www.msi.com/index.php?func=prodcpusupport&maincat_no=1&cat2_no=&cat3_no=&prod_no=539)

[http://www.msi.com/index.php?func=prodcpusupport&maincat_no=1&cat2_no=&cat3_no=&prod_no=540](http://www.msi.com/index.php?func=prodcpusupport&maincat_no=1&cat2_no=&cat3_no=&prod_no=540)

Either way, its a SiS 650/651 chipset (probably the 651 LOL), and it should support 2x and 4x AGP cards. Which means that virtually any AGP card should work ;)

---

### Post by ispy on 2010-06-01
I'm ordering the one you suggested, this computer is likely going to be a secondary as the owner is buying a new one as we speak. She just wanted to save this one for others to use. Thanks so much for your help.

---

### Post by cascade9 on 2010-06-02
No problem :) 

Good luck to your friend and her new computer, and with the video card ;)

---

### Post by drreed on 2010-06-02
> **ispy said:**
> I have an AGP slot, but it only supports 66Mhz, 32 bit cards. This is a very old computer.

It also has 2 PCI slots, but I need to check if those are available.

*edit: Looks like only one PCI slot is used.

before spending cash money, check the bios version on the board and see what's available. As I mentioned before, any new card you buy is much newer than your bios. It may require an update to the board before installation. For example, I have an oldish ECS crossfire board with a PCI x 16. I can still buy new cards for this board, but most would not work without a bios upgrade because they have feature sets that were unavailable when my bios was last updated. That's why I suggested a used card from the same time frame, or within a couple years. 

But [I]I was just trying to save you some aggravation. However, if you don't mind going over to this girls house and updating bios's etc., thats another matter . . . 
:)

**edit** I had visions of you hunched over a tiny computer shelf she calls a desk, surrounded by unicorns and glass figurines, breaking a sweat because your having a problem flashing the BIOS on a relic that isn't worth what you paid for the card (on a Saturday) because your bound and determined to see it through to the end. Have an escape clause . . .
[/I]
An example (using this board) of problems one encounters fooling around with old hardware: [http://forum-en.msi.com/index.php?topic=124132.0](http://forum-en.msi.com/index.php?topic=124132.0)

---

### Post by cascade9 on 2010-06-03
> **drreed said:**
> before spending cash money, check the bios version on the board and see what's available. As I mentioned before, any new card you buy is much newer than your bios. It may require an update to the board before installation. For example, I have an oldish ECS crossfire board with a PCI x 16. I can still buy new cards for this board, but most would not work without a bios upgrade because they have feature sets that were unavailable when my bios was last updated. That's why I suggested a used card from the same time frame, or within a couple years. 

I've heard of this before, and its always been because of the BIOS that some ECS systems shipped with- they had 'locked' the BIOS so you couldnt use an PCIe video card in teh PCIe slot! 

Be thankful they actually made an update, some of the manufacturers that ECS made systems for (eg emachines) never unlocked the BIOS, and I've heard of them making unlocked BIOSes and then trying to charge money for the update :| 

I've played with many AGP systems, in in the vast majority of cases, AGP works fine. Its far less likely to be locked like what happened with some of the PCIe systems, about the worst I've seen has been systems where you cant actually turn off the onbaord video at all. 

Noteverybody has access to nice, ancient AGP cards. Maybe things are better when you are, but here, if you try to find a 2nd hand card from a dealer, they will try to charge far more than what they are worth (I got told that a AGP GF/GF2 was worth aprox $75 US when I tried to pick one up about 2 years ago.....even though I know my hardware backwards).  

> **drreed said:**
> 
But [I]I was just trying to save you some aggravation. However, if you don't mind going over to this girls house and updating bios's etc., thats another matter . . . 
:)

**edit** I had visions of you hunched over a tiny computer shelf she calls a desk, surrounded by unicorns and glass figurines, breaking a sweat because your having a problem flashing the BIOS on a relic that isn't worth what you paid for the card (on a Saturday) because your bound and determined to see it through to the end. Have an escape clause . . .[/I]

If that system needs a BIOS update to get a AGP card going, I would be very suprised. Not that updating the BIOS is going to be that hard, MSI still has the updates up (not that any of them have anything to do with AGPm, AGPgart or video cards)

I wouldnt say that system is worth less than a $40 AGP 6200 as well, but that is relative.... 

> **drreed said:**
> 
An example (using this board) of problems one encounters fooling around with old hardware: [http://forum-en.msi.com/index.php?topic=124132.0](http://forum-en.msi.com/index.php?topic=124132.0)

You did read that thread, right? That was just because the poster couldnt find the drivers (typical SiS), and it was for XP.

---

### Post by cbrunhaver on 2010-06-15
I'm sorry I missed following up with this thread.  

I would HIGHLY recommend getting a newer nVidia card for video playback.  It breathed new life into my daughter computer (older p4 based machine) and I use it for movie playback in her room using XBMC.

SMplayer fully supports VDPAU and so this thing will chew right through MPEG-2 and H.264 (but not flash under linux).  Don't be put off by the PCI interface - it performs much better than most AGP options out there (using older chipsets etc)

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814127472&cm_re=8400GS_PCI-_-14-127-472-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16814127472&cm_re=8400GS_PCI-_-14-127-472-_-Product)

---

