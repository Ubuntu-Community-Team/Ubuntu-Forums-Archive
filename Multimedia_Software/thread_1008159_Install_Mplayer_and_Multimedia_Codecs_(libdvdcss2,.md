---
title: "Install Mplayer and Multimedia Codecs (libdvdcss2,w32codecs,w64codecs) in Ubuntu 8.10"
date: 2008-12-11
forum: Multimedia Software
---

### Post by slayer^_^ on 2008-12-11
**Installing most of the codecs you need with a single package**

The package **ubuntu-restricted-extras** installs most of the codecs (except the ones below) you need.
To install it, you need to add the following lines to /etc/apt/sources.list file or you need to make sure you have enabled Universe and multiverse repositories Using GUI.

    ```
sudo gedit /etc/apt/sources.list
```

Make sure you have the following two lines save and exit your file

    ```
deb http://archive.ubuntu.com/ubuntu intrepid universe multiverse
deb-src http://archive.ubuntu.com/ubuntu intrepid universe multiverse
```

Now you need to run the following command to update the source list

  ```
sudo apt-get update
```

Install mplayer using the following command

    ```
sudo apt-get install ubuntu-restricted-extras
```

_**If you use a 64 bit version of Ubuntu**_ probably you would like to install a native 64 bit version of the flash player (that is far more stable than the version you install with the package flasplugin-nonfree ,  which is a 32 bit version of it emulated with nspluginwrapper)

It is very simple:


1) Download the 64 bit flash 10 plugin from here, and save it on the desktop: [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz)

this is the link of the adobe labs download page for 64 bit flash player (just if you wanna check if new versions of it have been released...)

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

if the link above should not work try downloading by this link (a bit elder version, though...)

[http://linux.softpedia.com/get/Internet/HTTP-WWW-/Adobe-Flash-Player-for-64-bit-Linux-42958.shtml](http://linux.softpedia.com/get/Internet/HTTP-WWW-/Adobe-Flash-Player-for-64-bit-Linux-42958.shtml)

2) Remove previous existing versions of flash player: type in terminal, string by string:

```

sudo apt-get remove --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
sudo rm -f /usr/lib/iceweasel/plugins/npwrapper.libflashplayer.so
sudo rm -f /usr/lib/firefox/plugins/npwrapper.libflashplayer.so
sudo rm -f /var/lib/flashplugin-nonfree//npwrapper.libflashplayer.so
sudo rm -f ~/.mozilla/plugins/npwrapper.libflashplayer.so 

```

3) Open the terminal and execute your file manager with root privileges, for example in gnome (ubuntu):

```
gksu nautilus
```

4) Enter the /usr/lib/mozilla/plugins folder

5) Extract the package you downloaded on the desktop and drag and drop the "libflashplayer.so" file from the desktop to the folder.

6) Restart Firefox, open youtube and be sure the plugin works... it should ;) and, you know what? no more flash crashes or grey windows on 64 bit Ubuntu !!!

_If you're using the Opera browser:_

Do this **_only_** if, after having done point 4 and 5, you can't experience flash in Opera

7) Restart Opera and give a try to the youtube website. if flash doesn't work go forward:

8 ) Enter the /usr/lib/opera/plugins folder

9) Extract the package you downloaded on the desktop and drag and drop the "libflashplayer.so" file from the desktop to the folder.

6) Reboot Opera, open youtube and be sure the plugin works... it should ;) and, you know what? no more flash crashes or grey windows on 64 bit Ubuntu !!!

**Install Mplayer in Ubuntu 8.10 (Intrepid Ibex)**

MPlayer is a movie and animation player that supports a wide range of codecs and file formats, including MPEG 1/2/4,DivX 3/4/5, Windows Media 7/8/9, RealAudio/Video up to 9, Quicktime 5/6, and Vivo 1/2. It has many MX/SSE (2)/3Dnow(Ex) optimized native audio and video codecs, but allows using XAnim&#8217;s and RealPlayer&#8217;s binary codec plugins, and Win32 codec DLLs. It has basic VCD/DVD playback functionality, including DVD subtitles, but supports many text- based subtitle formats too. For video output, nearly every existing interface is supported. It&#8217;s also able to convert any supported files to raw/divx/mpeg4 AVI (pcm/mp3 audio), and even video grabbing from V4L devices.

You need to add the following lines to /etc/apt/sources.list file or you need to make sure you have enabled Universe and multiverse repositories Using GUI.

    ```
sudo gedit /etc/apt/sources.list
```

Make sure you have the following two lines save and exit your file

    ```
deb http://archive.ubuntu.com/ubuntu intrepid universe multiverse
deb-src http://archive.ubuntu.com/ubuntu intrepid universe multiverse
```

Now you need to run the following command to update the source list

  ```
sudo apt-get update
```

Install mplayer using the following command

    ```
sudo apt-get install mplayer
```

If you want to open mplayergo to Applications&#8212;>Sound&Video&#8212;> Mplayer Movie Player


**Install Smplayer (Mplayer Front-end)**

Qt Mplayer front-end, with basic features like playing videos, DVDs, and VCDs to more advanced features like support for MPlayer filters and more. One of the most interesting features of SMPlayer: it remembers the settings of all files you play. So you start to watch a movie but you have to leave&#8230; don&#8217;t worry, when you open that movie again it will resume at the same point you left it, and with the same settings: audio track, subtitles, volume&#8230;

    ```
sudo apt-get install smplayer
```

Install smplayer themes using the following command

    ```
sudo apt-get install smplayer-themes
```


**Install libdvdcss2 and w32 video codecs in Ubuntu 8.10 (Intrepid Ibex)**

Support for WMV, RealMedia and other formats has been bundled into the w32codecs package. This package is not available from the Ubuntu repositories due to licensing and legal restrictions.

For Ubuntu 8.10 (Intrepid Ibex) Users run the following command

    ```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

Then, add the GPG Key using the following commands

    ```
sudo apt-get update
```

    ```
sudo apt-get install medibuntu-keyring
```

    ```
sudo apt-get update
```

Use the following command

    ```
sudo apt-get install non-free-codecs
```

Using above download locations you can install most of the non-free mutimedia codecs for ubuntu.

You can use the Medibuntu repository to install non-free programs like **Skype** also.

**Mplayer Plugin for Firefox**

If you want to install Mplayer with plug-in for Mozilla Firefox run the following command

    ```
sudo apt-get install mozilla-mplayer
```

**Streaming .wmv videos in Firefox**

For being able to view streaming .wmv videos in Firefox, you just need a plugin called "MediaPlayerConnectivity". It, actually, allows you to launch embed video of website in an external application with a simple click. You can find it here:

[https://addons.mozilla.org/it/firefox/addon/446](https://addons.mozilla.org/it/firefox/addon/446)


DISCLAIMER: all the informations above are taken from the website **_[www.ubuntugeek.com](www.ubuntugeek.com)_**

---

### Post by Izek on 2008-12-12
Well, thanks for this, much easier in my opinion than certain other threads. *ahem*

---

### Post by slayer^_^ on 2008-12-13
you're welcome... ;)

---

### Post by Izek on 2008-12-14
Just so you know, you can edit the line;
```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

to
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

and then follow the rest of the codec instructions for hardy.

---

### Post by SuperSonic4 on 2008-12-14
Isn't this just condensed from the sticky?
A good topic though, especially if you only want codecs

Kubuntu users should use kate ```
sudo kate /etc/apt/sources.list
```

I use nano for editing my sources list :p which works on all variants: [code]sudo nano /etc/apt/sources.list

---

### Post by Craig73 on 2008-12-22
Would there be any reason that I can't use the mplayer-plugin for OGG and WAV files?  In the ~/.mozilla/firefox/?.default/pluginreg.dat it would seem to suggest I should be able to, but I don't have it as an option in Firefox preferences (Just Totem web browsing plugin and Movie Player, which is kind of redundant)

---

### Post by slayer^_^ on 2009-01-04
are you sure you did everything right?

try doing again:

```
sudo apt-get install mozilla-mplayer
```

and let me know if ti works or not...

---

### Post by andrew.46 on 2009-01-05
Hi,

> **Izek said:**
> Well, thanks for this, much easier in my opinion than certain other threads. *ahem*

I agree! Threads like this one:

[Howto] Install the svn Mplayer under Intrepid Ibex
[http://ubuntuforums.org/showthread.php?t=1024592](http://ubuntuforums.org/showthread.php?t=1024592)

are way too much and go against the general Ubuntu prinicple of ease of use and ease of installation.

Andrew

---

### Post by Proteusiq on 2009-01-05
I still can not play wmv direct on my firefox! I can see that it downloads and have mplayer, yet when I play it is just blank!

---

### Post by slayer^_^ on 2009-01-05
Try with this addon for firefox... It, actually, allows you to launch embed video of website in an external application with a simple click.

[https://addons.mozilla.org/it/firefox/addon/446](https://addons.mozilla.org/it/firefox/addon/446)

and let me know if it works...

---

### Post by Izek on 2009-02-18
Delete Post

---

