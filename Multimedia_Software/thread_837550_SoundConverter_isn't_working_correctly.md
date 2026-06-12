---
title: "SoundConverter isn't working correctly"
date: 2008-06-22
forum: Multimedia Software
---

### Post by windoze87 on 2008-06-22
While going through an old box of goodies, i found an old mp3-cd i had made when i was still using Windows. I copied the files (all in .wma format, 128kbps) to my external hard drive, and proceeded to kick on SoundConverter to convert them to .mp3 files. It's only 20 songs, and as soon as i hit Convert, it decides not to do anything anymore. I can still cancel or pause the conversion, but the bar does not move a bit, and it does not convert the files. I'm not exactly sure what's going on, seeing as i had no problem converting 900+ songs from .wma to .mp3 when i first installed Linux. I have all necessary codecs installed to convert to .mp3. Any ideas? I'm using 8.04 btw

---

### Post by cozmicharlie on 2008-06-22
> **windoze87 said:**
> While going through an old box of goodies, i found an old mp3-cd i had made when i was still using Windows. I copied the files (all in .wma format, 128kbps) to my external hard drive, and proceeded to kick on SoundConverter to convert them to .mp3 files. It's only 20 songs, and as soon as i hit Convert, it decides not to do anything anymore. I can still cancel or pause the conversion, but the bar does not move a bit, and it does not convert the files. I'm not exactly sure what's going on, seeing as i had no problem converting 900+ songs from .wma to .mp3 when i first installed Linux. I have all necessary codecs installed to convert to .mp3. Any ideas? I'm using 8.04 btw

Can you play the files on your computer?  Have you tried another converter?

---

### Post by windoze87 on 2008-06-22
I found the problem... but i'm not so sure about a solution. I downloaded the KDE converter, soundKonverter, and it did the same thing-it refuses to convert files. I have all the gstreamer plugins(or thought i did) and i also installed w32codecs from the medibuntu repository when i installed Hardy. I decided to run Rhythmbox from terminal to see what kind of info i'd get, and this is what i saw: ```
rick@source:~$ /usr/bin/rhythmbox
Rhythmbox-Message: Missing plugin: gstreamer|0.10|rhythmbox-metadata|audio/x-asf-unknown decoder|decoder-audio/x-asf-unknown, codec_id=(int)355
Rhythmbox-Message: All missing plugins are blacklisted, doing nothing

``` it's telling me i don't have gstreamer, which i do, and then saying the plugin i need (which is the one that plays .wma formats) is blacklisted, but i thought w32codecs came with it? So it seems that Rhythmbox and in turn SoundConverter has the plugins blacklisted. Any ideas?

---

### Post by xc3RnbFO8P on 2008-06-22
> Hi,
I was having the same problem as yours. In my course of searching for a solution, I came across a post that deals with this.

The solution was to install libfaad2-0

This package contains the libmp4ff.so.0 that is needed by Banshee, Rhythmbox, and Exaile to play m4a files. 

Install the one in the official ubuntu repository. 

Hope this helps.
[http://ubuntuforums.org/showthread.php?t=456353]("http://ubuntuforums.org/showthread.php?t=456353")

---

### Post by windoze87 on 2008-06-22
Thanks for the effort lol but that didnt do anything, either. It just seems to me that .wma codecs are now blacklisted for some reason :confused:

---

### Post by xc3RnbFO8P on 2008-06-22
Then check in /etc/modprobe.d/blacklist

---

### Post by windoze87 on 2008-06-22
I also did that earlier after i ran Rhythmbox through terminal, and i couldn't see anything in there that pertains to .wma codecs.

---

### Post by cozmicharlie on 2008-06-22
You probably have done this but just to be sure - do you have ffmpeg installed?

---

### Post by windoze87 on 2008-06-22
I didn't, but when i installed it, it didn't make a difference anyway. I just now tried playing one of the .wma files in Totem, and it gave me basically the same output that Banshee did. ```
rick@source:~$ /usr/bin/totem
** Message: don't know how to handle audio/x-asf-unknown, codec_id=(int)355
** Message: Error: You do not have a decoder installed to handle this file. You might need to install the necessary plugins.
gstplaybasebin.c(2284): prepare_output (): /play

** Message: Missing plugin: gstreamer|0.10|totem|audio/x-asf-unknown decoder|decoder-audio/x-asf-unknown, codec_id=(int)355 (audio/x-asf-unknown decoder)
no application found
** Message: No installation candidate for missing plugins found.
** Message: don't know how to handle audio/x-asf-unknown, codec_id=(int)355
** Message: Error: You do not have a decoder installed to handle this file. You might need to install the necessary plugins.
gstplaybasebin.c(2284): prepare_output (): /play

** Message: Missing plugin: gstreamer|0.10|totem|audio/x-asf-unknown decoder|decoder-audio/x-asf-unknown, codec_id=(int)355 (ignoring)
** Message: All missing plugins are blacklisted, doing nothing

```

---

### Post by cozmicharlie on 2008-06-24
I found this post in the forums and it looks like the same problem you are having ([http://ubuntuforums.org/showthread.php?t=775943](http://ubuntuforums.org/showthread.php?t=775943)).  Below are the gstreamer and other codecs I have (and I can convert and play wma fine). Double check make sure you have them all installed.  If so try reinstalling them - uninstall all of them and also delete the gstreamer0.10 folder in your home/name (it is hidden) then reinstall the gstreamer plug ins as described in post #7 of the thread.  

gstreamer0.10-alsa
gstreamer0.10-ffmpeggstreamer0.10-gnomevfs
gstreamer0.10-pitfdl
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-base
gstreamer0.10-plugins-base-apps
gstreamer0.10-plugins-good
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
gstreamer0.10-plugins-pulseaudio
gstreamer0.10-tools
gstreamer0.10-x
totem-gstreamer
ubuntu-restricted-extras
ffmpeg
w32codecs

---

