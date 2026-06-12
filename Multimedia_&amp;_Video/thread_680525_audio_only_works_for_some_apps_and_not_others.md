---
title: "audio only works for some apps and not others"
date: 2008-01-28
forum: Multimedia &amp; Video
---

### Post by uncr347ivenam3 on 2008-01-28
**First here's the problem:**
I can get sound to work in some of the programs I run like rhythmbox and totem movie player all the time however in some programs like Hydrogen and VLC, the audio only works sometimes and when it doesn't work, sometimes I can get it working by changing the OSS audio device between */dev/audio* and */dev/audio1*.  I can live with having to change the audio device although an automatic solution would be nice.  The problem is the audio doesn't work for flash and java content online and for other programs like amarok and wine.  when I go into the *system>preferences>sound menu*, I switched all the audio devices to *ADC Capture/Standard PCM Playback* and when I pressed the test button, they all made sound.  any suggestions on how to get the problem fixed are appriciated.


**here's the system specs (from lspci, etc**
```
lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:05.0 Mass storage controller: Promise Technology, Inc. PDC20268 (Ultra100 TX2) (rev 02)
00:07.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
00:07.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev a1)
```

```
lsusb
Bus 004 Device 005: ID 13b1:0020 Linksys 
Bus 004 Device 003: ID 0409:005a NEC Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

```

```
uname -a
Linux zaphod 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux
```

I have 512 MB DDR memory, AMD Athlon XP 2200+ proc, a CD/DVD drive and 4 harddrives

To the best of my knowlege, most to all of the programs I have installed are up-to-date and I'm running gusty

Thanks for your help

---

### Post by uncr347ivenam3 on 2008-04-03
OK, I got it figured it out.  I needed to run [_alsamixer_]("http://en.wikipedia.org/wiki/Alsamixer") (from terminal) and unmute all the audio out items by pressing "m" while the correct columns are selected (the ones with the "MM" under them) and make them louder. 

[IMG]http://upload.wikimedia.org/wikipedia/commons/8/86/Alsamixer.png[/IMG]
(from Wikipedia)

[Edit]Hooray for [_FreeGeek_]("http://freegeek.org/") where I found out the fix[/Edit]

---

