---
title: "Trouble with playing media"
date: 2014-03-14
forum: Multimedia Software
---

### Post by drew14 on 2014-03-14
im new here, (just came in from windows xp -(dual boot). My rhythmbox and VLC players are staggering and speeding up. I downloaded something called xmms but although I can see it in my download folder, I cant seem to find an exe file to open it. Is there a better program that I should be downloading and using with Ubuntu??
   I dont know from typing commands, ( came into computers too late post windows 95...lol), but I can follow easy instructions,just please be explicit. Thanks for all and any help
:guitar:

---

### Post by ssam on 2014-03-14
You should use the software center to install programs.

What hardware do you have? CPU? Graphics card?

---

### Post by Vladlenin5000 on 2014-03-14
My first comment XMMS is redundant if you already have Rhythmbox. Only install/use it if you really want XMMS over the default player (to each its own...).
 There's no *.exe file in Linux world. The sooner you free yourself from that "Windows mindset" the better. As explained in the previous post, always start searching for new software in the Software Center - It's an 'app store' like any other and even Windows 8 seems to be geared in that direction so you better get used to it. When not found in the 'app store' then - and only then - it's time to search somewhere else.

---

### Post by SeijiSensei on 2014-03-14
I recommend installing [SMPlayer](http://smplayer.sourceforge.net/) for video playback.  It's in the repositories which you can access via the Software Center application.

There's also a Windows version.

---

### Post by drew14 on 2014-03-15
thank you all, but I didnt get the answer I needed. My music and you tube videos are  unwatchable staggered and playing way too fast. I have this notebook w split xp and ubuntu. the ubuntu os is working fine, the media playback is a problem. when I reboot and play youtube or vlc under win xp, it all plays normal, only under ubuntu am I seeing these issues. IS there a way to set this?  thanks in advance

---

### Post by speartip on 2014-03-15
Have you installed all the relevant codecs? If not open a terminal & paste the following:
```
sudo apt-get install ubuntu-restricted-extras lame sox transcode flac ffmpeg cdrdao
```
That should be enough, then for dvd playback:
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```
Hope that helps.

---

### Post by drew14 on 2014-03-16
please dont laugh, undiscoverable built in to motherboard graphics, not a separate card. cpu1.33  2g mem 32 bit, running Ubantu 12.04Lts

---

### Post by drew14 on 2014-03-16
how do I open a terminal?

---

### Post by oldos2er on 2014-03-16
> **drew14 said:**
> how do I open a terminal?

Ctrl-Alt-t

Could you copy & paste the following command in a terminal, then copy & paste its output here so we can see what graphics card you have? ```
lspci | grep VGA
```

---

### Post by drew14 on 2014-03-16
i entered the codes as you said into terminal and it loaded. Upon playing a cd ( mp3s), banshee played it, once again staggering cutting out, unusable...same happened using gnome...its got to be my computer, im guessing. thanks for your help

---

### Post by drew14 on 2014-03-16
i downloaded an mp3 to the desktop, I tried banshee, gnome and movie player and vlc...just like from the cd-r, skipping staggers, sped up, unusable. I did use terminal and copy& pasted the codes you send it and they loaded fine. guess its time to stop and go or a new computer if Im going to tangle and get to enjoy linux once and for all.    Any suggestions for a reasonable computer and basic printer for home use, under 500 that is ubuntu friendly& will do it all including games ?    Again, THANK YOU to all who took the time to help. its trully appreciated.

---

### Post by speartip on 2014-03-17
If all plays well on Windows XP, then I doubt it is a computer problem.
It is still most likely a hardware compatibility problem if you have installed all the relevant codecs.
If you are looking for a new computer anyway, I always look for one that is all intel based including intel integrated graphics. That way your less likely to run into hardware issues.

---

### Post by drew14 on 2014-03-17
thank you

---

### Post by Yellow Pasque on 2014-03-17
This is worth a shot: [https://wiki.ubuntu.com/Audio/PositionReporting](https://wiki.ubuntu.com/Audio/PositionReporting)

---

