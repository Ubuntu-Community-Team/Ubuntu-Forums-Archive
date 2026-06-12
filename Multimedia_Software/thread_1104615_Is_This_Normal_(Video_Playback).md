---
title: "Is This Normal? (Video Playback)"
date: 2009-03-23
forum: Multimedia Software
---

### Post by joey-elijah on 2009-03-23
I've encountered this on all my various Ubuntu installations during the past year or so - including on different hardware, so i don't think it's a missing codec or dodgy install... 

When i play video back in OS X, Windows Vista or Windows 7 - it's smooth and slick and fine.

When i play video back in Ubuntu it plays fine, sound etc BUT as it plays there are times when  (particularly during fast moving scenes) where the video has some kind of line horizontally dividing the picture and there is a slight, but very quick, lag to the top of the picture above this 'line'. It's very quick as i say, but it's something i've only ever encountered in Linux - it's the same in Totem, VLC but happens slightly less in Gnome MPlayer.

Argh. i can't articulate what it is very well. It's never on screen long enough for a screen grab and screencap tools are too slow to pick it up.

It does mean i don't use Ubuntu for watching my tv shows or movies (avi's, divx, etc) as they all suffer from it, and whilst it's not overly intrusive it's a bit annoying watching an action sequence and the top 3rd seems to move slower than the rest for a slight second... every few minutes.

Like i said i've tried it on various hardware - from a 1GB Nvidia 8500GT to a GMA500 all seem to have it.

I'm sorry i can't word it better just wondering it anyone has notice the same thing? In a way I'm hoping yes - because it must mean that there is something wrong with every 20+ install of Ubuntu and Ubuntu-derivatives I've done this last year, but on the other hand i really prefer Ubuntu to Windows and it's annoying having to boot into Windows to watch a movie etc.

---

### Post by lovinglinux on 2009-03-23
This is a known issue with nVidia cards. The best solution is to update the card drivers. There is new version (180.x I guess) that fix this problem.

You can also disable compiz while watching videos. You can easily do this with fusion-icon:

```
sudo apt-get install fusion-icon
```

There are other workarounds, but they do not work for everyone.

[http://ubuntuforums.org/showthread.php?t=942339](http://ubuntuforums.org/showthread.php?t=942339)

---

### Post by joey-elijah on 2009-03-24
Thanks for the reply. 

HOwever i also encounter this on an intel card in my netbook...

---

