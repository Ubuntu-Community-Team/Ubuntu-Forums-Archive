---
title: "karmic sound only in amarok"
date: 2009-10-31
forum: Multimedia Software
---

### Post by allaf on 2009-10-31
Hi,

I'm going crazy here.
On my almost fresh install of karmic (i kept my /home), I do have **sound in amarok** but **no sound in any other non kde application**.

No sound in xine mplayer vlc flash.

I have linux-backports-modules-alsa-karmic-generic installed

I have followed the "[Comprehensive Sound Problem Solutions Guide v0.5e]("http://ubuntuforums.org/showthread.php?t=205449")" but i don't want to recompile alsa that's plain crazy as amarok has sound!

so to make it short : 
- sound ok in amarok and kde apps like kaffeine
- no sound anywhere else

(i am in the audio group, i removed pulseaudio package)

Also the sound was working fine until i rebooted, i don't get it, i've looked everywhere on the net but nothing works.


Any help appreciated.

---

### Post by allaf on 2009-10-31
Turns out alsa was using another sound card as default, I had to specify the soundcard to use for alsa in ~/.asoundrc

[http://alsa.opensrc.org/FAQ026](http://alsa.opensrc.org/FAQ026)


Looks like your pc can change the soundcard order randomly at boot.

---

### Post by allaf on 2009-10-31
No i spoke too soon.

Problem is only half solved, now when i play a video with xine or flash the other applications are muted, like the old days with oss.
I just don't get it.

---

### Post by ilcavero on 2009-11-01
I have the same problem in ubuntu, amarok seems to be broken.

---

