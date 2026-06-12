---
title: "Divx"
date: 2009-05-11
forum: Multimedia Software
---

### Post by ali999 on 2009-05-11
hi...just wondering if someone knows how to get divx to work on web players. i have totem as my only media player so am interested to know a solution that works with that. basically i am trying to get divx streams to work so i don't have to actually download the videos. i downloaded the tar ball from here [http://download.divx.com/labs/divx61...cc4.0.1.tar.gz](http://download.divx.com/labs/divx61...cc4.0.1.tar.gz)
and installed it successfully but the online streaming still does not work. any ideas? 

thanks

---

### Post by lovinglinux on 2009-05-11
Gecko-mediaplayer has DivX support. Follow [this tutorial](http://ubuntuforums.org/showthread.php?t=766683).

---

### Post by ali999 on 2009-05-11
i was hoping that there be some way to make totem play them...don't particularly wanna have to download another media player just for this

---

### Post by lovinglinux on 2009-05-11
> **ali999 said:**
> i was hoping that there be some way to make totem play them...don't particularly wanna have to download another media player just for this

Is just another frontend for mplayer with a Firefox plugin, which can play DivX, Quicktime, RealPlayer and WMV. So I think is a good option to play most of the videos you will find on the web.

---

### Post by psyke83 on 2009-05-12
Honestly, don't bother with the divx tarballs, there are much better (and cleaner) ways to gain support for multiple codecs in Ubuntu.

[LIST=1]
[*]Uninstall/remove any software or files installed from the divx tarball you previously used - it's not necessary and may cause conflicts. Refer to the install instructions; you may need to invoke "sudo make uninstall" in the working directory.
[*]Enable the Medibuntu repository according to the official method on the [wiki]("https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories") page.
[*]Install the ubuntu-restricted-extras metapackage (which installs many different codecs for gstreamer/totem), the w32codecs package, and the libdvdcss2 package for protected DVD playback support:
```
$ sudo apt-get install ubuntu-restricted-extras w32codecs libdvdcss2
```
[/LIST]

Totem (and therefore the Totem web plugin) will now support all codecs that are supported in ffmpeg *and* within the w32codecs package, including - but not limited to - divx.

---

### Post by RubenK on 2009-05-23
I get:
```
E: Package w32codecs has no installation candidate
```
&
```
E: Package libdvdcss2 has no installation candidate
```
I already have the restricted extra's installed.

EDIT: I made a stupid mistake: forgot to add the GPG key...

---

