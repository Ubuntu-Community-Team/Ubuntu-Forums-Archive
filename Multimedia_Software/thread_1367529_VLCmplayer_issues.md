---
title: "VLC/mplayer issues"
date: 2009-12-29
forum: Multimedia Software
---

### Post by davidself1001 on 2009-12-29
After upgrading to 9.10 i can play my vid files (avi,mpeg,wmv,flv) with avidmux but not with other players (eg VLC, mplayer, Totem_).  I have tried the procedures outlined in the comp help thread but did not help.  Not sure if my Medibuntu key is correct.  Followed instructions but not sure how to tell if it worked.  I am on a x64 platform Ubuntu.  I did get one error while performing the installation step.  I get a incompatible Java RTE lib while trying to load the 32 bit lib as stated in the install instruction.  It says it is looking for a vers 15.x.x file but the installed JRTE is a vers 16.x.x file.  Help>

sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs ia32-sun-java6-bin icedtea6-plugin libmp3lame0 non-free-codecs openjdk-6-jre unrar
[sudo] password for david: 
Sorry, try again.
[sudo] password for david: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnash is not installed, so not removed
Package gnash-common is not installed, so not removed
Package libflashsupport is not installed, so not removed
Package mozilla-plugin-gnash is not installed, so not removed
Package swfdec-mozilla is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
alsa-oss is already the newest version.
faac is already the newest version.
faad is already the newest version.
gstreamer0.10-ffmpeg is already the newest version.
gstreamer0.10-plugins-bad is already the newest version.
gstreamer0.10-plugins-ugly is already the newest version.
gstreamer0.10-plugins-ugly-multiverse is already the newest version.
ia32-libs is already the newest version.
libmp3lame0 is already the newest version.
non-free-codecs is already the newest version.
unrar is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ia32-sun-java6-bin: Depends: sun-java6-jre (= 6-15-1) but 6-16-0ubuntu1.9.04 is to be installed
E: Broken packages

---

### Post by doas777 on 2009-12-29
first install the ubuntu-restricted-extras package (or reinstall if already present), and that will take care of the java dependency.

Edit: wait, you are uninstalling all those packages? why?

just install mediubuntu, then install the ubuntu-restricted-extras. done.
just paste in this:
```

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update; sudo apt-get install ubuntu-restricted-extras

```

---

### Post by davidself1001 on 2009-12-29
Did that and it showed that i had the latest version already installed.

---

### Post by doas777 on 2009-12-29
> **davidself1001 said:**
> Did that and it showed that i had the latest version already installed.
I edited my post after rereading your command. there is no reason to remove those packages that I can tell (in fact the error you are getting is telling you that you don't have java installed but are trying to remove it anyway).

just run the command i added and it should take care of the rest. 
post back if not

---

### Post by davidself1001 on 2009-12-29
Still no video from VLC.  I get audio but no video.

---

### Post by mc4man on 2009-12-29
open up synaptic, search ffmpeg, and see what version of the ffmpeg libs are installed (libavcodec thru libswscale.

Basically you want to re-install them so you have either just the plain versions or the extra versions (you don't particularly want the unstripped versions installed

If you added medibuntu then they offer a slightly better extra version of those libs

So just mark all the **extra versions** for install and apply (if you happen to lose a  player or plugin just re-install after.

Don't re-install ubuntu restricted extras anymore - it will remove the extra versions of the ffmpeg libs. (it's misconfigured in karmic

---

### Post by doas777 on 2009-12-29
> **davidself1001 said:**
> Still no video from VLC.  I get audio but no video.
that sounds like a vid card driver issue to me what kind of card/driver do you have?

---

### Post by davidself1001 on 2009-12-29
I have libavcodec-extra-52 v4:0.5, libavformat52 v4:0.5.  Those are the only two libs selected.  No others loaded.

---

### Post by SuperSonic4 on 2009-12-29
> **davidself1001 said:**
> Still no video from VLC.  I get audio but no video.

Could also be a dodgy video file. Have you tried changing VLC's output to X11?

---

### Post by davidself1001 on 2009-12-29
X11 no help.  my video card info is in my signature below.

---

### Post by davidself1001 on 2009-12-29
~$ ffmpeg
ffmpeg: error while loading shared libraries: libx264.so.67: cannot open shared object file: No such file or directory

Get the above error when trying to execute ffmpeg.  do i need the libx264.so.67 file?  If so, where is it?

---

### Post by SuperSonic4 on 2009-12-29
x264 can be obtained

[list=A]
[*]From the repos (may be in a codec package or the like)
[*]From the [videolan archive]("ftp://ftp.videolan.org/pub/videolan/x264/snapshots/")
[*]From [git]("http://wiki.videolan.org/Git") (only the latest version) 
[/list]

For B it is best to pick the repo version unless you're compiling the bleeding edge vlc/ffmpeg/mplayer/mencoder.

If you choose B or C it may be best to install it in /opt/x264 (you'll have to make this directory) or /usr/local as not to conflict with repo x264 and it's deps

---

### Post by davidself1001 on 2009-12-29
Resolved.  Reloading x264 lib cause ffmpeg and vlc to be removed for some reason.  When i reloaded them all worked.

Thanks for the help.

---

