---
title: "SMPlayer 0.6.4 released"
date: 2008-10-25
forum: Multimedia Software
---

### Post by rvm4000 on 2008-10-25
[SMPlayer](http://smplayer.berlios.de) 0.6.4 has been released.

Most important changes:
> 
 * Now the dialog to find subtitles can also download the subtitle file and load it in smplayer automatically.
 * The black screen problem when using Compiz should really be fixed now.
 * Added support for encoding autodetection for subtitle files. Requires a mplayer compiled with enca support.
 * Now it's possible to choose the audio device to be used with alsa (needs the application "aplay").
 * Added the possibility to add consecutive files (video_01.avi, video_02.avi..) automatically to the playlist.
 * Bugfix: logout is not cancelled by smplayer.
 * Now the options in preferences display a tooltip with a help message.
 * Now it's possible to change the video track.
 * Added the Galician translation.


You can download deb packages for Ubuntu Hardy, [**here**](http://smplayer.berlios.de/downloads.php).

Or experimentally, you can try this repository for apt:
> deb [http://ppa.launchpad.net/rvm/ubuntu](http://ppa.launchpad.net/rvm/ubuntu) hardy main

---

### Post by markinf on 2008-10-25
*** The black screen problem when using Compiz should really be fixed now.**

That problem made me turn off Compiz by default :D, I think now I will use it again =)

Thanks very much
^^ Downloading now =D

---

### Post by rvm4000 on 2008-11-01
From svn r2161, smplayer allows better customization for srt and sub subtitles:

[[img]http://img368.imageshack.us/img368/8959/subtitlesfr1.th.png[/img]](http://img368.imageshack.us/my.php?image=subtitlesfr1.png)[[img]http://img368.imageshack.us/images/thpix.gif[/img]](http://g.imageshack.us/thpix.php)

Previously only the colors could be changed.

These settings (except scale and line spacing) won't be applied for actual *.a.s.s subtitles, they'll use their own defined styles (I think that's better).

If you want to test this new feature, you can get packages (i386 and amd64) [here](ftp://ftp.berlios.de/pub/smplayer/ubuntu/).

---

