---
title: "MythTV Setup Issues"
date: 2009-03-28
forum: Multimedia Software
---

### Post by 3givor on 2009-03-28
I normally don't post new threads on a topic, because the forums here along with other tutorials I have read on MythTV are so good, but I am stumped! I have a system with two PVR-150 tuners in it that will not let me configure the capture cards in MythTV. I have the following hardware:

Gigabyte M61PME-2SP motherboard (with integrated GeForce 6150 video)
AMD Athlon X2 7750 Processor
4GB Corsair XMS2 DDR2-800 RAM
Western Digital 80GB IDE drive (system)
2 - 750GB Seagate SATA drives in a software RAID0 (media storage)
2 - Hauppauge PVR-150 tuners

The setup of Ubuntu server (Intrepid AMD64) goes smoothly and all hardware is found and installed correctly. The MythTV install goes very well until I start mythtv-setup and try to add the capture cards. No matter what slot I put the cards in nor whether there are one or two in the system mythtv-setup will not let me add the cards in step 2 of the set up. I choose the MPEG2 (PVR-150, 250, etc.) and it just tells me 'failed to open' in the card status. The output of dmesg looks good:

[    7.169446] ivtv:  Start initialization, version 1.4.0
[    7.169504] ivtv0: Initializing card #0
[    7.169506] ivtv0: Autodetected Hauppauge card (cx23416 based)
[    7.170217] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[    7.170223] ivtv 0000:01:06.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[    7.170230] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[    7.223016] tveeprom 2-0050: Hauppauge model 26552, rev F168, serial# 9920920
[    7.223018] tveeprom 2-0050: tuner model is LG TAPE H001F MK3 (idx 68, type 47)
[    7.223021] tveeprom 2-0050: TV standards NTSC(M) (eeprom 0x08)
[    7.223022] tveeprom 2-0050: audio processor is CX25843 (idx 37)
[    7.223024] tveeprom 2-0050: decoder processor is CX25843 (idx 30)
[    7.223025] tveeprom 2-0050: has radio
[    7.223027] ivtv0: Autodetected Hauppauge WinTV PVR-150
[    7.275290] cx25840 2-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #0)
[    7.320851] tuner 2-0043: chip found @ 0x86 (ivtv i2c driver #0)
[    7.325395] tda9887 2-0043: creating new instance
[    7.325397] tda9887 2-0043: tda988[5/6/7] found
[    7.326690] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[    7.326705] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #0)
[    7.340624] tuner-simple 2-0061: creating new instance
[    7.340626] tuner-simple 2-0061: type set to 47 (LG NTSC (TAPE series))
[    7.357408] cx25840 2-0044: firmware: requesting v4l-cx25840.fw
[   10.808693] cx25840 2-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   10.878755] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   10.878769] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   10.878780] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   10.878793] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   10.878804] ivtv0: Registered device radio0 for encoder radio
[   10.878805] ivtv0: Initialized card #0: Hauppauge WinTV PVR-150
[   10.878818] ivtv:  End initialization

And, I can run 'cat /dev/video0 > /tmp/test.mpg' and get clean video.

I don't know where else to go with this.

Thanks in advance,

Ivor

---

### Post by wolfen69 on 2009-03-28
did you install ivtv-utils?

---

### Post by 3givor on 2009-03-28
I have them installed, but don't know how to use them. I have been using MythTV for over two years and have never had to go any deeper than resetting a few passwords. My apologies for my ignorance.

---

### Post by wolfen69 on 2009-03-28
perhaps there is something lacking in the server kernel that is needed. just a guess.

---

### Post by 3givor on 2009-03-28
I just tried a mythbuntu install without the RAID0 and it appears to work. Downloading an alternate ISO now and will post results with that. It looks like it might be a kernel issue after all.

---

### Post by 3givor on 2009-04-02
This was indeed a kernel issue. Reinstalling with the Mythbuntu alternate CD allowed me to see all three of my PVR-150s, my HVR-1600, and my WinTV-PVR-USB2 right out of the box...

---

### Post by 3givor on 2009-04-22
So I have been two weeks on the new system (minus the WinTV-PVR-USB2 because of the hanging on boot issue posted elsewhere) and the backend is solid. I now have a frontend issue that I am hoping someone can help with. I am using a Sony Bravia 42" LCD HDTV in my living room and trying to plug a Myth frontend box into it as the primary media source. I have the following hardware:

Antec Fusion 430 case
Asus AM2-VM motherboard
AMD Athlon X2 4400 processor
ATI Radeon X1550 (MSI version)
2GB DDR2-667 RAM
320GB SATA drive
TSST DVD-RW

I have loaded Mythbuntu 8.10 AMD64 desktop with frontend and Xubuntu desktop roles with no problem and can use the system as a desktop with the TV displaying 1920x1080 resolution just fine. The video is DVI out of the X1550 to VGA in on the TV, since the TV does not have DVI, only HDMI inputs, btw.

Now, the problem; every time I load Mythfrontend the display gets all wonky. It looks like th screen splits in two and the sync is way off, because I can sort of make out the dialog about prescaling theme images, but the frontend never 'settles down'. It's as though Myth is using completely different sync rates or resolution for the frontend. Has anyone seen this before or do I need to dump the VGA and find an HDMI-capable motherboard or something?

---

### Post by wolfen69 on 2009-04-22
ati cards have been known to have serious issues when attempting to do anything besides normal usage. if you have a spare nvidia card you can use to test, it will tell you a lot.

---

### Post by georgek on 2009-05-06
Even though you're OK now, I hit the same problem yesterday and, for the sake of anyone else who gets here before they find out the answer, here's what I found out.

My problem was that I was running mythtv-setup as a user other than mythtv (using ssh -X from another box but I don't think that made any difference).

To be able to see the dvb card(s) the user has to be in the video group.  User mythtv was but my other user wasn't.  All I needed to do was add my user into the video group (and log out and back in again) and all was fine :)

---

