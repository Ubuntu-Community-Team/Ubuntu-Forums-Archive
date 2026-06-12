---
title: "Optical S/PDIF does not light up"
date: 2008-11-15
forum: Multimedia Software
---

### Post by tvars on 2008-11-15
Hi,

I've just bought an [Asus M2N68-VM]("http://www.asus.com/products.aspx?modelmenu=2&model=2446&l1=3&l2=149&l3=626&l4=0") motherboard which has digital audio capabilities and optical S/PDIF connector on the back. I installed Mythbuntu 8.10 to set up my media server.

The problem is that I can't get audio through the S/PDIF connector. I've seen many threads that sound similar to my problem but they all end up fixing it by un-muting the "iec958" output using alsamixer. My problem is that this output doesn't even appear as an option on alsamixer. I do have outputs called "Digital" and "PCM" but un-muting them does not help. Even worse, there's no red light coming out of my optical cable!

I'm tearing my hair out, I'm not sure if I'm looking at a OS/driver problem or a faulty motherboard.

Any clues would be much appreciated!

Here's a few prints that may be relevant. What else should I be looking at?

```

tom@mythbox:~$ uname -a
Linux mythbox 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:06 UTC 2008 x86_64 GNU/Linux

tom@mythbox:~$ aplay -L
front:CARD=NVidia,DEV=0
    HDA NVidia, VT1708B Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, VT1708B Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, VT1708B Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, VT1708B Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, VT1708B Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, VT1708B Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
hdmi:CARD=NVidia,DEV=0
    HDA NVidia
    HDMI Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)

tom@mythbox:~$ amixer info
Card default 'NVidia'/'HDA NVidia at 0xdbef8000 irq 21'
  Mixer name	: 'VIA VIA VT1708B 8-Ch'
  Components	: 'HDA:1106e721'
  Controls      : 29
  Simple ctrls  : 16

tom@mythbox:~$ amixer scontrols
Simple mixer control 'Master Front',0
Simple mixer control 'Headphone',0
Simple mixer control 'PCM',0
Simple mixer control 'Front',0
Simple mixer control 'Front Mic',0
Simple mixer control 'Surround',0
Simple mixer control 'Center',0
Simple mixer control 'LFE',0
Simple mixer control 'Side',0
Simple mixer control 'Line',0
Simple mixer control 'CD',0
Simple mixer control 'Mic',0
Simple mixer control 'Capture',0
Simple mixer control 'Capture',1
Simple mixer control 'Digital',0
Simple mixer control 'Input Source',0

tom@mythbox:~$ lspci -vv
...
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
	Subsystem: ASUSTeK Computer Inc. Device 8345
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (500ns min, 1250ns max)
	Interrupt: pin A routed to IRQ 21
	Region 0: Memory at dbef8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
		Masking: 00000000  Pending: 00000000
	Capabilities: [6c] HyperTransport: MSI Mapping Enable+ Fixed+
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel



```

---

### Post by ozrex on 2008-11-17
+1 here.

I have tried the mainboard in Vista, and it seems that the VIA drivers for the chipset (VT1708B) have some form of software switch to determine if audio is send out via HDMI or optical (one at a time, both is not available).  The linux drivers that came with the mainboard CD seem to be a modified Alsa, but are for SUSE linux.

---

### Post by tvars on 2008-11-18
I just tried compiling the latest alsa drivers. It didn't help.

alsa-driver-1.0.18a
alsa-lib-1.0.18
alsa-utils-1.0.18

Any other ideas?

---

### Post by alvincura on 2008-11-29
I have the same issue with the same board.  Very interested in a fix for this.  I purchased this motherboard specifically for the onboard SPDIF.  I tried an Creative SoundBlaster PCI Express X-FI Titanium, for which there were no kernel drivers.  Creative has a downloadable driver, which compiled fine, but didn't work with SPDIF.

I would prefer to use the onboard audio anyway, and so am interested in how this can be made to work.

---

### Post by tvars on 2008-11-29
I haven't been able to make this work. I'm using the 6 channel audio feeding into my hi-fi out for now. :(

---

### Post by PhilipCan on 2008-12-01
I have read several posts on this.  As far as I can tell, it simply isn't supported yet in ALSA.   I tried a patch someone posted but it just crashed ALSA on me. 

As far as HDMI vs External S/PDIF, this is an option in the bios but it won't do you any good if you can't select iec958 at all in ALSA.

---

### Post by scoot on 2008-12-04
What patch did you apply? I tried latest alsa stable and had no luck. I would REALLY like to get this working on my M2N68-VM as well. :)

---

### Post by viperxbr on 2009-01-17
I have the exact same problem with the same MB.  Mythbuntu 8.10 and alsa 1.0.18a drivers still no s/pdif output.

Anyone heard of any fix yet?

V.

---

### Post by DadAgain on 2009-01-19
Same drama with M3N78-VM... (onboard SPDIF & HDMI)

I had a pig of a time trying to get things to work (drivers for tuners, EPG problems etc etc) in vista/win7 so figured perhaps going back to MythTv for this build was the go since I knew the tuners were well supported and never had  the shpherd tv listing is justthe best (for Australia)... but if I cant get any sound I'm screwed and will have to go back to a window solution again... DOH!!

---

### Post by viperxbr on 2009-01-20
Interestingly the alsa sees the SPDIF port but sees it as an "Input" but not an "Output":

mythbuntu1:/proc/asound$ cat card0/codec#0
Codec: VIA VT1708B 8-Ch
Address: 0
Vendor Id: 0x1106e721
Subsystem Id: 0x10438345
Revision Id: 0x100100
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
.
.
.
Node 0x20 [Pin Complex] wcaps 0x400701: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x985601f0: [Fixed] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Power: setting=D0, actual=D0
  Connection: 1
     0x12
Node 0x21 [Pin Complex] wcaps 0x400601: Stereo Digital
  Pincap 0x00010030: IN OUT EAPD
  EAPD 0x2: EAPD
  Pin Default 0x47c421f0: [N/A] **SPDIF In at Ext Rear Panel**
    Conn = RCA, Color = Grey
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Power: setting=D0, actual=D0
.
.
.

Anyway to change this an "Out"?

V.

---

### Post by richardjones on 2009-01-20
I've just got one of these yesterday. Kicking myself for not searching for compatibility issues :(

There is a bug in Launchpad:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/298465](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/298465)

---

### Post by slick666 on 2009-01-27
I haven't gotten min working but I noticed the same thing. I have an Audigy LS and by default the digital IO port was configured to by an IEC958 input

What I had to do for mine is go into recording (Tab) and on the far right there is an option to change it (in my case) to many different things.

Right now everything appears to be setup. I have a TOSLink to fiber cable but I'm getting no light on the other end :(. All spdif Connection's I've had under linux (Including a laptop) lit up unmuted.

I hope this ti[p helps you all out.

---

### Post by nicoloks on 2009-02-03
Same issue on an Asus M3N78-VM board. I can get audio over HDMI using ALSA 1.0.19, but can't for the life of me get audio over SPDIF. As my DD5.1/DTS reciever only has SPDIF inputs I have a choice of either 6 channel analog sound or stereo PCM when hooking up the HDMI to my Plasma. Glad I found this thread though as I was about to put it down to some elusive config error and go back to Windows. Has anyone toyed around with the options in /etc/modprobe.d/alsa-base? I tried adding "options snd-hda-intel model=6stack-dig" after reading a few threads, but no go.

---

### Post by troipoison on 2009-02-19
[QUOTE=nicoloks;6669210]Same issue on an Asus M3N78-VM board. I can get audio over HDMI using ALSA 1.0.19, but can't for the life of me get audio over SPDIF. As my DD5.1/DTS reciever only has SPDIF inputs I have a choice of either 6 channel analog sound or stereo PCM when hooking up the HDMI to my Plasma. Glad I found this thread though as I was about to put it down to some elusive config error and go back to Windows. Has anyone toyed around with the options in /etc/modprobe.d/alsa-base? I tried adding "options snd-hda-intel model=6stack-dig" after reading a few threads, but no go.[/QUOTE

I was going through the exact same thing as you. Had it hooked up to my plasma via hdmi, but wanted the 5.1 out of my optical. (plasma won't pass 5.1 through the digital out.)
So after my update of alsa to 1.0.19 I tried forcing the front audio off on the bios so I could focus on the rear HD. All that gave me was hdmi 2 channel audio. This board can't send audio from the toslink and hdmi through linux (I had it on windows nicely.) My new remote will only work with vista... which ain't happening.

To get to it, I snipped an old 3pin wire that goes from cd/dvdrom audio to mobo. Pulled a toslink from an old dead dvd player (try an alley or salvation army or goto an electronics shop for an adapter.) The pin config on the mobo goes like this >     
                     _____
                          5volt
                     _____
                     _____data
                          gnd 
if that makes sense, the singled out pin is 5v and then data and ground are right next to each other. It's up by the last pci slot.I got the light on it right away, so I knew it was good to go, set the bios to read front audio HD. It still wasn't enough. Then I used the alsa update script again, but this time I did it -snap, and grabbed the latest snapshot. Set the audio switches to iec958 default pcm, and iec958 on. iec958 1 I just left off.

If not for the alsa update script, nvidia 180, and all the support and reading I've been over with confirmations of hdmi, I wouldn't have bothered to get spdif. HATS OFF TO THIS COMMUNITY!!!!:D

my first post.
(p.s. I also have the newest bios on there for the m3n78-vm)
Let me know if anything needs clarifying, like I say, first post. 3 years with linux. 
I can take pics if needed.

---

### Post by ElJefeRocks on 2009-02-26
I have the same problem.  My optical actually does show up as a device though, but its output is to null.  I think it doesn't know where the optical out hardware is so it dumps it and the signal is carried over the hdmi instead.  My aplay -L is below.  Also using the latest alsa-1.0.19 on an ASUS M3A78-T (ATI 790gx)

```

userver:~$ aplay -L
default:CARD=SB
    HDA ATI SB, ALC1200 Analog
    Default Audio Device
front:CARD=SB,DEV=0
    HDA ATI SB, ALC1200 Analog
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, ALC1200 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, ALC1200 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, ALC1200 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, ALC1200 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, ALC1200 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=SB,DEV=0
    HDA ATI SB, ALC1200 Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=HDMI
    Default Audio Device
hdmi:CARD=HDMI
    HDA ATI HDMI, ATI HDMI
    HDMI Audio Output
```

---

### Post by viperxbr on 2009-02-27
> **troipoison said:**
> [QUOTE=nicoloks;6669210]Same issue on an Asus M3N78-VM board. I can get audio over HDMI using ALSA 1.0.19, but can't for the life of me get audio over SPDIF. As my DD5.1/DTS reciever only has SPDIF inputs I have a choice of either 6 channel analog sound or stereo PCM when hooking up the HDMI to my Plasma. Glad I found this thread though as I was about to put it down to some elusive config error and go back to Windows. Has anyone toyed around with the options in /etc/modprobe.d/alsa-base? I tried adding "options snd-hda-intel model=6stack-dig" after reading a few threads, but no go.[/QUOTE

I was going through the exact same thing as you. Had it hooked up to my plasma via hdmi, but wanted the 5.1 out of my optical. (plasma won't pass 5.1 through the digital out.)
So after my update of alsa to 1.0.19 I tried forcing the front audio off on the bios so I could focus on the rear HD. All that gave me was hdmi 2 channel audio. This board can't send audio from the toslink and hdmi through linux (I had it on windows nicely.) My new remote will only work with vista... which ain't happening.

To get to it, I snipped an old 3pin wire that goes from cd/dvdrom audio to mobo. Pulled a toslink from an old dead dvd player (try an alley or salvation army or goto an electronics shop for an adapter.) The pin config on the mobo goes like this >     
                     _____
                          5volt
                     _____
                     _____data
                          gnd 
if that makes sense, the singled out pin is 5v and then data and ground are right next to each other. It's up by the last pci slot.I got the light on it right away, so I knew it was good to go, set the bios to read front audio HD. It still wasn't enough. Then I used the alsa update script again, but this time I did it -snap, and grabbed the latest snapshot. Set the audio switches to iec958 default pcm, and iec958 on. iec958 1 I just left off.

If not for the alsa update script, nvidia 180, and all the support and reading I've been over with confirmations of hdmi, I wouldn't have bothered to get spdif. HATS OFF TO THIS COMMUNITY!!!!:D

my first post.
(p.s. I also have the newest bios on there for the m3n78-vm)
Let me know if anything needs clarifying, like I say, first post. 3 years with linux. 
I can take pics if needed.

Should not have to do that.  With proper drivers, it should just work.  

I've got the latest snap of Alsa and see all the digital connections but I'm still unable to fire up that optical port.

Any other suggestions?

---

### Post by tvars on 2009-02-27
There's an bug on the alsa project for this issue. 

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4330](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4330)

---

### Post by viperxbr on 2009-02-28
> **tvars said:**
> There's an bug on the alsa project for this issue. 

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4330](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4330)

I know about the bug.  That's why I said I installed the latest snap (development snapshot) of the Alsa drivers/utils which recognize the digital port(s).

---

### Post by troipoison on 2009-03-01
Like I say I've got the latest snap of alsa too and it reads all the ports, but won't separate the digital audio on the back outputs.

If you have an HDMI cable plugged in, it won't send audio to the s/pdif on the rear, only HDMI. So I just added a front s/pdif, there's pins on the board for it, I just mounted it in the back. 

The junk driver/util that comes on the m3n78-vm cd won't work in windoze either. You need the newest version as well. Otherwise everytime you boot, you have to disable/enable the s/pdif in the util.

... upon mentioning that, I wonder if a disable/enable would light up the back s/pdif.

3 wires to make a front connection though.... not a lot of work. Since mine is going from this method, I'm not sure I'll be running anymore tests until possibly 6 months or so with a new snap of alsa.

---

### Post by qball4 on 2009-03-23
I've done everything you have, troipoison, but still can't get audio either over the back toslink or over the new module connected to the internal header. 

1. MB=Asus M3N78-VM
2. Latest ALSA snap
3. Soldered toslink module IN|5V|GND (pins facing down, port forward) to 4 pin cable to S/PDIF header 5V|NONE|OUT|GND
4. Tried both with and without 'options snd-hda-intel model=6stack-dig' in /etc/modprobe.d/alsa-base
5. BIOS set to Internal+External with Front HD
6. Un-muted IEC958 and IEC958 Default PCM

aplay -l shows:

```

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: NVidia [HDA NVidia], device 1: VT1708B Digital [VT1708B Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

aplay -L shows:

```

front:CARD=NVidia,DEV=0
    HDA NVidia, VT1708B Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, VT1708B Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, VT1708B Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, VT1708B Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, VT1708B Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, VT1708B Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
    HDA NVidia, VT1708B Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)

```

I'm stumped. :confused:  Do you see anything different from your config?

Thanks,
qball4

---

