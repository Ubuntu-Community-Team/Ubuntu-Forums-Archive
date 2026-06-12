---
title: "Virgin Freedom Netbook - speakers are too quiet"
date: 2009-08-18
forum: Multimedia Software
---

### Post by DougEdey on 2009-08-18
I received a Virgin Media Freedom netbook a few weeks ago, try as I might I cannot get the speakers to be louder then a whisper. I've gone through the sound support thread.

Headphones are fine.
The front speakers I can *only* hear if I put my ear right next to the speaker grills and it's kind of rather annoying.

Specs listing from Virgin (I'll grab the UNR output when I get home):

Main Features
Processor 	Intel® Atom™ Processor N270, 1.60 GHz, 533 MHz FSB, 512K L2 Cache
Chipset
BIOS 	Intel® 945 GSE Chipset + ICH-7M FSB 533 MHz
EFI based BIOS, 1 MB
Operating System 	Operating System Genuine Microsoft® Windows® XP Home Edition
System Memory 	1GB DDR2 533 MHz (1 x So-DIMM slot, Max. 2GB)
Storage
Hard Drive 	120GB SATA Hard Drive
Display
Size 	10.2" TFT LCD
Resolution 	WSVGA 1024x600
Backlight 	TFT LCD Backlight
Video/Audio Features
Graphics 	 
Type 	Integrated Intel Graphics
Controller 	Intel® Gen 3.5 Integrated 133 MHz GFX core
VRAM 	64MB Shared Video Memory
Audio 	 
Controller 	Intel® High Definition Audio, Stereo output
Internal Speaker 	2 x 1 W
Internal Mic 	yes
Built-in Webcam 	 
Resolution 	0.3 megapixel
I/O
Input Device 	 
Keyboard 	UK Edition, 77Key+ Windows Function keys
Touchpad with Left/Right Click Buttons
I/O Ports 	1 x Mic in
1 x Headphone out
1 x RJ-45 (Ethernet)
2 x USB 2.0 port
1 x VGA DB 15-pin (External Monitor)
1 x DC-in (AC/DC adapter)
Expansion Slots 	 
Memory Card 	2-in-1 Card Reader (SD/MMC)
Internal Card 	1 x PCI Express Mini Card
Communications
Wireless LAN 	Wireless LAN 802.11 b/g/n
LAN 	10/100 Ethernet
Security
System Boot/HDD Password 	Yes
BIOS Password 	Yes
Kensington Lock 	Yes
Power Management
Battery 	Li-Ion, 3Cell (2S2P), 3300 mAh
Battery Life 	2 hours 30 mins standard use
AC/DC Adapter 	DC 36W 12V / AC 110V~240V 50/60 Hz
Physical Features
Weight 	1.1 kg
Dimensions 	265x182x26mm
Finish 	Gloss laquored finish, pantone referenced

---

### Post by DougEdey on 2009-09-18
So I found how to resolve this at last!

edit /etc/modprobe.d/alsa-base.conf

and add:

```
options snd-hda-intel model=eeepc-p701

``` 

To the end.

Reboot. HEAR THE SOUND!

I've only tried it on Karmic I reckon it should be fine on Jaunty

---

### Post by DougEdey on 2009-09-20
scratch that, the eeePC model does not enable the Headphone socket.

Use model=samsung-nc10 instead

Sorry!

---

### Post by Míse on 2009-09-20
I have a freedom net book with the exact same specs and the exact same problem. i have tried the solution but it tells me that no directory exists. its a shame cos i like ubuntu, i have unbuntu and linux mint on all my pcs, but if i cant get the speakers to work on my net book then im going to have to delete it and stick to windows ;o(

---

### Post by DougEdey on 2009-09-20
Which step? When you try to edit? Could you copy + paste the line you're having issues with? Thanks!

---

### Post by Míse on 2009-09-20
abhristin@ubuntu :~$ edit/etc/modprobe.d/alsa-base.conf  
bash: edit/etc/modprobe.d/alsa-base.conf : no such file or directory

---

### Post by DougEdey on 2009-09-20
You're missing a space, if you're in Ubuntu copy and paste the following line:

gksudo gedit /etc/modprobe.d/alsa.conf

---

### Post by Míse on 2009-09-20
yeah im in ubuntu , thanks .. ill git it whirl now ;o)

---

### Post by Míse on 2009-09-20
ive pased that in and it doesnt do anything 
abhristin@ubuntu:~$ gksudo gedit /etc/modprobe.d/alsa.conf 
abhristin@ubuntu:~$ 

and thats all it does

---

### Post by Míse on 2009-09-20
ive also tried adding in the "base" element to the code, but is it only produces the same result 
abhristin@ubuntu:~$ gksudo gedit /etc/modprobe.d/alsa-base.conf 
abhristin@ubuntu:~$

---

### Post by Míse on 2009-09-21
can anybody help me with this? i like Ubuntu and i dont really want to uninstall it but if the sound doesnt work then i will have to as it works perfectly on windows

---

### Post by Míse on 2009-09-21
abhristin@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 Analog [ALC662 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by Míse on 2009-09-22
may i give a big thank you to [DougEdey]("http://ubuntuforums.org/member.php?u=368104") for all his help. this code does work and i can hear the sound . im very very happy so thank you very much . would you know to acess the web cam ? as i cant seem to access it the same way i would on windows ?

---

### Post by DougEdey on 2009-09-22
Sorry about that I didn't get the email alerts for some reason! What was the problem?

---

### Post by Míse on 2009-09-22
you can access the cam on windows using the the fn f1 combo, but when i try to access it with the ununtu i can find it . the issue with the speakers im not sure, i just rebooted the comp and entered the code again and it worked .. sound precious sound ;o)

---

### Post by DougEdey on 2009-09-22
I'm not sure with the Webcam, I am trying to get the spare LED to light for mine when it's on, but when I pressed FN+F1 it did come on, you may need to restart the application which you want to use it if it was open. But It worked with my install of 8.10 fine.

I'll take another look tomorrow, I left my netbook at work :)

---

### Post by leeagt on 2009-09-23
i;m so grateful to you.mate . I've been trying to get sound on this netbook for over a month. Thanks very much :) your a legend:)

---

### Post by leeagt on 2009-09-23
to get the webcam to work.  Press fn + f1 and then use a program called cheese it's under applications -> Graphics

---

### Post by DougEdey on 2009-09-23
There appears to have been a regression in Ubuntu Karmic, currently trying to work out why but I can't get a colour webcam. That's a seperate thread though so please make a new one if you want to.

---

### Post by Míse on 2009-09-23
well i hade tried other programs from the packet manager but they wouldnt recognise the cam, however cheese has done the trick, and its in colour, so once again mate thank you very much .

---

### Post by macstevejb on 2009-09-25
Thanks for the fix..speakers now working on my netbook at long last!

Webcam has always worked fine for me using Fn+F2...both in cheese and Skype

regards,

:)

---

### Post by dudewhatthehellman on 2009-12-28
hey guys i recently got jolicloud on my vmf and it has the same problem, i put in all those lines and speakers are now working fine with both eeepc and samsung versions but the headphone socket doesnt work, anyone else experiencing this?

---

