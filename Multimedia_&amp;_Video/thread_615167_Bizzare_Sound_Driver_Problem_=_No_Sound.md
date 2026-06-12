---
title: "Bizzare Sound Driver Problem = No Sound"
date: 2007-11-16
forum: Multimedia &amp; Video
---

### Post by RSVampire on 2007-11-16
Hey guys,
for some reason my sound randomly disappears and then randomly reappears whenever I log in/out of Ubuntu Gutsy. I have a Sound Blaster card and as of this second it's not giving any sound output. Can anybody explain to me why it works one day, then not the next, then randomly works again?

here are some command print outs.
> rsvampire@rsvampire:~$ lspci -i
lspci: option requires an argument -- i
Usage: lspci [<switches>]

-v              Be verbose
-n              Show numeric ID's
-nn             Show both textual and numeric ID's (names & numbers)
-b              Bus-centric view (PCI addresses and IRQ's instead of those seen by the CPU)
-x              Show hex-dump of the standard portion of config space
-xxx            Show hex-dump of the whole config space (dangerous; root only)
-xxxx           Show hex-dump of the 4096-byte extended config space (root only)
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]   Show only devices in selected slots
-d [<vendor>]:[<device>]        Show only selected devices
-t              Show bus tree
-m              Produce machine-readable output
-i <file>       Use specified ID database instead of /usr/share/misc/pci.ids.gz
-D              Always show domain numbers
-M              Enable `bus mapping' mode (dangerous; root only)
-P <dir>        Use specified directory instead of /proc/bus/pci
-F <file>       Read configuration data from given file
-G              Enable PCI access debugging
rsvampire@rsvampire:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge (rev 01)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0a.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
00:0d.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
00:0d.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
00:0d.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV40 [GeForce 6800 XT] (rev a1)
rsvampire@rsvampire:~$ clear

rsvampire@rsvampire:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge (rev 01)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0a.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
00:0d.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
00:0d.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
00:0d.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV40 [GeForce 6800 XT] (rev a1)
rsvampire@rsvampire:~$ 

---

### Post by RSVampire on 2007-11-17
anybody? 

I'd appreciate any kind of help on this matter...

---

### Post by RSVampire on 2007-11-19
please guys... need some help here... I understand everybody is busy. I've already run through the Sound post on how to fix your sound by reinstalling the ALSA drivers... and it still only randomly works.

---

### Post by gashcr on 2007-11-20
OK, now we are two with the same problem here, I'd appreciate some help too---

---

### Post by kag on 2007-11-20
Make it three. lspci lists it as "01:09.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 06)"

It was doing this sometimes with Feisty and now with Gusty.

EDIT: followed this guide and it seems to have fixed my problem. I guess I'll only be able to tell for sure in a few days...
[http://ubuntuforums.org/showthread.php?t=601433&highlight=sound](http://ubuntuforums.org/showthread.php?t=601433&highlight=sound)

---

### Post by RSVampire on 2007-11-22
this seems to have fixed my problem as well.

I'll keep tabs for a couple days like you and see how it goes.

---

### Post by bladednuisance on 2007-11-22
when logging in/out are changing users? I had this problem awhile back, its in the user permissions, by default only the administrative account has permission to audio plyback. Log in as your admin., got system,administration,users and groups, select the user, then enable audiio devices (check the box), for all users. This method applies to a few other usefull permissions

---

### Post by RSVampire on 2007-11-26
well my sound is working fine now these days... the only problem I have now with this method is sometimes my soundcard(s) swap slots between 0 and 1 depending on the IRQ ratings...

strange...

---

### Post by RSVampire on 2007-11-27
so how do I choose an audio device from it's name or it's driver from startup?

because I can get sound now whenever it randomly turns off, but it's randomly turning off because the default slot keeps changing back and forth between the integrated audio and the sound blaster card based on the IRQ.

So if I tell it to default to slot 0 in 2 days my sound card will move to slot 1 then I have to re-edit the file and restart the computer... I'd rather tell it "default soundcard.driver.xxx" rather than "default IRQ slot x" so it can dynamically change when the system changes.

can anybody help me with that?

---

### Post by RSVampire on 2007-11-29
I think I found the answer to my problem here... 

[http://ubuntuforums.org/showthread.php?t=546793&highlight=sound](http://ubuntuforums.org/showthread.php?t=546793&highlight=sound)

---

