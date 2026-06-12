---
title: "Dell Inspiron 9300, sound after 7.04 installation"
date: 2007-04-23
forum: Multimedia &amp; Video
---

### Post by Robert Leithe on 2007-04-23
I've been using 6.10 for a few months, and decided to install 7.04 as soon as it was released. After the installation I am experiencing trouble with my sound. I'll try to explain as detailed as possible what the trouble consist of:

- after the installation and first logon I was presented the sound for successful logon. However at an extremely loud volume setting. At the front of the Inspiron 9300 there are buttons that (amongst other things) control the main volume (it corresponds with the volume icon at my upper right corner). When I pressed the button for reducing the volume nothing happened. The on screen indication appeared and showed me that the main volume in fact was reduced, but I could not make out any reduction in the volume at which the welcome sound was played.

- when I watch video, either in VLC or inline in Firefox I experience the same thing. The media player's native volume control however (whether the media player at the time is VLC or an inline player) works for adjusting the volume.

- today, when I was watching a trailer online, I observed the following: the media player's native volume control and the main volume (whether adjusted from the icon or the buttons) appears to adjust their separate "sound track". Both sound tracks play exactly the same. The main volume has little effect on the output. The sound that is presented in the same manner as the logon sound mentioned earlier, is overwhelmingly present. And also of a lower quality than I am used to from 6.10.

I've been looking at System>Preferences>Sound, and this looks ok. I have tried various selections for playback, but have found no solution as of yet.
Have also right clicked the main volume icon and opened the Volume Control. Here I can see that Master is set at 50%, Headphone is set at 50%, PCM is set at 50% and CD is set at 50%. Line-in, Microphone and PC Speaker are all set to 0% and marked with a red cross at the bottom (muted). Have tried various volume levels for each different set of sliders, but have not found anything to make things "the way I want them to be".
From this window I can select the following two devices (File>Change Device):
- Intel ICH6 (Alsa mixer)
- SigmaTel STAC9750,51 (OSS mixer)

Any tips on how to solve this?

Sincerely

---

### Post by saydilip on 2007-04-25
I too have te same problem with my Inspiron 9300. The other things I noticed are

1) when I single click the volume icon on the system tray and reduce the volume(this is the master volume) all the way down, I could still hear the music.

2) When I press mute button in the front of my laptop, the master volume is muted, but the music is still heard.

3) The abouve two happen till I mute the PCM, which effetively measn that the mute key is useless.

4) Also the subwoofer in the system is also playing the regular music like another speaker. Guess its not configured properly.

Any help on addressign these issues are most welcome.

Dilip

---

### Post by leftyfb on 2007-04-26
System - Preferences - Sound
Default Mixer Tracks
Click "Master"
hold CTRL and click PCM
click close


The reason for this is the subwoofer in the 9300 is controlled differently(PCM?). So you need to select both Master and PCM to be controlled when changing the volume.

---

### Post by Robert Leithe on 2007-04-27
Excellent, thanks a lot! :)

---

### Post by saydilip on 2007-04-28
Thank you very much now the mute key works fine.. but the subwoofer control is not yet there.

---

### Post by firesyde424 on 2007-04-28
I'm having this problem as well with Hoary on an Inspiron 9300.  In Breezy, the front panel volume control worked for both the speakers and the subwoofer.  However, after an install of Hoary,  I did not have any volume control at all.  The front panel did not light or operate at all.  After an update to the ALSA drivers, the frontpanel worked, however the subwoofer control was not there.  The PCM slider will control it, but I dont know how to link the PCM slider to the front volume if that is even possible

---

