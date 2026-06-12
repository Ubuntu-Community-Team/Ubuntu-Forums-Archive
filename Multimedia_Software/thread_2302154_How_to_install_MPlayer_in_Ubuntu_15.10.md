---
title: "How to install MPlayer in Ubuntu 15.10?"
date: 2015-11-08
forum: Multimedia Software
---

### Post by v-anjel on 2015-11-08
How do I install MPlayer in Ubuntu 15.10?  I used to install MPlayer on older versions of Ubuntu from a PPA (ppa:mc3man/mplayer-test).  Unfortunately, this PPA doesn't contain a package that is compatible with Ubuntu 15.10.  Also, why isn't MPlayer available in the official repositories.  I know MPlayer2 is available in the official repos, but the subtitle/OSD rendering on it is not as good as that of MPlayer.   Thanks!

---

### Post by tea for one on 2015-11-08
> **v-anjel said:**
> How do I install MPlayer in Ubuntu 15.10?  I used to install MPlayer on older versions of Ubuntu from a PPA (ppa:mc3man/mplayer-test).  Unfortunately, this PPA doesn't contain a package that is compatible with Ubuntu 15.10.  Also, why isn't MPlayer available in the official repositories.  I know MPlayer2 is available in the official repos, but the subtitle/OSD rendering on it is not as good as that of MPlayer.   Thanks!

Good morning

This is not really the answer to your question but you may wish to explore this link about smplayer:-

[http://smplayer.sourceforge.net/en/downloads](http://smplayer.sourceforge.net/en/downloads)

---

### Post by vasa1 on 2015-11-08
[http://manpages.ubuntu.com/manpages/wily/en/man1/mplayer.1.html](http://manpages.ubuntu.com/manpages/wily/en/man1/mplayer.1.html)

---

### Post by v-anjel on 2015-11-08
> **tea for one said:**
> Good morning  This is not really the answer to your question but you may wish to explore this link about smplayer:-  [http://smplayer.sourceforge.net/en/downloads](http://smplayer.sourceforge.net/en/downloads)  Thanks for the suggestion.  Does SMPlayer have a command-line only version available?  I prefer video players without GUIs.  > **vasa1 said:**
> [http://manpages.ubuntu.com/manpages/wily/en/man1/mplayer.1.html](http://manpages.ubuntu.com/manpages/wily/en/man1/mplayer.1.html)  Isn't this MPlayer2?  I'm looking for MPlayer.

---

### Post by ajgreeny on 2015-11-08
Why is it important **not** to have mplayer2?

You can use it with no GUI from terminal just as before with command **mplayer /path/to/file** and as far as I'm aware is just an updated version of mplayer.  The executable is still called mplayer, not mplayer2.

---

### Post by mc4man on 2015-11-08
> **v-anjel said:**
> How do I install MPlayer in Ubuntu 15.10?  I used to install MPlayer on older versions of Ubuntu from a PPA (ppa:mc3man/mplayer-test).  Unfortunately, this PPA doesn't contain a package that is compatible with Ubuntu 15.10.  Also, why isn't MPlayer available in the official repositories.  I know MPlayer2 is available in the official repos, but the subtitle/OSD rendering on it is not as good as that of MPlayer.   Thanks!

There will be a 15.10 package there shortly, likely will be the only one I do for wily due to the short life of these non lts 'releases' (unless there is some significant commit..

---

### Post by v-anjel on 2015-11-08
> **ajgreeny said:**
> Why is it important **not** to have mplayer2?  You can use it with no GUI from terminal just as before with command **mplayer /path/to/file** and as far as I'm aware is just an updated version of mplayer.  The executable is still called mplayer, not mplayer2.  I searched for a compatible version of MPlayer but wasn't able to find one so I'm reluctantly using MPlayer2 (from the command line) at the moment.  I prefer MPlayer over MPlayer2 for two reasons... a. The Subtitles/OSD rendering on MPlayer is much better than in MPlayer2 and b. MPlayer2 tells me that my system is too slow to play most of the videos I throw at it.  MPlayer, on the other hand, plays it flawlessly.  Here's the mplayer config file I'm using, in case anyone is interested... [https://github.com/nlindgren/config/blob/master/.mplayer/config](https://github.com/nlindgren/config/blob/master/.mplayer/config) It works on both MPlayer and MPlayer2 > **mc4man said:**
> There will be a 15.10 package there shortly, likely will be the only one I do for wily due to the short life of these non lts 'releases' (unless there is some significant commit..  I can't wait.  Thanks a bunch! :D

---

### Post by mc4man on 2015-11-08
> **ajgreeny said:**
> Why is it important **not** to have mplayer2?

You can use it with no GUI from terminal just as before with command **mplayer /path/to/file** and as far as I'm aware is just an updated version of mplayer.  The executable is still called mplayer, not mplayer2.
mplayer2 is a dead project so no bug fixes, no nothing.

---

### Post by mc4man on 2015-11-08
> **v-anjel said:**
>  Also, why isn't MPlayer available in the official repositories. 
mplayer is setup to use a local version of ffmpeg master, statically linked. Debian/Ubuntu don't use statically linked libraries in their builds so for mplayer to return it has to be adjusted to use the repo shared ffmpeg libs.
No one in Ubuntu will do this, Debian is a tortoise so to speak, maybe some day...
(A FFmpeg dev had offered to help with this but so far no movement.

---

### Post by v-anjel on 2015-11-08
Looks like the repo has been updated! Installing it now. :D  Edit: Mplayer installed successfully.  Thank you, mc4man.  I hope you will continue to build mplayer packages for future versions of Ubuntu.

---

### Post by mc4man on 2015-11-08
> **v-anjel said:**
> Looks like the repo has been updated! Installing it now. :D  Edit: Mplayer installed successfully.  Thank you, mc4man.  I hope you will continue to build mplayer packages for future versions of Ubuntu.
16.04 will get a lot more attention so there will be mplayer, mpv, ffmpeg packages,  ect. updated for quite some time

---

### Post by mc4man on 2015-11-09
It looks like it will return, currently needs a little help but should be fixed shortly, ect.
[https://launchpad.net/ubuntu/+source/mplayer/2:1.2-1](https://launchpad.net/ubuntu/+source/mplayer/2:1.2-1)

Edit - the mplayer-gui package is complete garbage, totally worthless - 
[https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/1514698](https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/1514698)

---

