---
title: "trying to install multimedia codecs"
date: 2007-05-07
forum: Multimedia &amp; Video
---

### Post by Bashed on 2007-05-07
Used this guide to install multimedia codecs:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs)

Ran into a few issues here...

chad@Secured:~$ sudo apt-get install ubuntu-restricted-extras libxine-extracodecs gstreamer0.10-plugins-base gstreamer0.10-plugins-good \
> gstreamer0.10-plugins-bad gstreamer0.10-pitfdll
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
libxine-extracodecs is already the newest version.
gstreamer0.10-plugins-base is already the newest version.
gstreamer0.10-plugins-good is already the newest version.
[COLOR=Red]E: Couldn't find package gstreamer0.10-pitfdll[/COLOR]

chad@Secured:~$ sudo apt-get install w32codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
[COLOR=Red]E: Package w32codecs has no installation candidate[/COLOR]

chad@Secured:~$ sudo aptitude install libdvdread3 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

chad@Secured:~$ sudo /usr/share/doc/libdvdread3/install-css.sh
No prebuilt binary available.  Will try to build and install it.
You need to have debhelper and fakeroot installed.
If not, interrupt now, install them and rerun this script.

This is higly experimental, look out for what happens below.
If you want to stop, interrupt now (control-c), else press
return to proceed

[COLOR=Red]Install debhelper and fakeroot, then run this script again[/COLOR]


(I installed fakeroot and debhelper, then re-ran the script)...with errors.

checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
[COLOR=Red]checking for C compiler default output... configure: error: C compiler cannot create executables
See `config.log' for more details.
make: *** [build-stamp] Error 77[/COLOR]

---

### Post by Anlace on 2007-05-07
I too had problems with the ubuntu wiki howto.  I did get everything working perfectly by using this sticky thread in this forum:

Enabling Multimedia in Feisty (HOW-TO)
[http://ubuntuforums.org/showthread.php?t=413626](http://ubuntuforums.org/showthread.php?t=413626)

Seems like the only thing you are missing is adding medibuntu to your apt resources list.

Peace,
Gail

---

### Post by Bashed on 2007-05-07
I followed that and still get this:

chad@Secured:~$ sudo apt-get install libdvdcss2 w32codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate

---

### Post by Bashed on 2007-05-07
I was also not able to find "GStreamer plugins for aac, xvid, mpeg2, faad" in add/remove. I even selected "all open source applications" and searched for gstreamer, still did not show up.

---

### Post by Anlace on 2007-05-07
Interesting . . . .

When you do "apt-get update" does medibuntu give you any time-out or connection errors?

There is a repository HowTo on Medibuntu's web site [http://medibuntu.sos-sts.com/](http://medibuntu.sos-sts.com/)
Also in their list of available packages:  w32codecs  20061022-0medibuntu1+build1

I would guess that your challenge is with adding and/or updating the Medibuntu repository.

Peace,
Gail

---

### Post by Bashed on 2007-05-07
chad@Secured:~$ sudo wget [http://medibuntu.sos-sts.com/sources.list.d/feisty.list](http://medibuntu.sos-sts.com/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list
--15:22:21--  [http://medibuntu.sos-sts.com/sources.list.d/feisty.list](http://medibuntu.sos-sts.com/sources.list.d/feisty.list)
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving medibuntu.sos-sts.com... 88.191.42.241, 88.191.35.32, 88.191.30.43, ...
Connecting to medibuntu.sos-sts.com|88.191.42.241|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 240 [text/plain]

100%[========================================================================================================================================>] 240           --.--K/s             

15:22:22 (15.26 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [240/240]



Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release
Hit [http://raof.dyndns.org](http://raof.dyndns.org) feisty Release      
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Sources
Hit [http://raof.dyndns.org](http://raof.dyndns.org) feisty/experimental Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Sources
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Packages
Hit [http://raof.dyndns.org](http://raof.dyndns.org) feisty/experimental Sources
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Sources
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Sources
Fetched 197B in 2s (67B/s)
Reading package lists... Done

chad@Secured:~$ sudo apt-get install libdvdcss2 w32codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdcss2 is already the newest version.
libdvdcss2 set to manual installed.
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate

---

