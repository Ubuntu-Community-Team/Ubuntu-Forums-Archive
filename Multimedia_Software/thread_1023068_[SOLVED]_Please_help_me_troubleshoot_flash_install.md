---
title: "[SOLVED] Please help me troubleshoot flash install for Firefox 3 in hardy!"
date: 2008-12-27
forum: Multimedia Software
---

### Post by johnzollo on 2008-12-27
Hello!

    Thanks for letting me post.  I love Ubuntu and I really like the forums so I was hoping someone may be able to help with my question.  I'm trying to install flash (the plugin) for Firefox.  I tried inside of Firefox and that didn't work.  I tried installing the flashplugin-nonfree off of one of the respositories (either partner or multiverse -- I forget) and it failed after trying to download flash 9 -- which wasn't there.  I believe i installed off of another repository to get adobe-flashplugin, which installed and created a file (a link actually) in /usr/lib/mozilla/plugins, but Flash doesn't work in Firefox (3) and I can't see the plugin either.  :popcorn:

PLEASE HELP!!!

Here is is my info:
a newly installed hardy (heron) (8.04)
Firefox 3.0.5

Here are some info from the terminal:

```
john@maxwell:~$ dpkg -s adobe-flashplugin
Package: adobe-flashplugin
Status: install ok installed
Priority: optional
Section: partner/web
Installed-Size: 9868
Maintainer: DL-Flash Player Ubuntu <FlashPlayerUbuntu@adobe.com>
Architecture: i386
Version: 10.0.15.3-1hardy2
Replaces: flashplugin (<< 6)
Provides: flashplugin-nonfree
Depends: debconf | debconf-2.0, fontconfig, libatk1.0-0 (>= 1.20.0), libc6 (>= 2.4), libcairo2 (>= 1.6.0), libcurl3, libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.3.5), libgcc1 (>= 1:4.1.1-21), libglib2.0-0 (>= 2.12.0), libgtk2.0-0 (>= 2.12.0), libnspr4-0d, libnss3-1d, libpango1.0-0 (>= 1.20.5), libstdc++6 (>= 4.1.1-21), libx11-6, libxext6, libxt6, wget
Suggests: firefox, konqueror-nsplugins, msttcorefonts, ttf-bitstream-vera | ttf-dejavu, ttf-xfree86-nonfree, x-ttcidfont-conf, xfs (>= 1:1.0.1-5)
Conflicts: flashplayer-mozilla, flashplugin (<< 6), xfs (<< 1:1.0.1-5)
Description: Adobe Flash Player plugin version 10
 This package will download the Flash Player from Adobe. It is a
 Netscape/Mozilla type plugin. Any browser based on Netscape or Mozilla can use
 the Flash plugin. This package officially supports the following browsers:
 .
 Firefox 2.x, Firefox 3.x, SeaMonkey 1.11



john@maxwell:~$ dpkg -s flashplugin-nonfree
Package: flashplugin-nonfree
Status: purge ok not-installed
Priority: optional
Section: contrib/web




john@maxwell:~$ ls -l /usr/lib/mozilla/plugins
total 0
lrwxrwxrwx 1 root root 37 2008-12-27 12:25 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
john@maxwell:~$ 


```

I'd appreciate anything you could do...:guitar:

Thank you!
john

---

### Post by thadacto on 2008-12-27
If you are running AMD 64 then try this attachment. I don't know if it works for 32 bit systems.

---

### Post by johnzollo on 2008-12-27
THIS PROBLEM IS NOW SOLVED -- THANKS TO Everyonr that helped!!

Thadacto, thank you, but I'm running i386, so it didn't turn out to be that.  Thank you for your quick response.  What I did though, was run firefox from the command line (I was trying  to run it as sudo -- bad idea -- don't run firefox as sudo it will mess up the ownership of a few critical files in the ~/.mozilla dir).  When I did (run it from the command line), I got this error:

```
failed to initialize shared library /usr/lib/adobe-flashplugin/libflashplayer.so
```

I googled it and found out it was an existing problem.  The flash can't find the libraries it needs, so it will not load correctly. Here's a link on Ubuntu's forum (our forum):

[http://ubuntuforums.org/showthread.php?t=951194&page=2](http://ubuntuforums.org/showthread.php?t=951194&page=2)

And here's a link mentioned in that post above:

[http://linuxowns.wordpress.com/2008/08/12/install-flash-player-10-rc-on-ubuntu/](http://linuxowns.wordpress.com/2008/08/12/install-flash-player-10-rc-on-ubuntu/)

Creating the symblic links (sudo ln -s) worked great!  It works fine now.  I got my evite card from my friend -- it was funny & cute!

THANK YOU EVERYONE for your help!

Regards,
john zollo   :guitar:

---

### Post by thadacto on 2008-12-27
You're welcome, johnzollo.
I wrote that install doc as I had so much trouble getting flash to work. I hope it will help someone in the future. It was written by a dummy for a dummy. You seem to know what you're doing - I didn't  and still don't!!

---

