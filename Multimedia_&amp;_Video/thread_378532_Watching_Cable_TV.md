---
title: "Watching Cable TV?"
date: 2007-03-07
forum: Multimedia &amp; Video
---

### Post by nifocmike on 2007-03-07
Hi folks!

I'm trying to figure out by searching through these forums what would be the "best" way to set up Ubuntu for watching Cable TV but so far I haven't found nothing that really answers that question.

The video card installed is a Radeon 9200 with a standard coax cable with F connectors connected to the video card like you would on a regular TV.

The Cable TV comes through fine on the Winblows side of the computer, now I would like to do the same on the Ubuntu side.

So my questions is: Now what?

Thanks!

---

### Post by punx45 on 2007-03-07
first step is always knowing exactly what hardware you are working with.   often just the manufacturer/model is not enough because some manufacturers use different chips with various revisions of the same hardware.

so first things first:  go to a command line, and enter 'lspci' then copy the output of that here.

---

### Post by nifocmike on 2007-03-08
Okay. Here are the results:

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200] (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
02:09.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
02:0a.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
02:0a.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 07)
02:0e.0 FireWire (IEEE 1394): NEC Corporation uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr (rev 01)

Thanks for the quick response!

---

### Post by punx45 on 2007-03-12
this is your Tuner card.
```
02:09.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
```

thats the same chipset I have in my Hauppage PVR-150.   It uses the ivtv driver.

you can see here for the IVTV main page [http://ivtvdriver.org/index.php/Main_Page](http://ivtvdriver.org/index.php/Main_Page)

as well as the ubuntu howto here:   [http://ivtvdriver.org/index.php/Howto:Ubuntu](http://ivtvdriver.org/index.php/Howto:Ubuntu)

after you get that installed you should be able to do basic viewing/capturing.   if you want more advanced features like listings guide and scheduled recording look into PVR programs like MythTV.

---

### Post by majoridiot on 2007-03-14
if it is a digital cable box, look to see if it has a firewire port on it.  if so, it might be active and would 
give you the option of having 2 tuners if you go the mythtv route- plus it would likely be much better
quality pic and sound.

if your stb does have firewire (and your computer, too), you can check to see if it is active by following 
the first part of this:

[https://help.ubuntu.com/community/MythTV_Edgy_Firewire](https://help.ubuntu.com/community/MythTV_Edgy_Firewire)

the overall mythtv guide is here:

[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

---

