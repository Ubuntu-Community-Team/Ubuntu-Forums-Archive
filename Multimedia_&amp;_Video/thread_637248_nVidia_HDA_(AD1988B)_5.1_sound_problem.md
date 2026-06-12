---
title: "nVidia HDA (AD1988B) 5.1 sound problem"
date: 2007-12-10
forum: Multimedia &amp; Video
---

### Post by Weider on 2007-12-10
Two days of thorough search ended with absolutely nothing, so this is my last chance...

I have Asus Striker Extreme motherboard with fabric BIOS and revesion 1.03A. By different test tools I've got the main idea of what sound card I'm dealing with - classic AD1988B sound codec chipset, integrated on MCP55 nVidia north bridge (i680SLi)

So...

1. Sound [COLOR="Red"]WORKS[/COLOR]. Out of the box. Perfectly fine. With no glitches at all, etc.
2. By enabling in alsamixer-gui the corresponding channels - SURROUND, CENTER, LFE - I've got sound from all 6 speakers (I'am using oldschool Creative Inspire 5300 =))), including mp3, system sounds, etc.
3. BUT there is nothing I can do to hear native pure 5.1 channel surround sound in films, ac-3 mixes, DVD, HD. It is still a stereo from 5 speakers and hard groul from the sub =/

Alsmixer-gui suggests two sound cards - HDA nVidia (alsa mixer) & Analog Devices AS1988B (OSS mixer). But changing have no effect at all

speaker-test -Dplug:surround51 -c6 -twav works perfectly fine, giving nice woman voice in right channels

Officially ALSA do not have driver for AD1988B, but how does then surround and everything else work?

Running on Unutu 7.10, kernel is standart, 2.6.22-14, no modifications made



I'll really appriciate any help or brilliant ideas  for there are too few users of i680 SLi chipsets, espessialy under Linux... :confused:

Thanks in advance!

---

### Post by Weider on 2007-12-11
Suddenly, I've found the way to hear 5.1 surround sound in MPlayer, by starting it from concole with lots of parameters:

**gmplayer  -af channels=6:6:0:0:1:1:2:2:3:3:4:4:5:5 -channels 6 -quiet -nofs -delay -0.6  -aspect 4:3 <path_to_film>**

As a workaround it works fine, not w/o glitches, but... just fine. Still problem resides and I'm willing to get to the end. May be someone knows that this situation is just normal and nothing to worry about - and all you've to do take is to take a deep breath and wait for another release of ALSA...

---

