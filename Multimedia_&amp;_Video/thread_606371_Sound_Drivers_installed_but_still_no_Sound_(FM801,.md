---
title: "Sound Drivers installed but still no Sound (FM801, Alsa)"
date: 2007-11-07
forum: Multimedia &amp; Video
---

### Post by takai on 2007-11-07
Ive been reading through old threads on here for a while, but to no avail. I just reinstalled my desktop machine at work, and upgraded to Gutsy at the same time. Now sound has gone AWOL.

lspci gives:
> 00:06.0 PCI bridge: Advanced Micro Devices [AMD] AMD-8111 PCI (rev 07)
00:07.0 ISA bridge: Advanced Micro Devices [AMD] AMD-8111 LPC (rev 05)
00:07.1 IDE interface: Advanced Micro Devices [AMD] AMD-8111 IDE (rev 03)
00:07.2 SMBus: Advanced Micro Devices [AMD] AMD-8111 SMBus 2.0 (rev 02)
00:07.3 Bridge: Advanced Micro Devices [AMD] AMD-8111 ACPI (rev 05)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] AMD-8131 PCI-X Bridge (rev 12)
00:0a.1 PIC: Advanced Micro Devices [AMD] AMD-8131 PCI-X IOAPIC (rev 01)
00:0b.0 PCI bridge: Advanced Micro Devices [AMD] AMD-8131 PCI-X Bridge (rev 12)
00:0b.1 PIC: Advanced Micro Devices [AMD] AMD-8131 PCI-X IOAPIC (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
00:19.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:19.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:19.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:19.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 USB Controller: Advanced Micro Devices [AMD] AMD-8111 USB (rev 0b)
01:00.1 USB Controller: Advanced Micro Devices [AMD] AMD-8111 USB (rev 0b)
[b]01:0a.0 Multimedia audio controller: Fortemedia, Inc Xwave QS3000A [FM801] (rev b2)
01:0a.1 Input device controller: Fortemedia, Inc Xwave QS3000A [FM801 game port] (rev b2)[/b]
01:0b.0 Mass storage controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)
01:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
02:09.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5703X Gigabit Ethernet (rev 02)
04:00.0 Host bridge: Advanced Micro Devices [AMD] AMD-8151 System Controller (rev 13)
04:01.0 PCI bridge: Advanced Micro Devices [AMD] AMD-8151 AGP Bridge (rev 13)
05:00.0 VGA compatible controller: ATI Technologies Inc RV350 AQ [Radeon 9600]
05:00.1 Display controller: ATI Technologies Inc RV350 AQ [Radeon 9600] (Secondary)


Which leads me to believe that its an FM801 chipset, and thats certainly what setup detected originally. So FM801 is on the list.
FM801 is listed as loaded by lsmod, and no problems are associated with it in dmesg.

Still alsamixer gives:
> alsamixer

alsamixer: function snd_ctl_open failed for default: No such device

and aplay gives:
> aplay -l
aplay: device_list:204: no soundcards found...


So no avail. The sound preferences dialog gives:
> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.
Which i assume means it just cant open the port or driver.

Following up on a few older leads ive recompiled alsa-utils alsa-drivers and alsa-util from source, and also from the source packages via dpkg, no luck there whatsoever.

Interestingly i did get a brief tidbit of audio when i last rebooted which was that bit on the bongos before or as the login screen is displayed. Which gave me all sorts of hope, before being cruelly dashed again.

Anyone have some suggestions?

---

### Post by takai on 2007-11-08
Anyone? Still stuck here.

---

### Post by bobbyj99 on 2007-11-09
Sorry I know I wont be much help but I am also having a problem with sound in Gutsy. I just had to do a full reinstall and my sound is messing up again. It's not as bad as your problem though, but I am starting to think it's a Gutsy thing...I hope not though.

If your curious, My sound works in everything except games (Second Life, World of Padman and Wormux just to name a few). I searching and if I don't find anything significant to help me I am going to post my own thread.

I know you just reinstalled, but maybe you should try again. I hope you haven't customized too much.

---

### Post by takai on 2007-11-09
Just found out something interesting. It seems that dmesg has stopped updating. I cant add USB devices, or infact anything new to the system. Inserting a CD does nothing, and ive been trying to cause an error which would show up in dmesg, but to no avail.

---

### Post by Yellow Pasque on 2007-11-09
Uninstall the alsa packages. Install OSS, which supports your sound card:
[http://www.4front-tech.com/download.cgi](http://www.4front-tech.com/download.cgi)

Problem solved. :biggrin:

---

### Post by takai on 2007-11-11
> **Temüjin said:**
> Uninstall the alsa packages. Install OSS, which supports your sound card:
[http://www.4front-tech.com/download.cgi](http://www.4front-tech.com/download.cgi)

Problem solved. :biggrin:

Thanks, so the FM801 support in Alsa is actually erroneous. It is listed as supported in the Alsa docs.

---

