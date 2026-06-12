---
title: "mplayer won't install"
date: 2009-01-31
forum: Multimedia Software
---

### Post by Silvernail on 2009-01-31
I am  trying to install mplayer with 
```
sudo apt-get install mplayer
```
and I get this
> 
The following packages have unmet dependencies:
  mplayer: Depends: libasound2 (> 1.0.17) but 1.0.15-3ubuntu4 is to be installed
           Depends: libggi2 (>= 1:2.2.2) but 1:2.2.1-5ubuntu1 is to be installed
           Depends: libgtk2.0-0 (>= 2.14.1) but 2.12.9-3ubuntu5 is to be installed
           Depends: libmad0 (>= 0.15.1b-3) but 0.15.1b-2.1ubuntu1 is to be installed
           Depends: libmp3lame0 (>= 3.98) but it is not installable
           Depends: libopenal1 (>= 1:1.3.253) but it is not installable
           Depends: libpango1.0-0 (>= 1.21.6) but 1.20.5-0ubuntu1 is to be installed
           Depends: libspeex1 (>= 1.2~beta3-1) but 1.1.12-3ubuntu0.8.04.1 is to be installed
           Depends: libx264-59 (>= 1:0.svn20080408) but it is not installable
E: Broken packages
d
I also notice that package manager in the daily updates has 'mplayer' and 'mencoder' unticked and grayed out. Been this way for a long time.

What todo?

---

### Post by redroad55 on 2009-01-31
Try this How to ..[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

> -PART 2/5, AUDIO & VIDEO STREAMING--


OPTION 1, GECKO MEDIA PLAYER


Gecko Media Player is similar to mplayerplug-in, as it uses GNOME MPlayer to play virtually all formats, but works well without the need of adding any configuration options. Installation and setup is simple, just copy and paste the following commands into the terminal:

sudo apt-get remove kaffeine-mozilla mozilla-helix-player mozilla-mplayer mozilla-plugin-vlc totem-mozilla xine-plugin

sudo apt-get install gnome-mplayer gecko-mediaplayer

or if you're running Kubuntu, you might want the KDE front-end for MPlayer/Xine:

sudo apt-get install kmplayer gecko-mediaplayer

Restart your web browser and test the plug-in here. If you have problems viewing the trailers, please refer to the troubleshooting section.

Note: Please REBOOT if you are not carrying on with the rest of the howto, as you have made lot's of changes to your system and could have some strange problems until you start a fresh session. If you still have problems after rebooting, please read the troubleshooting section at the bottom.

Hope this helps .. Post back with any results or questions .. best to you ..

---

### Post by Silvernail on 2009-01-31
I did:
> dave@gadabout:~$  sudo apt-get remove kaffeine-mozilla mozilla-helix-player mozilla-mplayer mozilla-plugin-vlc totem-mozilla xine-plugin
[sudo] password for dave: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package kaffeine-mozilla is not installed, so not removed
Package mozilla-helix-player is not installed, so not removed
Package mozilla-plugin-vlc is not installed, so not removed
Package xine-plugin is not installed, so not removed
The following packages were automatically installed and are no longer required:
  skype-common
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  mozilla-mplayer totem-mozilla
0 upgraded, 0 newly installed, 2 to remove and 2 not upgraded.
After this operation, 1925kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 214298 files and directories currently installed.)
Removing mozilla-mplayer ...
Removing totem-mozilla ...
dave@gadabout:~$ 

Then I did;

> 

dave@gadabout:~$ sudo apt-get install gnome-mplayer gecko-mediaplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  skype-common
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  gecko-mediaplayer gnome-mplayer
0 upgraded, 2 newly installed, 0 to remove and 2 not upgraded.
Need to get 278kB of archives.
After this operation, 1110kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse gnome-mplayer 0.6.0-0ubuntu2 [110kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse gecko-mediaplayer 0.6.0-0ubuntu1.1 [168kB]
Fetched 278kB in 1s (147kB/s)          
Selecting previously deselected package gnome-mplayer.
(Reading database ... 214208 files and directories currently installed.)
Unpacking gnome-mplayer (from .../gnome-mplayer_0.6.0-0ubuntu2_i386.deb) ...
Selecting previously deselected package gecko-mediaplayer.
Unpacking gecko-mediaplayer (from .../gecko-mediaplayer_0.6.0-0ubuntu1.1_i386.deb) ...
Setting up gnome-mplayer (0.6.0-0ubuntu2) ...

Setting up gecko-mediaplayer (0.6.0-0ubuntu1.1) ...




Then I rebooted and tried to play a file and got:
> 
dave@gadabout:~/Videos/tape-credits/rizzolo/clips$ mplayer rizzolo1.mpg 
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Celeron(R) M CPU        520  @ 1.60GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing rizzolo1.mpg.
Win32 LoadLibrary failed to load: avisynth.dll, /usr/lib/win32/avisynth.dll, /usr/local/lib/win32/avisynth.dll


Exiting... (End of file)
dave@gadabout:~/Videos/tape-credits/rizzolo/clips$ 


I have stand alone 'Totem, Vlc, Kaffeine' installed. Does that make a difference from the mozilla versions?

Am I missing some 'codecs'? Are corrupted?
Thanks
Dave

---

### Post by redroad55 on 2009-01-31
Do you have medibuntu repository in your software sources ?If not go here [https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories]("https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories")

Also go to software sources and under updates check unsuported updates (back ports)

---

