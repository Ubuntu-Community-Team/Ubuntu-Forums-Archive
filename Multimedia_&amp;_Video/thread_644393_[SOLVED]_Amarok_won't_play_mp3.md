---
title: "[SOLVED] Amarok won't play mp3"
date: 2007-12-18
forum: Multimedia &amp; Video
---

### Post by brett611 on 2007-12-18
I've tried the suggestions in other threads but have a slightly different problem.  Amarok tells me that "Some media could not be loaded (not playable)".  see screenshot.  They're all mp3's and play fine on rhythmbox.  I keep hearing how awesome Amarok is and I have application envy...Thanks.

---

### Post by p_quarles on 2007-12-19
What other suggestions have you tried, specifically? (i.e., help us help you).

Anyway, to get Amarok playing MP3s, you'll need to install a couple of packages, which can be done by running this command:
```
sudo apt-get install libxine1-ffmpeg kubuntu-restricted-extras
```
You can also search for those two packages using the graphical package manager.

---

### Post by Mark20 on 2007-12-19
Hey I have the same problem.

I installed kubuntu-restricted-extras no problem.  But the libxine1-ffmpeg package returned the following when I tried to install it:
```

mark@Markonia:/etc/apt$ sudo apt-get install libxine1-ffmpeg
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libxine1-ffmpeg: Depends: libavcodec1d (>= 0.cvs20070307) but it is not installable
                   Depends: libavutil1d (>= 0.cvs20070307) but it is not installable
                   Depends: libmad0 (>= 0.15.1b) but it is not installable
                   Depends: libpostproc1d (>= 0.cvs20070307) but it is not installable
                   Depends: libxine1 (>= 1.1.8) but 1.1.7-1ubuntu1 is to be installed
E: Broken packages

```

I have all the sources uncommented in my sources.list file...do I need another source for this specific package?  Any suggestions?

---

### Post by p_quarles on 2007-12-19
@Mark20: That's odd. Try installing one of the packages that it's telling you is uninstallable. My guess is that they're conflicting with another package that you have. Attempting to install it will tell you which package(s) it needs to remove, and ask you whether you want to proceed.

---

### Post by brett611 on 2007-12-19
I'll try that tonight.  In the meantime here's what I've done so far:
Installed & uninstalled and installed Amarok via Synaptic.  Installed Automatix2

Followed advice of threads to install gstreamer0.8-mad.  Was told that did not exist.

Most of the orig threads I tried I now can't find.  I know, next thing I'll be telling you how big a fish I caught was...
[https://help.ubuntu.com/community/Re...515ba7630fcc59](https://help.ubuntu.com/community/Re...515ba7630fcc59)

---

### Post by Mark20 on 2007-12-19
Thanks p_quarles, I manually installed the packages first, then I was able to install the libxine1-ffmpeg package no problem!!

---

### Post by brett611 on 2007-12-20
I figured it out...but it has led to another problem so I've scratched Amarok and am using Exaile without any problems.

The problem with Amarok had to do with the Collections.  When I installed Ubuntu 7.10 I had all my files/music on an external USB HD.  When I first used Amarok it built the Collections based off the usb HD.  I copied the music to a music folder on the internal HD and used the tools to rebuild the Collections.  I had the settings to monitor changes, etc.

However, Amarok's Collections continued to look for the usb hd files.  It actually played mp3's with no problem when I navigated to the music folder.

The Collections db apparently does not get erased/deleted when uninstalling Amarok.  I couldn't find any threads about the collections db issue so I decided to cut my losses.  So far Exaile is everything I need.

If anyone knows where Amarok's Collections db is located / how to delete it please let me know as I have to assume its sitting there taking up space.

Thanks

---

### Post by p_quarles on 2007-12-20
The database is located in this file:
```
/home/*username*/.kde/share/apps/amarok/collection.db
```

---

### Post by brett611 on 2007-12-20
thx!

---

### Post by Spirotot on 2007-12-26
> **p_quarles said:**
> What other suggestions have you tried, specifically? (i.e., help us help you).

Anyway, to get Amarok playing MP3s, you'll need to install a couple of packages, which can be done by running this command:
```
sudo apt-get install libxine1-ffmpeg kubuntu-restricted-extras
```
You can also search for those two packages using the graphical package manager.

Thanks... I was having a problem similar to the original poster's problem. And, this worked! Thanks again!

---

