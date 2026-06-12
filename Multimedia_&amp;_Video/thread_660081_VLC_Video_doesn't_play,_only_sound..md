---
title: "VLC: Video doesn't play, only sound."
date: 2008-01-06
forum: Multimedia &amp; Video
---

### Post by Gummi on 2008-01-06
I have been using VLC for some years now and it has always worked perfectly, until recently. I was going to watch one of my favourite shows, but only the audio would play, not the video! I then tried to play files that worked the day before, but the same problem occurred. I've tried to reinstall, restart preferences, and all that I. The files work for any other player I use just fine by the way.
Also I use the latest Ubuntu relese.
There was one other thread about this problem that I found, but I decided to make a new thread because there it was another distro that was having the problem.

Forgot to mention this but when the video file starts the video track is set to 'disable' but even when I set it to 'track 1' it won't start.
It also seems that I can play mpg's. Nothing else though.
I tried to run VLC through the command line to try to get any idea of what's wrong so I got this message with .avi
```
[00000311] main decoder error: no suitable decoder module for fourcc `XVID'.
VLC probably does not support this sound or video format.
```
this for .mkv
```
 [00000328] main decoder error: no suitable decoder module for fourcc `DX50'.
 VLC probably does not support this sound or video format.
```
And this for .ogm
```
[00000311] main decoder error: no suitable decoder module for fourcc `DX50'.
VLC probably does not support this sound or video format.
[00000348] main decoder error: no suitable decoder module for fourcc `vorb'.
VLC probably does not support this sound or video format.
[00000349] main decoder error: no suitable decoder module for fourcc `vorb'.
VLC probably does not support this sound or video format.
```

So I suppose the problem is that VLC doesn't support these files although it should, so I'm figuring I need some sort of lib file or something in that way.

In some .ogm and .mkv files the sound doesn't play either. I have all the codecs that are needed. 
The problem isn't that the video is completely black it just doesn't play.
I have tried this:
o Start VLC and click on Settings, then Preferences.
o Expand Video and then expand Output modules. You will notice several options for output device.
o Select the item Output modules, and notice the checkbox at the bottom right that says Advanced options. Check the box, and now you have the option to select a different output device.
o Pick X11 video output
o Click on Save and you are set! 
It doesn't work.

-Gummi

---

### Post by Gummi on 2008-01-07
Bump

---

### Post by eye208 on 2008-01-07
It seems VLC cannot find the codec libraries for Xvid, DivX, Vorbis etc.

Usually these codecs reside in /usr/lib, e.g. /usr/lib/libxvidcore.so.4.1, /usr/lib/libvorbis.so.0.4.0 etc. Please check if these libraries are actually missing.

---

### Post by Gummi on 2008-01-07
They are there xvid, vorbis and matroska.

---

### Post by Gummi on 2008-01-08
I got this error while trying to open mplayer 
```
mplayer: error while loading shared libraries: /usr/lib/libvorbis.so.0: invalid ELF header
```
I wonder if this has anything to do with my little problem.

---

### Post by ubu-for on 2008-01-08
> **Gummi said:**
> 
I have tried this:
o Start VLC and click on Settings, then Preferences.
o Expand Video and then expand Output modules. You will notice several options for output device.
o Select the item Output modules, and notice the checkbox at the bottom right that says Advanced options. Check the box, and now you have the option to select a different output device.
o Pick X11 video output
o Click on Save and you are set! 
It doesn't work.

1. You can try to remove VLC completely and then reinstall it with Synaptic.
2. You can also try to compile VLC 0.9.0 with [this HOWTO](http://ubuntuforums.org/showthread.php?t=380303) but replace the Debian source file (*.tar.gz) with the [latest Gutsy source file](http://nightlies.videolan.org/build/gutsy-i386/latest/vlc_0.9.0-svn20080108-0-0.tar.gz) or install the [latest Gutsy package](http://nightlies.videolan.org/build/gutsy-i386/latest/) from the VLC nightlies server.

---

### Post by eye208 on 2008-01-08
> **Gummi said:**
> I got this error while trying to open mplayer 
```
mplayer: error while loading shared libraries: /usr/lib/libvorbis.so.0: invalid ELF header
```
I wonder if this has anything to do with my little problem.
Most definitely. It seems the files are corrupt.

---

### Post by Gummi on 2008-01-09
What do I do then?

---

### Post by ubu-for on 2008-01-10
> **Gummi said:**
> I have been using VLC for some years now and it has always worked perfectly, until recently.

Alternatively you can use Ogle instead of VLC to play your DVDs.

---

### Post by Gummi on 2008-01-11
No, no. DVD works fine, it's more a problem about the files.

---

### Post by ubu-for on 2008-01-12
Do you already know [these codecs](http://translate.google.com/translate?u=http%3A%2F%2Fwiki.ubuntuusers.de%2FCodecs%23head-571fa89762a5bb4be0c6e7318c2e4dcdc3127a6c&langpair=de%7Cen&hl=de&ie=UTF-8) (chapter "With Ubuntu/GNOME") for Totem-GStreamer?

---

### Post by Gummi on 2008-01-12
Yes I have all codecs I need, as I said, it always worked untill recently.

---

### Post by Sukarn on 2008-02-16
I've been having exactly the same problem for a few weeks now.
VLC has video set to disable by default, and enabling it requires stopping and starting the video again, in which case it defaults back to disable, so video cannot be played or converted through VLC.
Anyone got any solution?

---

### Post by sha_man on 2008-07-13
EXACT same problem here... any solution? 
DVDs work fine,mpg etc.

---

### Post by Sukarn on 2008-07-13
I should have posted back in this thread when I fixed my problem, but the thing is, I don't know exactly which package fixed it.

I was using an external repository with Ubuntu. I don't remember which one it was, but I think it was some ppa.

I went through all of my repositories and checked which unofficial repository had vlc or any of its dependencies.

I removed vlc, ffmpeg and all their dependencies with **sudo dpkg --force-depends --purge**, disabled all external repositories, did a **sudo aptitude install vlc ffmpeg** and then re-enabled the repositories one-by-one to see which one gave me updates (can't remember which one was causing the problem).

I then removed the offending repository from my package sources list.

---

### Post by samjaynes on 2008-07-13
I am having the same issue.  Fresh new install of 8.04, and ran VLC just fine with video and audio.  After installing a few more apps (Compiz, Gnome-Do, and Wine), I have no Video.  I have tried removing and reinstalling VLC, via Synaptic and sudo apt-get remove with no luck.  Even the default Movie Player after installing the sudo apt-get install ubuntu-restricted-extras, same thing.

---

### Post by Sukarn on 2008-07-14
> **samjaynes said:**
> I am having the same issue.  Fresh new install of 8.04, and ran VLC just fine with video and audio.  After installing a few more apps (Compiz, Gnome-Do, and Wine), I have no Video.  I have tried removing and reinstalling VLC, via Synaptic and sudo apt-get remove with no luck.  Even the default Movie Player after installing the sudo apt-get install ubuntu-restricted-extras, same thing.

So you mean to say that your default video player (totem) is also not showing any video?

In that case, try disabling compiz to see whether that works.

PS: I will be unable to reply for the 11 days as I am leaving town in a few hours.

---

### Post by samjaynes on 2008-07-14
Thanks for your reply.  I am unaware of how to disable Compiz, however, I have change the Appearance/Visual effects to normal with no avail.

Still very strange, especially with VLC and Totem with codecs.  Is there a log file that would be helpful.

---

### Post by abbyb1987 on 2008-07-14
hey gummi 
u can check for the graphic card drivers
may be you need to enable the restricted drivers thst's it
i had the same problem
u can check out [www.ubuntrix.co.nr ]("http://www.ubuntrix.co.nr")for more info on this
do reply if it helped you
:)

---

### Post by sha_man on 2008-07-14
> **abbyb1987 said:**
> hey gummi 
u can check for the graphic card drivers
may be you need to enable the restricted drivers thst's it
i had the same problem
u can check out [www.ubuntrix.co.nr ]("http://www.ubuntrix.co.nr")for more info on this
do reply if it helped you
:)

unfortunately, there's no  "Administration -> Restricted Drivers Manager" like suggested in Hardy...

Like samjaynes VLC worked fine before i installed Beryl or Compiz (I can't remember) but now i removed all of them. VLC is still not working properly though. Is there a way to restore the libs?

---

### Post by sha_man on 2008-07-14
YES! I GOT THE ERROR** FIXED!!!** :):):)

what i did was to completely remove vlc and all its component, remove all ffmpeg (search in synaptic 'ffmpeg' then all completely removed.) Then i deleted the vlc dir (*rm -rf ~/.vlc*) and finally reinstalled everything i removed.
it now does work again.

---

