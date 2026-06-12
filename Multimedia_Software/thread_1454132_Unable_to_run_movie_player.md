---
title: "Unable to run movie player"
date: 2010-04-14
forum: Multimedia Software
---

### Post by 123sarang on 2010-04-14
I have installed ubuntu 9.10 day before yesterday on my laptop Dell studio, When i try to play and video or audio in Application -> Sounds & Vedio -> Movie Player its unable to play anything and gives an error message as not supported. 
Do i need to install any external package?

Thanks in advance

---

### Post by Odd-rationale on 2010-04-14
You probably need to install some media codecs.

See the following link for more information:

[https://help.ubuntu.com/9.10/musicvideophotos/C/video-playback.html](https://help.ubuntu.com/9.10/musicvideophotos/C/video-playback.html)

---

### Post by lidex on 2010-04-14
More here:
[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by 123sarang on 2010-04-15
Thanks for your help
I have install Ubuntu_restricted_extras_offline_installer_ubuntu_9.10 through which now am able to play audio and video but now the sound of my laptop is very low.
Do i need to install some more packages for sound drivers.

---

### Post by lidex on 2010-04-15
Check your levels in alsamixer. From a terminal="Applications>Accessories>Terminal", enter this command:
```
alsamixer
```
Or try gnome-alsamixer, if installed, in the "Sound and Video" menu. To install use this:
```
sudo apt-get install gnome-alsamixer
```

---

### Post by garvinrick4 on 2010-04-15
Codecs are in the package "ubuntu-restricted-extras"

Make sure in Software Sources in System/Admin that your partners repository is
installed in Other Software tab I believe and your multiverse in ubuntu software.

Then just Code:

sudo apt-get install ubuntu-restricted-extras


Gives you all your codecs, Java if needed, true type fonts if needed, lots of stuff if really.
The first thing I do on any install is do my partners repository and install ubuntu-restricted-extras.
As you see below it installs all the gstreamers you need for MPlayer.

rick@rick-laptop:~$ aptitude show ubuntu-restricted-extras
Package: ubuntu-restricted-extras
State: installed
Automatically installed: no
Version: 39
Priority: optional
Section: multiverse/metapackages
Maintainer: Michael Vogt <michael.vogt@ubuntu.com>
Uncompressed Size: 32.8k
Recommends: gstreamer0.10-plugins-ugly, gstreamer0.10-plugins-ugly-multiverse,
            ttf-mscorefonts-installer, flashplugin-installer, unrar,
            gstreamer0.10-plugins-bad, gstreamer0.10-plugins-bad-multiverse,
            gstreamer0.10-ffmpeg, libavcodec-extra-52, icedtea6-plugin,
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
 [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) 
 
 Please also note that packages from multiverse are restricted by copyright or
 legal issues in some countries. See [http://www.ubuntu.com/ubuntu/licensing](http://www.ubuntu.com/ubuntu/licensing) for
 more information.

rick@rick-laptop:~$

---

