---
title: "Flashplayer will not work in Ubuntu 11.04"
date: 2011-05-14
forum: Multimedia Software
---

### Post by Zeta014 on 2011-05-14
Just what the title says, Natty Narwhal doesn't want me on youtube or other Flash powered sites in either Chrome or Firefox. Clicking the "Install Adobe Flash" button sends me to the Adobe website where I can install it, but nothing works. Any fixes?

---

### Post by MCTRL_751 on 2011-05-17
I'm having a similar problem, where my flash player will not function on either Chromium or Firefox on 11.04.

I haven't tried much yet, so I'm open to any and all suggestions. A list of what NOT to do may also be helpful.

---

### Post by garvinrick4 on 2011-05-17
> **MCTRL_751 said:**
> I'm having a similar problem, where my flash player will not function on either Chromium or Firefox on 11.04.

I haven't tried much yet, so I'm open to any and all suggestions. A list of what NOT to do may also be helpful.
Most likely easiest for you to open a terminal: ctrl/alt/t 
```
sudo apt-get install ubuntu-restricted-extras
```will give you quite a bit you will need see below: gstreamer bad & ugly for audio plus java plus mp3 playback and flash also.
```
Package: ubuntu-restricted-extras        
State: installed
Automatically installed: no
Version: 43
Priority: optional
Section: multiverse/metapackages
Maintainer: Michael Vogt <michael.vogt@ubuntu.com>
Uncompressed Size: 36.9 k
Depends: ubuntu-restricted-addons
Recommends: gstreamer0.10-plugins-ugly-multiverse, ttf-mscorefonts-installer,
            unrar, gstreamer0.10-plugins-bad-multiverse, libavcodec-extra-52,
            libmp4v2-0
Description: Commonly used restricted packages for Ubuntu
 This package depends on some commonly used packages in the Ubuntu multiverse
 repository. 
 
 Installing this package will pull in support for MP3 playback and decoding,
 support for various other audio formats (GStreamer plugins), Microsoft fonts,
 Java runtime environment, Flash plugin, LAME (to create compressed audio
 files), and DVD playback. 
 
 Please note that this does not install libdvdcss2, and will not let you play
 encrypted DVDs. For more information, see
 https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs 
 
 Please also note that packages from multiverse are restricted by copyright or
 legal issues in some countries. See http://www.ubuntu.com/ubuntu/licensing for
 more information.



```If you just want flash:
```
sudo apt-get install flashplugin-installer
```Or you can open Ubuntu Software center and type flash in upper right box and install.
Or you can go to Synaptics package manager and type flash in upper right box to install.
There are quite a few ways to install packages in Ubuntu. Find what you like best.

---

