---
title: "I somehow broke VLC"
date: 2007-08-06
forum: Multimedia &amp; Video
---

### Post by therandman on 2007-08-06
Somehow my VLC stopped playing DVD's and Divx, so I decided to uninstall it via Adept (Kubuntu).  Now I can't reinstall it; it won't let me in Adept or Add/Remove programs.  Was something possibly left behind that is causing this?  Thanks for the help in advance!

---

### Post by dougfractal on 2007-08-06
sudo apt-get remove --purge vlc
sudo apt-get install vlc

please post any errors

---

### Post by therandman on 2007-08-06
```
randmanmain@randmanmain:~$ sudo apt-get remove --purge vlc
Reading package lists... Done
Building dependency tree... Done
Package vlc is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
randmanmain@randmanmain:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree... Done
Package vlc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package vlc has no installation candidate

```

---

### Post by fredj on 2007-08-06
In Add/Remove applications look at the top right. Make sure you have selected ALL OPEN
SOURCE applications then do a search for vlc.

---

### Post by therandman on 2007-08-07
> **fredj said:**
> In Add/Remove applications look at the top right. Make sure you have selected ALL OPEN
SOURCE applications then do a search for vlc.

I am able to pull it up under the GNOME applications; when I check it, the check mark is light gray and automatically unchecks itself immediately.

---

### Post by dougfractal on 2007-08-07
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&subword=1&version=feisty&release=all&keywords=vlc&sourceid=mozilla-search](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&subword=1&version=feisty&release=all&keywords=vlc&sourceid=mozilla-search)
> Package vlc

    * feisty (graphics): multimedia player and streamer [universe]
      0.8.6.release-0ubuntu4: amd64 i386 powerpc

enable universe repository
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories)
>  How to add extra repositories

    * Read #General Notes 

[edit]
Using menus

    * Choose distribution-friendly repositories. These are part of the Ubuntu distribution system. This is the recommended method. 

System-->Administration-->Software Sources

Check the repositories you think you will need (main, universe, restricted, multiverse). You probably won't need the 'sources' repository.

---

