---
title: "Comprehensive Sound Problem 7.04"
date: 2007-06-28
forum: Multimedia &amp; Video
---

### Post by pablo88 on 2007-06-28
Hi -

I recently posted elsewhere ([http://ubuntuforums.org/showthread.php?t=484704](http://ubuntuforums.org/showthread.php?t=484704)) regarding a "No Sound" problem with Feisty on a laptop. Frustrated (not by the lack of help but by the lack of tangible results) I have started anew, and re-installed Feisty on the 80Gb Toshiba internal drive of the laptop. Prior to the install, I ran feisty off the CD - no sound was available then. Video played, but no sound.

Before I tinker with anything, I need to get the sound working. My lspci shows:

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05)
01:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
01:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

I guess this is the key line:

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)

Prior to this install, I had 7.04 installed on the laptop and the PLAYING of sound worked, but not the recording of sound. For podcast reasons I need to record. This is why I attempted (lol) to get the audio working fully. Yeah right.

I followed the instructions at:   [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)   as far as the last bit where I got stuck on the bit "Manually specify which model you are using". The laptopp has a Realtek ALC880 as shown when I enter:   cat /proc/asound/card0/codec\#*   producing -

Codec: Motorola Si3054
Address: 0
Vendor Id: 0x10573055
Subsystem Id: 0x10573055
Revision Id: 0x100700
Codec: Realtek ALC880
Address: 1
Vendor Id: 0x10ec0880
Subsystem Id: 0x8800000
Revision Id: 0x100800

When I read through ALSA-Configuration.txt, there is a multitude of models to choose from and I haven't a clue which one I should use. Any answers?

I'm seeking to provide as much info as poss. I've been at this for 5 days now and am desperate for a working solution. Any assistance given much appreciated.

-- Pablo

---

### Post by renzokuken on 2007-06-28
most Realtek chipset issues are solved by updating the alsa-driver.  thats how i got my ALC chip working

go to [www.alsa-project.org](www.alsa-project.org) and download the latest **alsa-driver** to your home folder. i think the current version is 1.0.14

then open a terminal and run the following commands to compile it from source

```

sudo apt-get install build-essential
tar xjf alsa*
cd alsa*
./configure
make
sudo make install

```

reboot and see if it works

---

### Post by pablo88 on 2007-06-28
Hi renzokuken -

Followed your instructions. All went well, but still no sound.

At the end of the "make install" process, this came up in the terminal.

> /sbin/depmod -a 2.6.20-16-generic 
cat WARNING

WARNING!!! The mixer channels for the ALSA driver are muted by default!!!
**************************************************************************
You would use some ALSA or OSS mixer to set the appropriate volume.


How do I unmute the mixer channels?

-- Pablo

---

### Post by renzokuken on 2007-06-28
open a terminal and type

```
alsamixer
```

the just use left and right to select channels, prees "m" to toggle mute/unmute and up and down arrow keys to raise/lower volume

---

### Post by pablo88 on 2007-06-28
Ok, entered "alsamixer" into the terminal, brought up the alsamixer v1.0.13

Turned every channel I could find up to FULL, rebooted and still, Nothing.

Ai caramba, this is enough to make me go back to windows.

Apologies - no need for foul language I know. Hmmmmmmmmmmm.

-- Pablo

---

### Post by pablo88 on 2007-06-28
Oh joy - the MUTE button thing was the missing key. Incredible joy and happiness abound. Muchos gracias for your help. 5 days of silence are over.

:popcorn:

:D

---

### Post by pablo88 on 2007-06-28
But one further thing, I still cannot record using Audacity. Any suggestions?  Great to have the sound back, but what would I need to do to enable recording to work too?

-- Pablo

---

### Post by renzokuken on 2007-06-28
did you turn up/unmute all the channels in the "capture" section of alsamixer?

use the tab key to move between "playback, "capture" and "all"

---

### Post by mohnkern on 2007-06-28
I've been having a similar problem.

A bit about my configuration:

Two sound outputs on machine --- Onboard audio (disabled in Bios) and SBLive Value edition:

Relevant portion of lspci:

00:0d.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
00:0d.1 Input device controller: Creative Labs SB Live! Game Port (rev 08)
[snip]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 A
C97 Audio Controller (rev 60)


I run alsamixer, and everything is turned up on the SBlive, and mute is definitely not on.  (I show OO's not MM's under everything, except "TONE")

If I turn Tone on, I get a hum out of the speakers, so I know it's accessing the card.

But every application has no sound, including Gnome and KDE.  It's like it's pumping the sound out somewhere else.  and its not the onboard audio, because I plug it in, and there's nothing there.

Is there just some way to tell Ubuntu to use a specific device for all audio?

I've been going through this problem for over a month.

---

### Post by alexm0428 on 2007-06-28
Hi.

I have exactly the same problem:

WARNING!!! The mixer channels for the ALSA driver are muted by default!!!
************************************************** ************************
You would use some ALSA or OSS mixer to set the appropriate volume.

I moved up all the alsamixer controls and try with the m inall of them and still nothing.

I really want some help because I want to migrate form WXP to linux, but without sound its inconfortable.

My card is a Intel ICH5 with chipset "Analog Divices AD1985" -- that was wath alsamixer said.

thanks

PD: I have the Ubuntu feisty 7

---

### Post by pablo88 on 2007-06-28
Yes, I did turn up and unmute all the capture channels. Capture shows 4 channels. The first one is labelled IEC958 followed by 3 Capture channels - Capture, Capture 1 and Capture 2. The ability to mute or unmute these channels doesn't seem to exist although I have all the Capture channels turned right up.

---

### Post by dunkirk57 on 2007-06-28
Yeah, 'alsamixer' saved my sanity here, as well!!!:D I'm using a Lenovo Stinkpad Z61t (it's actually a very nice computer) running Ubuntu Desktop 6.10, and I ran an upgrade this morning only to find my sound quit working!!! (I couldn't listen to tunes and do my work!) It really bugged me, and I'm glad the solution was so easy. (I'm also glad I found this thread before I went a butchering, too!)

...Dunkirk57

---

### Post by mohnkern on 2007-06-28
To add to the "strangeness"

If I open up Kmix, and go to the Sblive card, and turn on the "tone" option, I get the tone, so its definitely seeing the card, and accessing it.

I just can't get any applications, or the desktop to put sound out it (i've used gnome, and KDE, to no avail).

I've tried plugging into every sound port on the box, and nothing.

I've also removed alsa with the --purge, and reinstalled it.

Well, there we go for more weirdness.  My USB headset that wasn't working, now is getting KDE system sounds.  But Amarok isn't playing through the USB headset, or anywhere else.

So, what we've got is:

USB headset working, with KDE system sounds.

SBlive isn't being used by KDE.

Applications (with the exception of KDE) don't seem to be piping sound anywhere useful.

It's like this moving target

---

### Post by mike2008 on 2008-04-01
hey,
I tried everything you wrote here and still nothing. I also unmuted everyth in alsamixer. I chose the ALSA 0.9.7 output plugin in Beep Media Player and also at the sound preferences
I hear a strange background noise 
Tnx

---

