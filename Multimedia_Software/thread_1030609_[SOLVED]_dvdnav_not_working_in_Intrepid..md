---
title: "[SOLVED] dvdnav not working in Intrepid."
date: 2009-01-04
forum: Multimedia Software
---

### Post by wolfdale on 2009-01-04
Ok I have been working on this for a good 6 hours, here is my dilemma. I get the following message when I use dvdnav with mplayer.

No stream found to handle url dvdnav://

mplayer does work for non-menu dvd's (Matrix Reloaded plays great) but when it comes to DVD's that require a menu navigation (like Disney's Tinker Bell), I can't get it to work on mplayer with Intrepid. In fact, none of my movie players will play with dvdnav on Inprepid (Totem, VLC, xine) Hardy's works great with dvdnav. Thus I need help. I'm wonder if it is a added feature with Intrepid that disables the ability to view encrypted/protected DVD's. I have to boot into *gasp* XP in order to watch Disney DVD's. Searching the web, I found a bug report for Intrepid. [https://lists.ubuntu.com/archives/universe-bugs/2008-November/020972.html]("https://lists.ubuntu.com/archives/universe-bugs/2008-November/020972.html")

It would be helpful if someone can confirm that this is indeed a bug with Intrepid/mplayer/dvdnav or better yet if someone has a workaround.

Below is my current setup indicating the latest codec install.

tony@wolfdale:~$ lsb_release -rd ; uname -a ; apt-cache policy ffmpeg libdvdcss2 libdvdread3 libdvdnav4 regionset 
Description:	Ubuntu 8.10
Release:	8.10
Linux wolfdale 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux
ffmpeg:
  Installed: (none)
  Candidate: 3:0.svn20080206-12ubuntu3
  Version table:
     3:0.svn20080206-12ubuntu3 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages
libdvdcss2:
  Installed: 1.2.10-0.2medibuntu1
  Candidate: 1.2.10-0.2medibuntu1
  Version table:
 *** 1.2.10-0.2medibuntu1 0
        500 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages
        100 /var/lib/dpkg/status
libdvdread3:
  Installed: 0.9.7-11ubuntu2
  Candidate: 0.9.7-11ubuntu2
  Version table:
 *** 0.9.7-11ubuntu2 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages
        100 /var/lib/dpkg/status
libdvdnav4:
  Installed: 4.1.2-3
  Candidate: 4.1.2-3
  Version table:
 *** 4.1.2-3 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages
        100 /var/lib/dpkg/status
regionset:
  Installed: 0.1-3
  Candidate: 0.1-3
  Version table:
 *** 0.1-3 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages
        100 /var/lib/dpkg/status

---

### Post by mc4man on 2009-01-04
If your using the repo version of mplayer than I don't believe it's dvdnav enabled. I use my own built versions so not 100% sure but the dvdnav version does require libdvdnav4 4.1.3-1 and libdvdread4 4.1.3-1 (note that libdvdread 3 and 4 can coexist.

If you don't want to build use rvm's ppa repo (smplayer

I believe his current mplayer is dvdnav enabled

[https://launchpad.net/~rvm/+archive](https://launchpad.net/~rvm/+archive)
[http://smplayer.berlios.de/forums/viewtopic.php?id=741](http://smplayer.berlios.de/forums/viewtopic.php?id=741)

(if you have 2 drives mplayer defaults to /dev/dvd, or if only one d. ck. your /dev's

```
sudo lshw -C disk
```

Note that some structure protected titles will not work right in mplayer in dvdnav mode, in those cases use smplayer or specify the main movie title


Edit: if you get it going note that you can also set up a autorun for mplayer dvdnav (or a couple

This also allows you to r. click on the dvd icon and choose mplayer dvdnav or whatever you name it.

All you need is a command that works in most cases or specifically to the use intended. (I actually have 3, Mplayer Dvdnav,  Mplayer Dvdnav 1 , Mplayer Dvdnav 2 (different commands for different situations

see screens for 1

---

### Post by wolfdale on 2009-01-04
Thank you mc4man for pointing me to the SMPlayer project, those guys (and gals) are geniuses. I installed their pre-built *.deb packages and it got dvdnav working again, I'm back in Disney heaven.

Seriously, I installed libdvdread4 fist followed by libdvdread, libdvdnav and mplayer. Intrepid popped warnings that libdvdread4 was untested and could be harmful but I installed anyway. I suspect over time libdvdread4 will be incorporated into medibuntu or some other common repository. 

Again thanks for your help. I definitely learned a lot.

---

### Post by mc4man on 2009-01-05
> Intrepid popped warnings that libdvdread4 was untested and could be harmful but I installed anyway

I wouldn't worry about that, I've been running those versions on hardy for quite some time with no issues, plus libdvdread3 is still in place for those apps that require it.

I would also advise not to use the installed default gui for mplayer (gmplayer.

It's what you'll see in your Applications menu, it can have a 'rough' time with a dvdnav version of mplayer as the backend. ( and anyway you have smplayer which while it doesn't yet support menus is a superior gui media player.

---

