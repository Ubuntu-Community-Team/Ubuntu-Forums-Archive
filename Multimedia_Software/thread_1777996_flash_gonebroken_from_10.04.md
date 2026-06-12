---
title: "flash gone/broken from 10.04 ?"
date: 2011-06-08
forum: Multimedia Software
---

### Post by i.r.id10t on 2011-06-08
Thought 10.04 is an LTS release?  Did updates yesterday, Flash is now gone from my system.  The flashplugin-nonfree package is still installed.  Tried purging and reinstalling it, no joy.

Suggestions before I go and manually install it?

Running 10.04 on x86

---

### Post by i.r.id10t on 2011-06-08
So ya know, not having any real work to do - other than getting bigbluebutton and sakai working - I took a closer look at the errors.  

Apparently, the flashplugin-nonfree package installs a flashplugin-installer package, and that package has a bad version number in it.  Browsed the directory on archive.canocial.com and found the current version, downloaded it manually, set up a webserver on localhost, edited my hosts file to point locally, and apt- found the package.  Unfortunately the md5sums differ, and I really don't have time to go correcting the package, etc.

<voice volume=loud type=annoyed content=rant>
Ya know, Ubuntu used to be good. But then "they" started screwing with things - using the MAC address to determine ethernet device names, changing the way the boot scripts work, etc.  Thought that my particular issues wiht 10.04 were minimal, and that I could get a few years of use in before switching back to Debian, Slackware, Gentoo, or even LFS.  But this broken packaging on a LTS release really grinds my gears ...  

Next term I'll NOT be using Ubuntu either on any of my systems, as a recommendation to those who ask about Linux, or for the courses I teach.
</voice>

Sorry, I know that my fellow forums folks aren't in charge of anything regarding packages, support, etc. but a guy has to vent once in a while....

---

### Post by no2498 on 2011-06-08
install the plugin flash aid for fire fox 
then run it
your all done

---

### Post by i.r.id10t on 2011-06-08
> **no2498 said:**
> install the plugin flash aid for fire fox 
then run it
your all done

And doing this will provide security updates, etc as they are available?  One of the big reasons to use a distro wtih a package manager is to ... manage your packages!

I've submitted this on launchpad and filed a bug report ...

---

### Post by no2498 on 2011-06-08
it told me today there is a update ready for flash but only in fire fox
on this computer i use opera

---

