---
title: "Removing Fuppes from Ubuntu 9.1"
date: 2010-03-04
forum: Multimedia Software
---

### Post by endlessracingz on 2010-03-04
I am still largely a linux newbie also making me an Ubuntu newbie. I know the basics and have read the Ubuntu Pocket Guide several times and reference it a lot still. I went to the trouble of installing Fuppes onto my system (Ubuntu Server 9.1) and after configuring it and playing around with it I did not get the results I wanted. I soon after found PS3 Media Server which did almost everything I wanted to instantly with no configuration. Problem solved...

But what to do with the fuppes install? I did the following
```
sudo apt-get autoremove fuppes
```Just for arguement sakes I attempted to run ```
fuppes
``` to see if I removed it. However, I was wrong... fuppes started up like it always did
```
$ fuppes
            FUPPES - 0.662
    the Free UPnP Entertainment Service
      http://fuppes.ulrich-voelkel.de

webinterface: http://192.168.1.190:55085

r = rebuild database
u = update database
i = print system info
h = print help

press "ctrl-c" or "q" to quit
```Sooooo now what? I want to wipe everything I no longer need that is involved with fuppes away!

---

### Post by endlessracingz on 2010-03-05
bump

Can anyone help?

---

### Post by endlessracingz on 2010-03-07
bump

Anyone? Please!

---

### Post by axo on 2010-03-07
Hi,

I think what you are looking for is apt-get remove --purge fuppes.

---

### Post by endlessracingz on 2010-03-07
> **axo said:**
> Hi,

I think what you are looking for is apt-get remove --purge fuppes.

```
$ sudo apt-get remove --purge fuppes
[sudo] password for administrator: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package fuppes is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

```

I already used apt-get to remove the program... but the program still remains somehow. Even apt-get says the package is not installed and yet it is still capable of running when i type the "fuppes" command.

---

### Post by Kaligo on 2010-03-07
What output do you get from: ```
aptitude show fuppes
```

---

### Post by endlessracingz on 2010-03-07
```
$ aptitude show fuppes
No current or candidate version found for fuppes
Package: fuppes
New: yes
State: not installed
Version: 0+svn611-1
Priority: extra
Section: graphics
Maintainer: Andrew Colin Kissa <andrew@topdog-software.com>
Uncompressed Size: 1,397k
Depends: adduser, libavcodec1d (>= 0.cvs20070307), libavformat1d (>= 0.cvs20070307), libavutil1d
         (>= 0.cvs20070307), libc6 (>= 2.4), libgcc1 (>= 1:4.1.1-21), libgif4 (>= 4.1.6),
         libjpeg62, libmad0 (>= 0.15.1b), libmagick++10, libmagick10, libogg0, libpcre3 (>= 7.4),
         libpng12-0 (>= 1.2.13-4), libraw1394-8, libsimage20, libsqlite3-0 (>= 3.4.2), libstdc++6
         (>= 4.2.1-4), libswscale1d (>= 0.cvs20070307), libtag1c2a (>= 1.4), libtheora0,
         libtiff4, libuuid1, libvorbis0a (>= 1.2.0), libvorbisenc2 (>= 1.1.2), libvorbisfile3 (>=
         1.2.0), libxml2 (>= 2.6.27), lsb-base, zlib1g (>= 1:1.2.3.3.dfsg-1)
Description: A free, multiplatform UPnP A/V Media Server
 FUPPES supports a wide range of UPnP MediaRenderers
 as well as on-the-fly transcoding of various audio, video
 and image formats. FUPPES also includes basic DLNA support.

```

but I can clearly run fuppes still
```
$ fuppes
            FUPPES - 0.662
    the Free UPnP Entertainment Service
      http://fuppes.ulrich-voelkel.de

webinterface: http://192.168.1.190:42693

r = rebuild database
u = update database
i = print system info
h = print help

press "ctrl-c" or "q" to quit

```

---

### Post by Kaligo on 2010-03-07
Hmm, my first suspicion is that the logs for synaptic are broken.  If you try installing and uninstalling Fuppes that should reset its installation state.

---

### Post by endlessracingz on 2010-03-08
> **Kaligo said:**
> Hmm, my first suspicion is that the logs for synaptic are broken.  If you try installing and uninstalling Fuppes that should reset its installation state.

Re-downloaded the source code and installed fuppes once again. I tried removing via apt-get and it still didn't work... but what i tried that DID work was installing then uninstalling as follows:
```
$ svn co [https://fuppes.svn.sourceforge.net/svnroot/fuppes/trunk](https://fuppes.svn.sourceforge.net/svnroot/fuppes/trunk) fuppes
$ cd fuppes/
$ autoreconf -vfi
$ ./configure
$ make
$ make install
$ make uninstall

```

fuppes no longer runs and seems to be finally removed... I guess you should always keep the source code you gather for programs installed on the computer so that they can be removed by following the above path

---

### Post by Kaligo on 2010-03-08
So you didn't install it from synaptic originally? Well that would solve the mystery, glad to hear you got it sorted.

Please mark the thread as solved from the Thread Tool link at the top of the page.

Cheers.

---

