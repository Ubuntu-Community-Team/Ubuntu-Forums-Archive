---
title: "Ubuntu 12.10: How to completly remove pulseaudio?"
date: 2012-10-27
forum: Multimedia Software
---

### Post by ZoLToR on 2012-10-27
Hello.
How to completly remove pulseaudio in Ubuntu 12.10? Tried some manuals, but after them and after rebooting I see "pulseaudio" process in gnome-system-monitor and I can't change input/output audio settings in Skype because it think that pulseaudio is in system :(
Tried these commands:
```

sudo killall pulseaudio
killall pulseaudio
sudo apt-get remove pulseaudio
sudo apt-get purge pulseadio
sudo apt-get autoremove

```

Thanks. And sorry for my English:oops:

---

### Post by gordintoronto on 2012-10-27
I'm sorry, but I think you are asking the wrong question. Pulseaudio works fine with Skype.

---

### Post by jerrrys on 2012-10-27
try here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=How+to+completely+remove+pulseaudio&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=How+to+completely+remove+pulseaudio&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

---

### Post by ZoLToR on 2012-10-28
**gordintoronto**, hm, I has wheeze, noise from speakers, when Skype started notifications... I was not able to properly adjust the PulseAaudio and decided to remove it. Sound of Skype notifications when it output directly through ALSA - is perfect. 
And... I deleted pulseaudio from system. For it, before removing process, needed write text "autospawn=no" to ~/.pulse/client.conf.
But now I have other problem: I can't control my volume from notebook media keys. I has installed volti but it not starting with error message:
```
 
zoltor@zoltor-dm1:~$ volti
[alsactrl.py:__init__:41] can't open Master control for card Generic, trying to select first available mixer channel

[alsactrl.py:__init__:49] can't open first available control for card Generic
error: list index out of range
Traceback (most recent call last):
  File "/usr/bin/volti", line 53, in <module>
    volti = main.VolumeTray()
  File "/usr/lib/volti/volti/main.py", line 124, in __init__
    self.watchid = gobject.io_add_watch(fd, eventmask, self.update)
TypeError: an integer is required

```

**jerrrys**, ok, thank you.

---

### Post by edwardoclese on 2012-11-16
Oh so tired now, after so many release upgrades, so many tries to fix long standing problems with ubuntu and now ubuntustudio 12.10 on a variety of machines, all of which seem to boil down to pulseaudio. 

Recordings in Audacity and Ardour do not playback at proper speed.
Mute toggle will not unmute.
Crackle and stalls in Flash at fullscreen.

Now I've autoremoved pulseaudio, and it takes a bunch of stuff with it, including ubuntustudio-desktop, ubuntustudio-generation, and ubuntustudio-recording.

The mute toggle now works, but the indicator no longer exists

Launchpad Bug #972781 seems to match. 

The last install I had that worked was 10.10

---

