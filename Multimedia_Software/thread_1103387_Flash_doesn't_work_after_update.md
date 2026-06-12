---
title: "Flash doesn't work after update"
date: 2009-03-22
forum: Multimedia Software
---

### Post by tegnoto89 on 2009-03-22
I just ran an update, I'm not sure if flash was included, but now flash won't work.  I can't watch youtube videos, etc.  I ran ```
sudo apt-get install flashplugin-nonfree
```

But alas, it said it was already the newest version.  I uninstalled it, and when I tried to reinstall it, this is what happened:

```
tom@tom-laptop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic libsmokeqt1 libjack0.100.0-0 ruby1.8
  libfluidsynth1 libqt0-ruby1.8 skype-common libruby1.8 ladcca2
  linux-headers-2.6.24-19 libnss3-0d
Use 'apt-get autoremove' to remove them.
Suggested packages:
  konqueror-nsplugins libflashsupport ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-nonfree
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/18.8kB of archives.
After this operation, 168kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 136790 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124.0ubuntu2_i386.deb) ...
Setting up flashplugin-nonfree (10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124.0ubuntu2) ...
Downloading...
--17:37:48--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 69.192.2.70
Connecting to fpdownload.macromedia.com|69.192.2.70|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
17:37:49 ERROR 404: Not Found.

download failed
The Flash plugin is NOT installed.

```

When I tried the same command a second time, it said it was already the newest version:

```
tom@tom-laptop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic libsmokeqt1 libjack0.100.0-0 ruby1.8
  libfluidsynth1 libqt0-ruby1.8 skype-common libruby1.8 ladcca2
  linux-headers-2.6.24-19 libnss3-0d
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

I also tried uninstalling and installing the .deb file from the website; also didn't work.

Any thoughts?

---

### Post by tegnoto89 on 2009-03-22
Solved!  Installed the 64bit flash, works perfectly.  AND I was having a problem with full-screen videos being choppy- it solved that too!  :D

---

### Post by mefistofeles666 on 2009-03-22
how did you Install the 64bit flash, I'm having the same problem. but I'm using  8.10 32 bits, I think. it's a  laptop from 5 yrs ago, so I'm sure it can't really support 64 bits.

---

### Post by tegnoto89 on 2009-03-23
[http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

---

