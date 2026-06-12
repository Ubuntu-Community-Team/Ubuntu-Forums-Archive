---
title: "Patched mplayer still flickers"
date: 2008-01-13
forum: Multimedia &amp; Video
---

### Post by mikeym on 2008-01-13
Hi,

I've tried patching mplayer for compiz playback using this guide ([http://ubuntuforums.org/showthread.php?t=571556](http://ubuntuforums.org/showthread.php?t=571556)) and I've also tried using this guide ([http://ubuntuforums.org/showthread.php?t=636277&highlight=video+playback+compiz+mplayer](http://ubuntuforums.org/showthread.php?t=636277&highlight=video+playback+compiz+mplayer)), but I'm still getting a resonable amount of flicker and glitching on playback. 

This is mainly happening where there is a lot of movement in a scene. The patch has definitely worked because I can watch it in normal resolution whilst zoomed right in using compiz zoom desktop. My graphics card in NVIDIA 8600GTS and I have a dual core processor and I'm running compiz ontop of XFCE so it shouldn't be hardware related.

Could someone tell me where I'm going wrong?

(**[COLOR="Red"]edit[/COLOR]**) PS the CPU usage is normally not so high when glitching is happening I'm not sure why it is in this one but it's the only picture I managed to capture a glitch.

---

### Post by mikeym on 2008-01-14
* Bump *

Also, if anyone knows how to patch the SVN so that the gnome screensaver is disabled.

---

### Post by shirilover on 2008-01-14
I have also patched mplayer-svn for compiz, but I usually just toggle compositing off when watching video.
As for the gnome-screensaver problem, I use the python script from the follwing thread:
[http://ubuntuforums.org/showthread.php?t=284804&highlight=disablegss](http://ubuntuforums.org/showthread.php?t=284804&highlight=disablegss)

You could patch the SVN, by looking at the diff.gz from the Ubuntu source for mplayer(not as easy as the above method).

---

### Post by mikeym on 2008-01-15
Thanks,

I followed your advice and made patch from the Ubuntu source to fix the gnome screensaver. While the link you give is a worth while fix I'd rather not have another program polling on my computer unless I have to. 

[Here's a link to my howto thread.]("http://ubuntuforums.org/showthread.php?t=668257")

I've begun to suspect that the flicker I'm experiencing in mplayer is the result of the duff NVIDIA proprietary drivers, as I have noticed very similar flicker and glitching on my desktop when things are moving. [There's a thread hear about it]("http://www.nvnews.net/vbulletin/showthread.php?t=106244"), but I'm getting no response as per usual.

---

