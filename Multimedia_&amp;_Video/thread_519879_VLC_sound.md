---
title: "VLC sound"
date: 2007-08-07
forum: Multimedia &amp; Video
---

### Post by covisp on 2007-08-07
I am new to Ubuntu, but not new to Linux/Unix/BSD/OS X, etc. I installed it and got it up and running without issue, even got my Apple bluetooth keyboard to talk to my white box x86 running Ubuntu 7.04.

I use SMB to mount my various drives on my main machine (Mac) so that I have access to all my media stuff, and this all works fine (even got them to automount on boot).

When I play stuff in "Movie Player" it all plays fine, but I really like the various features tha tVLC offers and I am used to using it under OS X and Windows, so I installed it. Also, since ther are less technical people using the machine to watch videos, I'd prefer having the exact same program for everyone.

(Yeah, this is all offered as proof that I'm not a n00b)

However, when I play stuff in VLC, the sound is very choppy, almost like static or that sort of choppiness you get when the gain is too high for the speakers.  I've played identical files in Movie Player and VLC and the sound is fine in one and not in the other.  I have the computer hooked up to some dell PC speaker set (subwoofer, 2 front, 2 rear) but I can't find a model number on the Subwoofer, though I doubt that is the issue as I've used the same speakers under windows and OS X and with Movie Player without issue.

I saw a lot of threads on NO sound in VLC, but nothing on bad sound, so what now?

I'm making due with Movie Player, which is quite good and I can certainly live with it, but this has me bugged now, so I'd like to solve it.

Linux ubu 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux

$ apt-show-versions -r vlc*
vlc/feisty uptodate 0.8.6.release-0ubuntu4
libvlc0/feisty uptodate 0.8.6.release-0ubuntu4
libservlet2.3-java/feisty uptodate 4.0-8ubuntu3
vlc-nox/feisty uptodate 0.8.6.release-0ubuntu4
mozilla-plugin-vlc/feisty uptodate 0.8.6.release-0ubuntu4
vlc-plugin-esd/feisty uptodate 0.8.6.release-0ubuntu

anything I forgot to mention?

---

### Post by Azmo on 2007-08-15
Settings -> Preferences -> Audio -> Output modules

Enable "Advanced options" by checking the box at the lower right.

Then e.g choose OSS. Worked for me.

---

### Post by magicrobotmonkey on 2007-08-17
> **Azmo said:**
> Settings -> Preferences -> Audio -> Output modules

Enable "Advanced options" by checking the box at the lower right.

Then e.g choose OSS. Worked for me.

That doesnt work for me. I still have static with all videos only in vlc, not in any other players

---

### Post by robog2 on 2007-08-23
Same problem here.  None of the output modules correct this.

---

### Post by Juan_VCS on 2007-08-24
Try *[COLOR="RoyalBlue"][this](http://ubuntuforums.org/showpost.php?p=2943608&postcount=2)[/COLOR]*

---

