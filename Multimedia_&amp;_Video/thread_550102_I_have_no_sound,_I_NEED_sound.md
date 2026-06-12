---
title: "I have no sound, I NEED sound"
date: 2007-09-13
forum: Multimedia &amp; Video
---

### Post by AstarothCY on 2007-09-13
Ubuntu cannot play any audio whatsoever. I never had any problems with audio, but yesterday while trying to install a USB wifi adapter amarok just started spewing noise mid-song, and anything I tried playing after that came out as noise (not just in Amarok). There was also a huge slowdown every time I tried to play audio. After a reboot, there was no sound at all, not even the Ubuntu startup sound. I booted into WinXP and the sound works fine so it's not my hardware. I don't even know where to begin fixing this because it's such an absurd problem.

I should say that I tried everything in [this thread]("http://ubuntuforums.org/showthread.php?t=205449") and it still doesn't work. I also tried logging in as a different user and it still doesn't work.

---

### Post by dabl on 2007-09-13
I'd start by removing and re-installing the ALSA packages -- it sounds like something went very wrong while Amarok was using the sound system.  There's also a "Master Sound Troubleshooting" thread somewhere on this forum that has material on all the commond sound chips.  :)

---

### Post by AstarothCY on 2007-09-13
Maybe you posted before i edited in that last line but I have followed the instructions in the sound troubleshooting thread and that included reinstalling all the alsa packages, still no luck.

---

### Post by dabl on 2007-09-13
Bummer .... :(

When you open the mixer (right click the speaker icon in the top right of your screen), if you "Edit">"Preferences", are all the little boxes checked?  And all the little mute lights unmuted, and sliders up from their lowered and locked positions?  I distinctly recall having to fiddle with that thing for quite a while when I first installed Ubuntu -- I think maybe "PCM" or "Front" was muted by default, and that turned out to be the channel that I needed.

---

### Post by AstarothCY on 2007-09-13
Yeah my mixer is fine, anyway it wouldn't be anything like that considering what happened with Amarok just playing noise and stuff.

---

### Post by AstarothCY on 2007-09-14
bump

---

### Post by Robbyx on 2007-09-15
I too had no sound till just now. I changed the device from ALSA to OSS mixer. I wonder if I am loosing out not being able to use ALSA.

---

### Post by AstarothCY on 2007-09-16
> **Robbyx said:**
> I too had no sound till just now. I changed the device from ALSA to OSS mixer. I wonder if I am loosing out not being able to use ALSA.

Did you have anything similar to my problem, i.e. with a breakdown of sound in Amarok? Or did you just never have sound?

---

### Post by Robbyx on 2007-09-17
> **AstarothCY said:**
> Did you have anything similar to my problem, i.e. with a breakdown of sound in Amarok? Or did you just never have sound?

I had sound and then it stopped after I used hibernate. I now have ALSA working as well. I followed the advice in the 'Comprehensive Sound problem solutions guide' that part dealing with 'getting alsa drivers from fresh kernel'  If you follow the advice in that  section make sure you also implement the very important reinstallation of the gdm and desktop, before rebooting.

Robin

---

### Post by tmenness on 2007-09-18
I had the same problem yesterday. I was running Amarok, hibernate, log back in and no sound. I followed the instructions you mention, including reinstalling asla, no luck.

Reading this thread, it actually seems to be a problem with Amarok... no clue really.

Help appreciated,

---

### Post by AstarothCY on 2007-09-18
In the millions of threads I've read about sound problems, I remember reading something about Amarok messing with global sound settings.. I will try reinstalling it when I get home from work.

---

### Post by Robbyx on 2007-09-18
I do not use amorak. Why not choose another application. I use SMPlayer and xmms.

R

---

### Post by AstarothCY on 2007-09-18
Uh, doesn't matter anyway, it didn't help.

I have reinstalled pretty much everything.. alsa and every remotely relevant package, gstreamer, the whole kernel ffs... I am completely at a loss. Anyone? Please?

---

### Post by Robbyx on 2007-09-18
Have you tested for sound in the system -preferences - sound Ubuntu main menu option?

Also try the OSS sound protocol and see if you hear anything through that.

R

---

### Post by AstarothCY on 2007-09-18
tried that, nothing

---

### Post by AstarothCY on 2007-09-19
bump

---

### Post by loserboy on 2007-09-19
do you have another kernel to fall back on to see if that makes a difference

---

### Post by AstarothCY on 2007-09-19
Nope, tried several kernels, all have no sound.

---

### Post by AstarothCY on 2007-09-21
I have checked for IRQ conflicts, there are none.

---

### Post by deadgobby on 2007-09-21
Try this thread and see if it helps.
[http://ubuntuforums.org/showthread.php?t=41](http://ubuntuforums.org/showthread.php?t=41)
Gobby

---

### Post by AstarothCY on 2007-09-21
*sigh*

---

### Post by tmenness on 2007-09-29
sudo aptitude install alsa-oss

...solved my problem, which I strongly suspect was related to Amarok messing up with alsa.

check this out:
[http://www.oreillynet.com/onlamp/blog/2006/07/audio_problem_from_flash_video.html](http://www.oreillynet.com/onlamp/blog/2006/07/audio_problem_from_flash_video.html)

Hope it helps,

---

### Post by AstarothCY on 2007-11-04
SOLVED


1. Open the volume control app
2. Edit -> Preferences
3. Check "Surround" and "Audigy Analog/Digital Output Jack"
4. Increase the volume for the Surround channel.
5. Go to the Switches tab and untick the "Audigy Analog/Digital Output Jack" box.
6. Wonder why the hell Ubuntu sound architecture is so useless.
7. The end.

---

### Post by hockey97 on 2007-11-04
my sound works somtimes it's odd.

it's random some day's it will work perfectly and then other day's I get no sound at all.

I am using sound blaster surround sound.

---

### Post by Attila2452 on 2007-11-04
i have a sorta similar problem! 

i have sound but its verry low and distorted. my speakers, and volume on my computer are FULL but its verry low i have tried changing options but it does nothing.

see i am using dual companies (XP and Ubuntu) but my sound WORKS on XP and XP only its just Ubuntu that its not working properly on! 


 - Attila Hajzer -

---

### Post by AstarothCY on 2007-11-04
Have you looked at [this thread](http://ubuntuforums.org/showthread.php?t=205449)?

---

