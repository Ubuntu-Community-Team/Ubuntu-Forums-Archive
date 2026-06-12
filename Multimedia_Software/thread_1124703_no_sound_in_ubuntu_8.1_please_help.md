---
title: "no sound in ubuntu 8.1 please help"
date: 2009-04-13
forum: Multimedia Software
---

### Post by Blue+Linux on 2009-04-13
hey
i recently got my old laptop fixed so i could use it to experiment with various linux distributions.

i installed ubuntu and love it, the sound worked at first but now it no longer does. why? 

i tried reinstalling ubuntu twice! but to no avail. i had xp on the laptop aswell so i booted it up and the sound worked o.O im a newbie to linux obviously but over the last 3 days ive got familiar with the basics.

I also tried installing mandriva and suse but the audio doesnt work on them either.

ive looked through the forums but nothing seems to help so if you have the patience to show me what to do it would be greatly appreciated

add my msn [email]samclayton33@hotmail.co.uk[/email] <--- its easier and faster than posting your reply on the forum :)

or just post

i look forward to hearing from you :) thanks

Blue

---

### Post by connorh123 on 2009-04-13
I have the same problem =/

---

### Post by djbushido on 2009-04-13
Can you post what happens when you do this command:"lspci"
This will tell us the pci chips you have, so we can move forward.
Also, make sure packages relating to pulse-audio and alsa are installed in synaptic. Actually, only alsa is needed, pulse recommended.

---

### Post by Blue+Linux on 2009-04-13
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:07.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:07.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
02:07.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
02:08.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:09.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

---

### Post by Blue+Linux on 2009-04-13
and yes i do believe i have packages
abd thanks for the reply
it was faster than i expected :)

---

### Post by djbushido on 2009-04-13
Hmmm... First things first, you can add your msn in the user panel to the forum, and if you want live help, look up IRC - #ubuntu on freenode
Anyway, it looks like you have a very generic soundcard, I have no idea what the problem would be. Also, check to make sure all wires are plugged in and not chewed through by various pets. See my sig.

---

### Post by Blue+Linux on 2009-04-13
im on a laptop so there is no wires :) only a power lead and mouse. ill do the live support thing but im not sure how helpful that will be. thanks for your help
if it doesnt get fixed ill just go back to xp aha 
ive spent days trying to fix the audio and im sick of it xD
thanks again

---

### Post by djbushido on 2009-04-13
Oh, so it's going to a laptop speaker? In that case, it may be out of the range of default linux because it is quite possible that it is hard-wired to the motherboard (the speaker - AC'97 may be controlling headphone out). At least try headphones to make sure that Linux is at least producing sound.

---

### Post by Blue+Linux on 2009-04-13
there is no sound being produced at all
even with headphones :/

---

### Post by djbushido on 2009-04-13
And you said that windows can produce sound right?
Very weird...
I use a Via AC97, but I don't see why Intel wouldn't work...
That's very weird, I'm sorry I don't know what else to do...

---

### Post by Blue+Linux on 2009-04-13
yes windows was producing sound fine
no worries
thanks very much for your help :)

---

### Post by Blue+Linux on 2009-04-13
fixed

---

