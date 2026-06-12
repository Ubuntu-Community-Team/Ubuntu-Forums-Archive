---
title: "no sound alc889"
date: 2011-04-10
forum: Multimedia Software
---

### Post by DanBender on 2011-04-10
Hi! I'm currently having the issue of no sound in any programs. I've just installed Mythbuntu 10.10 64-bit onto a new motherboard (MSI NF750-G55). This has an integrated NVidia High-Definition Audio controller (based on Realtek ALC889). It works in Windows, but not in Linux; though I had to go out of my way to get it to work in Windows as well.

I've followed the instructions detailed here: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) up to the point of the```
sudo modprobe snd-hda-intel
```(I used that snd- entry because that was in the output of one of the earlier steps). However, there was no obvious results for the modprobe, only the next command prompt. And still no sound.

I thought I saw on another thread that someone had some success with the ALC889 by using a sound preferences utility, but I can't find any obvious sound utilities in the Mythbuntu menus (uses XFCE desktop). The closest thing I can find is Mixer, which just seems to be volume controls, and doesn't seem to have anything to identify what sound drivers are loaded, or if they are loaded. It does correctly identify my sound device as "HDA NVidia (ALSA mixer)" in the drop-down box as a choice, though. There's another choice in the "Applications->Multimedia" menu called "aumix," which might be something like I want, but that just flashes a window onto the screen real quick and disappears.

Anyone have any hunches here? Thanks in advance.

---

### Post by DanBender on 2011-04-12
I was able to enable sound using by following the instructions on [this wiki page.]("https://help.ubuntu.com/community/HdaIntelSoundHowto") I added the line ```
options snd-hda-intel model=6stick-dig
```into /etc/modprobe.d/alsa-base.conf. Once I did that and restarted I was able to hear sound from the speakers.

HOWEVER

it was very faint! I turned all the volume controls in Applications>Multimedia>Mixer to 100%, and did the same to the volume in Mythfrontend, and I still needed to turn the volume on my amp from -45dB (what is normally used for all my other components) to -35dB (which would normally put your eardrums out) to get an acceptable volume. I might be able to adjust the settings on my amp for that input to up its volume, but if there are any other options in Mythbuntu to increase the output volume, I'd like to know about it. It's always been a little quiet from Windows as well, but not this extreme.

---

