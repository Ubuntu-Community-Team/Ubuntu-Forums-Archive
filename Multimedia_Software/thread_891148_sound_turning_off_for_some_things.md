---
title: "sound turning off for some things"
date: 2008-08-15
forum: Multimedia Software
---

### Post by zapree on 2008-08-15
ok so sound works and its good quality but....  If the first thing that i play with sound is a mp3 track on rythmbox for exaple, then i cant watch a online video (youtube, veoh, ext.) and visa versa. so if i want to watch a video online and i have been listening to music i have to restart the computer and then it works, but i cant go back to listening to music afterwards and have to restart the computer again.
thanks for your help
Patrick


using xtreme sound 7.1 diamond sound card
the driver is ALSA although it seems that there is no specific driver for my soundcard (just in case anyone knows of one to support the soundcard that would be great because i cant use the 8 channel audio output with ALSA :( )

---

### Post by jrw10293 on 2008-10-09
I have the same problem. If I kill Firefox from the system monitor, I can play media in other applications. I may be way off, but I think it's a problem specific to Firefox and Ubuntu together, because it's the only application I have this problem with. I've tried different media players simultaneously, and they work fine. Also I just stopped using openSUSE, and I didn't have this problem. A good friend has the exact same problem so, I'd assume it's fairly common. If ANYONE knows how to fix this, please help.

---

### Post by jrw10293 on 2008-10-09
I snagged this off another thread: [http://ubuntuforums.org/showthread.php?t=793175](http://ubuntuforums.org/showthread.php?t=793175). I changed my sound use ALSA and now it works fine. I did have to tell my applications that didn't come packaged with Ubuntu that I'm using ALSA though.  > **ubuntu-freak said:**
> Are you both Hardy users? Try explicitly selecting PulseAudio in System > Preferences > Sound, instead of Auto Detect. If there is no improvement, even after a reboot, switch to ALSA instead (Gutsy used ALSA as default). You will have to tell non-GNOME apps (VLC, MPlayer etc) that you are now using ALSA, which you can do in their preferences. Reboot if anything weird happens, then test again.
 
Nathan

---

