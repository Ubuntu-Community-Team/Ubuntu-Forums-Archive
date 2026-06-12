---
title: "Sound in Flash doesn't work"
date: 2007-06-11
forum: Multimedia &amp; Video
---

### Post by iAlta on 2007-06-11
Sound in Flash doesn't work, and I'm quite annoyed.

This means that I can't get stuff like; YouTube and other flash-based video players only play the video not the audio, flash based aduio streamers like the one on twit.tv or audible.com don't work, and of course flash games and flash website don't work propperly.

I can say that sound normally works and flash normally works, I can even play .flv 's on offline, non-flash players like totem, rythembox or Democracy. The problem is also in Opera and IE v/Wine.

I have tried different things like editing [/etc/firefox/firefoxrc]("http://ubuntuforums.org/showthread.php?t=255422"), I have tried making a symbolic link to [/usr/lib/libesd.so.1]("http://ubuntuforums.org/showthread.php?t=204022"). But all in vain

Does anyone know how to fix this problem?

---

### Post by grathinam on 2007-07-01
Did you make audible work on your system, am having same issue unable to play anything from audible.com.

If you resolved it please share your resolution

thanks in advance

---

### Post by kingpico on 2007-07-01
oss and alsa working at the same time for you? 
if yes then try to edit your ~/.asoundrc  If there is no .asoundrc txt file then make one.
now i cant tell you what the configuration should be , because i dont know what driver you use for sound. But you can go to the alsa website, read and **understand** how **dmix ** is working. 
I had the same problem with you sometime ago and i couldnt find a damn solution on web pages. dmix tutorial fixed the problem! 

have a look here as well [http://gentoo-wiki.com/HOWTO_ALSA_sound_mixer_aka_dmix](http://gentoo-wiki.com/HOWTO_ALSA_sound_mixer_aka_dmix) it might help you.

---

### Post by iAlta on 2007-07-14
POST no 2:
I was tring to use the audible flash player on their website for playing promos.
the .aa files are dripping in DRM, they don't work in linux, you'll have to burn them on a disk from Windows or MacOSX (which you can only do once) and then rip the CD's to .ogg files.

POST no3:
Thanks, created the txt file, will report back when I've gone through the howto, so far I've only come to the identify your driver part. (ens1370)

---

### Post by iAlta on 2007-07-15
OMFG!

I was surfing around ThinkGeek today, and there was an YouTube video there, and just started it, and I heard a strange sound, music like. I paused the podcast I was listening to but the music was still playing. I then paused the YouTube video and the music stopped. It worked!!! It acctually worked! After months of soundless YouTube, it acctually worked. I didn't go through the whole how-to, I just created the txt file, and whent on with my business, never bothering to test it out.


IT WORKED!!!!!!!!!!!!11\\:D/ \\:D/ \\:D/ \\:D/ \\:D/ \\:D/ \\:D/ \\:D/

---

### Post by josesanders on 2007-07-16
Can you please post exactly what you did, or at least a link to the howto that you refer to?

---

### Post by iAlta on 2007-07-16
The howto is the one in the third post, and all I did was 
```
touch .asoundrc
```

EDIT:
No wait, I looked at the file and it says,
```
pcm.!default {
type hw
card 0
}

ctl.!default {
type hw
card 0
}
```

I remember doing that, but I thought I didn't save it, oh well...

---

