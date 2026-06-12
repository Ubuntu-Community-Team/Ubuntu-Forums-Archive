---
title: "[SOLVED] AC3 5.1 Audio"
date: 2008-09-28
forum: Mythbuntu
---

### Post by Just4Fun20 on 2008-09-28
If this is posted somewhere I appreciate a link.  

I have a home theater with (5.1) surround sound.  My understanding is that this requires AC3 audio which may be stereo and which may be 5.1.  

Recently there was a post with a link to a test_ac3 v2.0 file.  This file "talks" out of each of the speakers.  It appears my surround sound is not working properly.  

What specific capacity, on my motherboard or sound card, is needed to enable or support AC3 and/or 5.1 audio?  I'm currently using the onboard audio chipset.  It connects through a stereo 1/8 inch jack (or so) which splits out into standard Right + Left RCA jacks.  

I believe SPDIF is digital, fiber audio, right?  If so, I don't have that capability.  

Assuming the mother board setup is ok (Do I need to know the MoBo HW, how do I check it?  BIOS?  MoBo specs?  Is there a Linux/Ubuntu command I should run?).  So, assuming the HW is capable that leaves the audio setup.  There are a lot of options.  

Under "Audio output device:" there is:  NULL, JACK:output, ALSA:default, ALSA:spdif, ALSA:surround51, ALSA:analog, ALSA:digital, ALSA:mixed-analog, ALSA:mixed-digital, /dev/dsp, /dev/adsp, ARTS:, 

Under "Passthrough output device:" there is:  ALSA:iec958:{ AES0 0x02 }, Default, 

Under Max Audio Channels: I have it set for 5.1 and Upmix set to Passive.  

There are also options on whether or not to "Enable AC3 to SPDIF passthrough", "Enable DTS to SPDIF passthrough", "Aggressive Sound card Buffer", and "Use Internal volume control".  

Only the internal sound control is selected.  

Thank you for any assistance.

---

### Post by mindoms on 2008-09-28
how exactly home theater system connected to the soundcard?
3 stereo jacks, green/black/orange or just one cable

a very basic way to test the setup is:
```
speaker-test -c 6 -D plug:surround51 -t wav
```

make sure no mixer-lane is muted or at a low level
You might need to make some visible with Edit->preferences in gnome-Volume-control

to identify the soundcard:
please run
```
lspci
``` and post the output

Also, it might be good to know what home-theatre setup you have

---

### Post by volkswagner on 2008-09-29
You can start by posting the output of the following

```
lspci
```

and 

```
aplay -L
```

Yes, you can't get 5.1 sound from your 1/8" jack.  What inputs are available on your receiver?

SPDIF can be fiber optic or coaxial (copper), you will need to see what your home theater has available.

---

### Post by Just4Fun20 on 2008-09-29
My MythTV Audio is connected to the receiver via the stereo port on the back of the computer.  This uses an 1/8" jack and the other end has standard RCA Red and Black connectors which connect to the receiver.  

My receiver is a Yamaha HTR-5250.  It has fiber connections which I use for my DVD player.  It's a little older but works well and is capable.  

I was playing with settings last night and think I gained on it.  

Thank you very much for your help.  

Here is the requested output:
```

MythBuntu:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:09.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
00:0a.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)
MythBuntu:~$

```

```

MythBuntu:~$ aplay -L
default:CARD=V8237
    VIA 8237, VIA 8237
    Default Audio Device
front:CARD=V8237,DEV=0
    VIA 8237, VIA 8237
    Front speakers
surround40:CARD=V8237,DEV=0
    VIA 8237, VIA 8237
    4.0 Surround output to Front and Rear speakers
surround41:CARD=V8237,DEV=0
    VIA 8237, VIA 8237
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=V8237,DEV=0
    VIA 8237, VIA 8237
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=V8237,DEV=0
    VIA 8237, VIA 8237
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
iec958:CARD=V8237,DEV=0
    VIA 8237, VIA 8237
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
MythBuntu:~$
```

---

### Post by volkswagner on 2008-09-29
I see you card has spdif out.  You will need to physically check if it is coaxial or fiber.  This will give you a multichannel connection to your amp.

run to get the card and device number for the spdif.

```
aplay -l
``` lower case "l" ell 

You can then follow the mythtv instructions for spdif passthrough.

[http://www.mythtv.org/wiki/index.php/Configuring_Digital_Sound_with_AC3_and_SPDIF]("http://www.mythtv.org/wiki/index.php/Configuring_Digital_Sound_with_AC3_and_SPDIF")

---

### Post by Just4Fun20 on 2008-09-30
> **volkswagner said:**
> I see you card has spdif out.  You will need to physically check if it is coaxial or fiber.  This will give you a multichannel connection to your amp.

run to get the card and device number for the spdif.

```
aplay -l
``` lower case "l" ell 

You can then follow the mythtv instructions for spdif passthrough.

[http://www.mythtv.org/wiki/index.php/Configuring_Digital_Sound_with_AC3_and_SPDIF]("http://www.mythtv.org/wiki/index.php/Configuring_Digital_Sound_with_AC3_and_SPDIF")

Excellent.  I did a bit of research, after searching the back of my machine.  It's older.  This whole MythTV project started as an experiment (to replace my TiVo).  I used some older equipment I had laying around.  The MoBo is a Biostar P4M80-M4 with (I think) a 2.4Ghz Pentium Celeron.  Overall it's a bit slow for anything but basic video.  

I couldn't find any other connectors so I pulled out the manual.  There is an SPDIF header on the MoBo but I need an SPDIF Bracket.  I might be able to buy one for $15-20.  Note the might since they're a little hard to find.  I could also probably make one although it would be coax.  Coax appears to be a standard RCA connector.  

Since audio is fairly important to me I'll keep playing with this and update a bit later when I've either built or bought a suitable bracket.   

Thanks for your help.

---

### Post by Just4Fun20 on 2008-10-18
I'm about ready to give up on this.  Perhaps 8.10 will see changes.  

I ordered the necessary part from Biostar and it can only be connected one way.  After installation I tried it and got nothing.  It is not "glowing red".  I looked in BIOS and there are no settings there.  There are no relevant jumpers on the MoBo.  

I wrote Biostar and they said I needed to run the Realtek Utility.  I can't find any such utility for Linux.  The Driver is built into the kernel.  Perhaps there is a command line switch???

Anyone have any luck with this?  Any suggestions?  It would be nice to have.  

According to the manual the sound chip/codec is the REALTEK ALC655.  It appears this is contained on the "Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)"

TIA

---

### Post by larsolav on 2008-10-20
Does the "iec958" bar show up in alsamixer at all? I have an intel sound chip, and I had to fiddle around a bit just to get the spdif it to be seen by alsamixer.
Good luck, hope you get it fixed!

---

### Post by Just4Fun20 on 2008-10-23
> **larsolav said:**
> Does the "iec958" bar show up in alsamixer at all? I have an intel sound chip, and I had to fiddle around a bit just to get the spdif it to be seen by alsamixer.
Good luck, hope you get it fixed!

This is mostly fixed.  Thank you.  

I had some problems with the alsamixer.  Possibly unrelated.  It ran but was causing my fiber output to shut down.  

I had more luck with the Volume Control.  (Go to the MythBuntu desktop, right mouse button on the menu bar across the top and add an icon for the Volume Control - as described in the post for low sound volume).  Open the Volume Control application.

On the Volume Control there is an item called "Hide Switches".  By clicking that there is a set of 8 buttons (in my case) and 6 other controls that appear.  One of those "buttons" was for IEC958 Output.  By enabling this I was able to get my fiber hookup to "glow red" and run some tests on it using the link for the MythTV SPDIF passthru instructions, which were very good ([http://www.mythtv.org/wiki/index.php..._AC3_and_SPDIF](http://www.mythtv.org/wiki/index.php..._AC3_and_SPDIF)).

I'm having some problems with my subwoofer, only from within MythBuntu, but I'll post a new thread on that and probably wait until after 8.10 comes out in a week, or so.  

Thanks again.

---

