---
title: "Onboard sound C-Media 6501"
date: 2007-05-10
forum: Multimedia &amp; Video
---

### Post by Gorlist on 2007-05-10
Hi, fresh install of Ubuntu 7.04 and found it doesn't seem to function with my onboard sound card (motherboard - ASRock AM2NF3-VSTA).

Ive tried following the comprehensive sound guide but ended up getting lost.

help!

Regards,

---

### Post by nerderello on 2007-12-28
just installed the self same mobo, and (with Ubuntu 7.10) had the same problem.

The answer is to set **USB Audio** in the Sound preferences (System > Preferences > Sound). I know that the sound card is installed on the mobo (ie. it is part of the motherboard, not a PCI card nor a USB attached device), and so is definately **not** a USB attached device, but if you open a terminal window (Applications > Accessories > Terminal) and enter the command **lsusb** (to list all USB attached devices) you'll get something like this :
> 
tp@tp-desktop:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0d8c:0201 C-Media Electronics, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 043d:0100 Lexmark International, Inc. 
Bus 001 Device 001: ID 0000:0000 

which shows the C-Media sound 'card' is considered to be a USB device (nb. the Lexmark device is my printer, which really is USB attached).

regards
Nerderello

---

### Post by nerderello on 2007-12-30
Since yesterday's post I've found a better way to solve the sound problem.

To get ALSA working I needed to create a file called **.asoundrc** (the fullstop in front of the name is correct, it makes the file invisible) in my home folder. Using the text editor I input:
> 
 pcm.!default {
        type hw
        card 1
        }

 ctl.!default {
        type hw
        card 1
        }


I think that the important part was that it is card 1 and not card 0.

I then restarted ALSA by entering (in a terminal window) **sudo /etc/init.d/alsa-utils restart**           .

I then went to the sound preferences (System > Preference > Sound) and turned the selections from USB Audio (see my earlier post) to ALSA - Advanced Linux Sound Architecture. And then tried the next tab - Sounds - and played the Login and Logout sounds.

hope this is of use
Nerderello

---

### Post by Yellow Pasque on 2007-12-30
Thanks for posting your findings. I know some users were having trouble with this sound chip

---

### Post by xromano on 2008-05-22
Hi, i find it very interesting. I have on-board card C-Media CMI9761a and it does not work properly under Ubuntu 7.10 as well. However, my USB and PCI list says following:
roman@medion:~$ lsusb
Bus 005 Device 003: ID 03f0:6611 Hewlett-Packard
Bus 005 Device 001: ID 0000:0000 
Bus 003 Device 001: ID 0000:0000 
Bus 001 Device 004: ID 03f0:3c02 Hewlett-Packard PhotoSmart 7350
Bus 001 Device 001: ID 0000:0000 
Bus 004 Device 004: ID 04f2:0200 Chicony Electronics Co., Ltd
Bus 004 Device 005: ID 0bc7:0006 X10 Wireless Technology, Inc.
Bus 004 Device 001: ID 0000:0000 
Bus 002 Device 003: ID 0db0:6982 Micro Star International Medion Flash XL V2.7A Card Reader
Bus 002 Device 001: ID 0000:0000 

Well it is obviously nothing concernig sound here. However, 
roman@medion:~$ lspci
........
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
......
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
....

This Intel ICH5 I found in alsamixer:
Card: Intel ICH5                                                                                               
Chip: C-Media Electronics CMI9761A 

Now I do not understand it. is it possible, that my on-board card is under this ISA bridge? I do not believe it. Could someone check my lists? I would to appreciate it.

---

