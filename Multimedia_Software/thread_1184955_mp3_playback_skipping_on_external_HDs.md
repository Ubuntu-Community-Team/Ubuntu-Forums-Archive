---
title: "mp3 playback skipping on external HDs"
date: 2009-06-11
forum: Multimedia Software
---

### Post by cmost on 2009-06-11
Hi folks!  I've discovered an irritating side effect of my switch from Debian to Ubuntu Jaunty.  My mp3's skip horribly when played from my USB external hard disks, regardless of which player I use (i.e., Exaile, Audacious, etc.)  I have a Western Digital 1 TB hard disk (MyBook,) plugged into a USB port residing on the motherboard.  Actually I have two identical such hard disks as I mirror one to the other.  I hard coded this hard disk by UUID in /etc/fstab to always mount to the same folder as I always keep it plugged in and turned on.  The disk is formatted with the EXT4 file system.  This arrangement worked absolutely fine in Debian Lenny for over a year and I had no problems playing music stored on this drive.  When I access my mp3 collection from any player in Ubuntu, however, the songs skip.  It's really irritating and enough of a deal breaker for me to consider ditching Ubuntu for Fedora 11.  I have recently updated to the recently released Kernel 2.6.30 (from here:  [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)) and wonder if this has anything to do with it, perhaps a regression I'm not aware of.  Prior to the official release of 2.6.30 I was running the release candidates of that kernel.  If anyone has any insight into this issue, I'm ready to hear it!  Thanks!!  :p

** Edit **

I did some Googling and there seems to be a problem with transfer speed on USB connected file systems in Ubuntu Jaunty.  That's just great!  
See here:  [http://ubuntuforums.org/showthread.php?t=1150108](http://ubuntuforums.org/showthread.php?t=1150108)

Bug Report:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/119730](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/119730)

Apparently this bug has been around since Ubuntu 8.10 but the devs were too busy implementing a flashy (worthless) notification system to worry about something as trivial as abysmal file transfer performance over the USB 2.0 bus.

---

### Post by andrew.46 on 2009-06-11
Hi cmost,

Sounds more than a little irritating :-). I am really only familiar with MPlayer for media playback but there is a caching option in there that should help with the slow transfer. Syntax would be something like:

```
mplayer -cache 2048 -cache-min 80 *<path_to_file>*
```

not a solution to your problem but it might help with the symptoms?

Andrew

---

### Post by cmost on 2009-06-11
Thanks Andrew!  I'll try your suggestion.  It would be a major pain in the a** to have to type this command in order to play mp3's.  It seems like every release of Ubuntu has one or two things that just make it unusable!!  This release it's the Intel regressions and this USB transfer bug.  Thankfully, streaming Internet radio from Shoutcast works okay.  :p  Shout out to Ubuntu developers:  Please, please, please devote more energy to polishing what's under the hood and ensure the basic infrastructure works instead of focusing on implementing new features!

---

### Post by wessexmario on 2009-07-23
You could take the pain out by adding the following alias to your .bashrc

      alias mplayer='mplayer -cache 2048 -cache-min 80'

then, whenever you use the mplayer command, the options will be automatically added into it.

---

