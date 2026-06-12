---
title: "Ubuntu Breezy No Sound on Audigy Sound Card"
date: 2005-10-13
forum: Multimedia &amp; Video
---

### Post by atomicrod on 2005-10-13
I just did an install of Ubuntu Breezy and am unable to get the sound to work on the computer.

System is the following
Amd 2000 XP
Soyo Dragon Plus MOBO
Soundblaster Audigy

Results of lspci command for the sound card are:
lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
0000:00:0c.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
0000:00:0c.1 Input device controller: Creative Labs SB Audigy MIDI/Game port (rev 03)
0000:00:0c.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port

I checked the master volume and it is at 100 percent.

I'm new to troubleshooting Linux problems so any help is appriciated. I am not sure which log files to check. The Alsa Mixer does start on boot.

I've had a Debian system and Ubuntu Horary and had no problems getting sound to work.

I also attempted to play a music cd, the drive mounts the cd normally and it gets the track informaion and appears to be playing it but I have no sound.

I also checked the pcm volume and made sure it is turned up and not muted.  I know the speakers/sound card work properly because this is a dual boot system and they are ok in Windows

Any help is appriciated.

---

### Post by ggore on 2005-10-13
I'm having the same problem, installed Breezy this morning and no sound on my Audigy2 card.  Everything seems to be normal and recognized.  Sound worked on the old version of Ubuntu.

---

### Post by atomicrod on 2005-10-13
I've had some success.  I ran alsamixer and noticed an option for Audigy Analog/digital output jack.  I toggled this to off.  I thought that would actually be shutting that off altogether, however it appears that if you turn digital off it goes to analog.  Once I did that, the sound began to work.  

I realize most will no doubt laugh, but I'm pleased its working

Hope this helps anyone else having a problem.

I still do not have sound in the CD Player, however I do in rythmbox so I'll keep working.

---

### Post by ggore on 2005-10-13
That solution didn't work for me, I still have no sound.

---

### Post by Widdershins on 2005-10-13
I had the same problem with my Audigy soundcard.  I googled around and none of the suggested fixes worked...ie, toggling alsamixer's digital output jack setting.  I solved it by installing 5.04 and doing an apt-get dist-upgrade (make sure you do the apt-get update before dist-upgrade) after changing all hoary references to breezy.  Now, I know there should be an easier way to accomplish all of this, but I am at a loss as to what it might be.  I don't know what the differences between alsa drivers/settings are either.  I hope you can get your sound card working with a fresh install of breezy.

Setup:
AMD Athlon XP 2500+ (3200+)
1GB Buffalo DDR 3700 DDR @ 400MHZ 
ATI Radeon 9800 Pro
Soundblaster Audigy

---

### Post by bionnaki on 2005-10-14
I also cannot get my audigy 2 card to work with my fresh install of breezy. I used to use this guide: [http://ubuntuforums.org/showthread.php?t=21211](http://ubuntuforums.org/showthread.php?t=21211) & always had success. any ideas?

---

### Post by Spif on 2005-10-14
Setting Audigy 2 as my default sound card under Sound Preferences did the job for me.

---

### Post by bionnaki on 2005-10-14
nothing is listed for me.

---

### Post by ggore on 2005-10-14
The Audigy card is already selected as the default soundcard, no other option is given.  I have checked and unchecked the Digital/Analog box on sound configuration as well, and that didn't work either.  I am baffled since soud worked perfectly under Hoary.

---

### Post by eightysix on 2005-10-15
I can't get my Audigy LS soundcard to work either, but see if downloading this program helps:

```
sudo apt-get gnome-alsamixer
```

When I run gnome-alsamixer, my on-board sound from my motherboard shows up, but not my Audigy LS. Anyone have a work around for this yet?

---

