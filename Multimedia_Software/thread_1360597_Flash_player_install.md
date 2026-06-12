---
title: "Flash player install"
date: 2009-12-21
forum: Multimedia Software
---

### Post by mr.b296 on 2009-12-21
Hello. I just installed ubuntu 9.04 and would like to know how to install a flash player so that i can watch videos online. i tried to install the Adobe player, but still can't watch a video from youtube.

---

### Post by wojox on 2009-12-21
[Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")

```

sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree

```

---

### Post by mr.b296 on 2009-12-21
i tried pasting the code, and this is what happened:

ubuntu@ubuntu:~$ sudo apt-get remove swfdec-mozilla
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package swfdec-mozilla
ubuntu@ubuntu:~$ sudo apt-get remove mozilla-plugin-gnash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package mozilla-plugin-gnash
ubuntu@ubuntu:~$ sudo apt-get remove adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  adobe-flashplugin
0 upgraded, 0 newly installed, 1 to remove and 267 not upgraded.
After this operation, 10.4MB disk space will be freed.
Do you want to continue [Y/n]? 
Abort.
ubuntu@ubuntu:~$

---

### Post by wojox on 2009-12-21
Probably need to 267 not upgraded first?

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by wojox on 2009-12-21
And enter yes to remove the plugin you installed directly from adobe and install the one from the repositories.

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by mr.b296 on 2009-12-21
when that upgrade is done, do i do the flash code?

---

### Post by wojox on 2009-12-21
Ya, but run:

```

sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree

```

Just incase it added mozilla or swfdec on the update and to purge the adobe-flashplugin. You good leave out: **sudo apt-get install flashplugin-nonfree** and run :

```

sudo apt-get install ubuntu-restricted-extras

```
 and get a bunch of codecs and flash and other wonderful things.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by mr.b296 on 2009-12-21
wow! thanks so much! i don't want to be a major pain in the ***, but, i can't find my built-in camera, either. Any idea how to locate that?

---

### Post by wojox on 2009-12-21
Try cheese it's what I use for my camera, but it's a usb plug. Not sure about built in.

```
sudo apt-get install cheese
```

---

### Post by mr.b296 on 2009-12-21
ok...there was a problem. i didn't mention to you that i'm running ubuntu on my computer from a 4GB thumbdrive. apparently there's not enough room?
Unpacking replacement gnome-applets-data ...
dpkg: error processing /var/cache/apt/archives/gnome-applets-data_2.26.1-0ubuntu1_all.deb (--unpack):
 failed in buffer_write(fd) (10, ret=-1): backend dpkg-deb during `./usr/share/gnome/help/stickynotes_applet/fi/figures/stickynote-right-menu-lock.png': No space left on device
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace libpulse0 1:0.9.14-0ubuntu20 (using .../libpulse0_1%3a0.9.14-0ubuntu20.3_i386.deb) ...
Unpacking replacement libpulse0 ...
Preparing to replace gstreamer0.10-pulseaudio 0.10.14-1 (using .../gstreamer0.10-pulseaudio_0.10.14-1ubuntu0.1_i386.deb) ...
Unpacking replacement gstreamer0.10-pulseaudio ...
Preparing to replace gstreamer0.10-plugins-good 0.10.14-1 (using .../gstreamer0.10-plugins-good_0.10.14-1ubuntu0.1_i386.deb) ...

(gconftool-2:8853): GConf-WARNING **: Could not flush file '/var/lib/gconf/defaults/%gconf-tree-ku.xml.new' to disk: No space left on device

(gconftool-2:8853): GConf-WARNING **: Could not flush file '/var/lib/gconf/defaults/%gconf-tree-xh.xml.new' to disk: No space left on device

(gconftool-2:8853): GConf-WARNING **: Could not flush file '/var/lib/gconf/defaults/%gconf-tree-tl.xml.new' to disk: No space left on device

(gconftool-2:8853): GConf-WARNING **: Could not flush file '/var/lib/gconf/defaults/%gconf-tree-fil.xml.new' to disk: No space left on device

(gconftool-2:8853): GConf-WARNING **: Could not flush file '/var/lib/gconf/defaults/%gconf-tree-dz.xml.new' to disk: No space left on device

(gconftool-2:8853): GConf-WARNING **: Could not flush file '/var/lib/gconf/defaults/%gconf-tree-mg.xml.new' to disk: No space left on device

(gconftool-2:8853): GConf-WARNING **: Could not flush file '/var/lib/gconf/defaults/%gconf-tree-ms.xml.new' to disk: No space left on device

(gconftool-2:8853): GConf-WARNING **: Could not flush file '/var/lib/gconf/defaults/%gconf-tree-is.xml.new' to disk: No space left on device

(gconftool-2:8853): GConf-WARNING **: Could not flush file '/var/lib/gconf/defaults/%gconf-tree-eo.xml.new' to disk: No space left on device

(gconftool-2:8853): GConf-WARNING **: Could not flush file '/var/lib/gconf/defaults/%gconf-tree-et.xml.new' to disk: No space left on device

(gconftool-2:8853): GConf-WARNING **: Could not flush file '/var/lib/gconf/defaults/%gconf-tree-az.xml.new' to disk: No space left on device

(gconftool-2:8853): GConf-WARNING **: Could not flush file '/var/lib/gconf/defaults/%gconf-tree-en_CA.xml.new' to disk: No space left on device

(gconftool-2:8853): GConf-WARNING **: Could not flush file '/var/lib/gconf/defaults/%gconf-tree-sr@Latn.xml.new' to disk: No space left on device

(gconftool-2:8853): GConf-WARNING **: Could not flush file '/var/lib/gconf/defaults/%gconf-tree-ka.xml.new' to disk: No space left on device

(gconftool-2:8853): GConf-WARNING **: Failed to write "/var/lib/gconf/defaults/%gconf-tree.xml": Error writing file "/var/lib/gconf/defaults/%gconf-tree.xml.new": No space left on device

Error syncing configuration data: Failed to write some configuration data to disk
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
dpkg: ... it looks like that went OK.
dpkg: unrecoverable fatal error, aborting:
 unable to flush updated status of `gstreamer0.10-plugins-good': No space left on device
E: Sub-process /usr/bin/dpkg returned an error code (2)
ubuntu@ubuntu:~$

---

### Post by dewmanstl on 2009-12-21
Yep...It ran out of room alright.....Get a bigger drive.... :P

---

### Post by llawwehttam on 2009-12-22
I kinda guessed you were doing that. ubuntu@ubuntu lol

Play.com has cheap usb drives

---

