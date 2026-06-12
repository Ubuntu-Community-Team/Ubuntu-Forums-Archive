---
title: "flash player problem"
date: 2009-03-27
forum: Multimedia Software
---

### Post by ssj3g0ku on 2009-03-27
i cant install flash player
i tried installing the deb from adobe for ubuntu 8.04 i have this: "Dependency is not satisfiable: libpango1.0-0"
i tried to convert the rpm to deb but when i start firefox nothing..
and the same i did this and i get 
```
sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  java-common libboost-thread1.34.1 libboost-date-time1.34.1
Use 'apt-get autoremove' to remove them.
Suggested packages:
  konqueror-nsplugins ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-nonfree
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/18.7kB of archives.
After this operation, 168kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 116812 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_9.0.124.0ubuntu2_i386.deb) ...
Setting up flashplugin-nonfree (9.0.124.0ubuntu2) ...
Downloading...
--02:42:32--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 88.221.210.70
Connecting to fpdownload.macromedia.com|88.221.210.70|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
02:42:32 ERROR 404: Not Found.

download failed
The Flash plugin is NOT installed.


```

and even on synaptic i got the same thing ..
how can i do ?

---

### Post by change_mode on 2009-03-27
Looks like a server error (?)

---

### Post by questworld on 2009-03-27
open up a terminal and execute following commands 

1 sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list
2 wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
3 sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libavcodec-unstripped-51 libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar 

Worked for me.

---

### Post by ssj3g0ku on 2009-03-27
not working
```
 sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libavcodec-unstripped-51 libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnash is not installed, so not removed
Package gnash-common is not installed, so not removed
Package libflashsupport is not installed, so not removed
Package mozilla-plugin-gnash is not installed, so not removed
Package swfdec-mozilla is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gstreamer0.10-ffmpeg is already the newest version.
gstreamer0.10-plugins-bad is already the newest version.
gstreamer0.10-plugins-bad-multiverse is already the newest version.
gstreamer0.10-plugins-ugly is already the newest version.
gstreamer0.10-plugins-ugly-multiverse is already the newest version.
gstreamer0.10-pitfdll is already the newest version.
E: Couldn't find package libavcodec-unstripped-51

```

---

### Post by hansdown on 2009-03-27
Hi ssj3g0ku.

What distro are you using?

Your first terminal output suggested konqueror.

---

### Post by kruegger on 2009-03-27
You might try to change the mirror the distro gets the packages from. It can be done with Synaptic:
Repositories> Setup> Ubuntu Software> Download from> Choose another server and run a proximity test.

It might work!!!.

---

### Post by gandaran on 2009-03-28
> **ssj3g0ku said:**
> i cant install flash player
i tried installing the deb from adobe for ubuntu 8.04 i have this: "Dependency is not satisfiable: libpango1.0-0"
i tried to convert the rpm to deb but when i start firefox nothing..
and the same i did this and i get 
```
sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  java-common libboost-thread1.34.1 libboost-date-time1.34.1
Use 'apt-get autoremove' to remove them.
Suggested packages:
  konqueror-nsplugins ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-nonfree
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/18.7kB of archives.
After this operation, 168kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 116812 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_9.0.124.0ubuntu2_i386.deb) ...
Setting up flashplugin-nonfree (9.0.124.0ubuntu2) ...
Downloading...
--02:42:32--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 88.221.210.70
Connecting to fpdownload.macromedia.com|88.221.210.70|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
02:42:32 ERROR 404: Not Found.

download failed
The Flash plugin is NOT installed.


```

and even on synaptic i got the same thing ..
how can i do ?

this error is due to two things, your system is not fully updated and you need to get the new apt package list.
install all updates and run **sudo apt-get update** to retrieve the new package list.
remove completely the broken flashplugin-nonfree package before running sudo apt-get update only then reinstall flash.
there are many ways to install flash, if one doesn't work try another, installing flash manually always works in any situation, see [this]("http://gandaran.com.sapo.pt/ubuntu.html").

---

### Post by questworld on 2009-03-28
ya gandaran is right. U need to update ur repository. However just incase u r wondering if u have the right repository then the answer is yes. The first two command makes sure u have it. 

Also make sure ur internet connect is nt dropping our whilst installing. If u want to go manual then the package that u could not download is here [http://packages.ubuntu.com/intrepid/libavcodec-unstripped-51]("http://packages.ubuntu.com/intrepid/libavcodec-unstripped-51")

---

### Post by gandaran on 2009-03-28
> **ssj3g0ku said:**
> not working
```
 sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libavcodec-unstripped-51 libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnash is not installed, so not removed
Package gnash-common is not installed, so not removed
Package libflashsupport is not installed, so not removed
Package mozilla-plugin-gnash is not installed, so not removed
Package swfdec-mozilla is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gstreamer0.10-ffmpeg is already the newest version.
gstreamer0.10-plugins-bad is already the newest version.
gstreamer0.10-plugins-bad-multiverse is already the newest version.
gstreamer0.10-plugins-ugly is already the newest version.
gstreamer0.10-plugins-ugly-multiverse is already the newest version.
gstreamer0.10-pitfdll is already the newest version.
E: Couldn't find package libavcodec-unstripped-51

```
libavcodec-unstripped-51 is for ubuntu 8.10 and can only be found in ubuntu 8.10 repositories, if you running ubuntu 8.04 you don't need it, it may conflict with another package, don't install it!

---

### Post by ssj3g0ku on 2009-03-28
should i install all the updates for ubuntu ?
last time i dit that after install on next reboot i fount that compiz
was not working anymore..

---

### Post by gandaran on 2009-03-28
> **ssj3g0ku said:**
> should i install all the updates for ubuntu ?
last time i dit that after install on next reboot i fount that compiz
was not working anymore..
if you are running ubuntu 8.04 then yes you have to update, there have been a lot of system changes, those flash package won't install/work without the updates.
if you don't want to update then install flash manually, this is the only way to get flash working, see the link in my first post how to install flash from the adobe tar.gz package.

---

### Post by ssj3g0ku on 2009-03-28
> **ssj3g0ku said:**
> should i install all the updates for ubuntu ?
last time i dit that after install on next reboot i fount that compiz
was not working anymore..

it worked PERFECT
i installed all the updates
after restart i got the deb from adobe and i installed
perfect
thanks :)

---

