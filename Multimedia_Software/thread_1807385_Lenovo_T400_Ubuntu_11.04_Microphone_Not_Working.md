---
title: "Lenovo T400 Ubuntu 11.04 Microphone Not Working"
date: 2011-07-19
forum: Multimedia Software
---

### Post by Piscanerian on 2011-07-19
I have been trying to get my microphone to work on my Lenovo T400 for over a month now.  I installed Ubuntu 11.04 64bit ~2 months ago and the microphone worked once or twice in that time.  Albeit, I only tried it once or twice.  

FYI, my audio output works perfectly fine, just not input.  And, I've ensured that I am in the groups: audio, pulse, pulse-{other} and voice.

I have been in and out of, I think, every Ubuntu forum page talking about microphone issues; but nothing has worked yet.

-------------------------------------------------
I even tried the AlsaUpgradeScript.sh at [http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)

Apparently that was risky, but at least it didn't break anything.

-------------------------------------------------
I edited my "/etc/modprobe.d/alsa-base.conf" to use one of each of the following at some point or another:

options snd-hda-intel model=laptop
options snd-hda-intel model=laptop position_fix=1 enable=yes
options snd-hda-intel model=thinkpad
options snd-hda-intel model=thinkpad-t400
options snd-hda-intel model=lenovo
options snd-hda-intel model=lenovo-t400


-------------------------------------------------
I apologize if this is a repeat thread, but none of the other threads have solved my problems; even ones that seem to be identical to mine in nature.

Although I have tried a million things, I can't remember most of them and would like to start from the beginning.  Simple things like "is it muted" are also warrented, but I have checked and it is not muted in alsamixer, pavucontrol or gnome-alsamixer.

I am using a Conexant CX20561 (Hermosa), as per my /proc/asound/card0/codec#0; which is also attached as a txt file.

my alsa-info.sh output is stored at [http://www.alsa-project.org/db/?f=994cab34b9895ceb2c1e6eca726c6f72baf357d8](http://www.alsa-project.org/db/?f=994cab34b9895ceb2c1e6eca726c6f72baf357d8)

Also, alsa-info.sh |grep Version supplies:


!!DMI Information
!!---------------

Manufacturer:      LENOVO
Product Name:      2764CTO
Product Version:   ThinkPad T400


!!Kernel Information
!!------------------

--
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.24
Library version:    1.0.24.1
Utilities version:  1.0.24.2

and finally amixer reports:


Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 74
  Mono:
  Front Left: Playback 55 [74%] [-19.00dB] [on]
  Front Right: Playback 55 [74%] [-19.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Mic',0
  Capabilities: volume pswitch penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 80
  Front Left: 80 [100%] [6.00dB] Playback [on]
  Front Right: 80 [100%] [6.00dB] Playback [on]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 3
  Mono: Playback 0 [0%] [-18.00dB] [on]
Simple mixer control 'Docking Mic',0
  Capabilities: volume pswitch penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 80
  Front Left: 73 [91%] [-1.00dB] Playback [on]
  Front Right: 73 [91%] [-1.00dB] Playback [on]
Simple mixer control 'Internal Mic',0
  Capabilities: volume pswitch penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 80
  Front Left: 80 [100%] [6.00dB] Playback [on]
  Front Right: 80 [100%] [6.00dB] Playback [on]

I've also attached these three output streams as text files, but this is my first post, so I don't know how well that works.  Especially since the alsa-info.results.txt had to be compressed to upload.

I'm really hoping it's something simple and stupid that I'm missing.  

Please, any response is greatly appreciated.  Thank you just for reading this post :)

---

### Post by yhuang on 2011-09-16
I realized my microphone stopped working one day, after it worked for 3 months. I am also using ubuntu 11.04 (64bit) with Thinkpad T400.

Since then, I spent a great deal searching online for a solution. Never had a luck, though.

---

### Post by ExxonValdeez on 2011-10-02
I've been trying to figure out the same issue and have had no luck. I'm glad I ran across your post because I was about to try other options as well.

My microphone used to work in older versions of Ubuntu and in Arch Linux so I'm not sure if some update broke it.

Have you tried using an external microphone? I'm considering getting one if I can verify that it works.

---

### Post by QBX on 2011-12-31
I have the same issue with a T410 and Ubuntu 11.10 64 bit. I had mine work under 11.04 before. Internal mic does not work. An external one - connected to either bluetooth or the jack does, and the internal one does work under Windows (have a dual boot setup).

---

### Post by gamfarnham on 2012-03-07
Hi Guys. I'm new to this forum, but I throw in the following experience which may be helpful.

I have a Lenovo T400 with a ConexantCX20561 sound card. I am running Ubuntu 11.10

I installed "recordMyDesktop" and found that it worked well straight out of the box. However it was recording both the built in microphone and the sound on the video which I was playing. This is often not a problem, and deffinitely better than no sound at all.

I then installed GNOME ALSA Mixer which recognised the card. It shows 8 possible sources - Master, PCM, Mic, Beep, Docking, Internal, IEC958 and IEC958 Default PCM.

Clicking "Edit" "Sound card properties" brings up the list of 8. All boxes are ticked by default. Unticking any box, removes that item from the mixer display.

I have no external mic attached at this stage of my checking. The only sliders which have any effect on the sound output are PCM and Internal.

If you can't get sound, it may be worth trying GNOME ALSA Mixer, but ensure that all 8 input possibilities are switched on and the slider controls set to the top (or near top) positions.

Piscanerian sounded desperate so I hope this helps. The problem may be something completely different, so no guarantees given.

---

