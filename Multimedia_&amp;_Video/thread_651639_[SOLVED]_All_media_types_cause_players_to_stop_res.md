---
title: "[SOLVED] All media types cause players to stop responding"
date: 2007-12-27
forum: Multimedia &amp; Video
---

### Post by TheAxeR on 2007-12-27
I tried really hard to find other threads with a similar problem but none seemed to fit.  I just bought a HP dv2500 and just got the sound working, everything was good until last night.  Everytime I try to play a media file ( mp3, flac, avi, ogg) then what ever player that I choose to open it with stops responding.  I have tried vlc, gxine, totem movie player, rhythmbox. The sound works, it plays the startup sound and also when I go into the sound set up the test sound works.

---

### Post by linuxwizard on 2007-12-28
Make sure you have all your codecs installed.
[https://help.ubuntu.com/community/RestrictedFormats#head-ade7b6cc5a280ee943fd7884cf7dc49ebe7e22ca](https://help.ubuntu.com/community/RestrictedFormats#head-ade7b6cc5a280ee943fd7884cf7dc49ebe7e22ca)

---

### Post by TheAxeR on 2007-12-28
I am certain that the codecs are installed, everything worked just a couple of days ago.  One thing that I have just noticed is that in rhythmbox is gives importing errors which say that it can not access the files.  However, I know that the permissions are such that anybody can read the files.

---

### Post by TheAxeR on 2008-01-01
Sorry to bump but I have not been able to find anything on this.

---

### Post by TheAxeR on 2008-01-01
Ok so I think I found a solution.  I was messing around with things and was able to get vlc to play media files as long as a I forced its alsa device.  By this I  mean I went into preferences selected audio>alsa>____ .  I changed it from the default to my sound card.  However, this would only cause vlc to work.  This lead me to belive that it may be some sort of sound server issue.   I could not find anything that looked out of the ordinary in any of the gui administrative tools (multimedia systems selector or sound preferences etc) so I went into gconf and looked around to see if I could find anything relating to a sound server.  Well I found that esd was enabled by default so I deselected it logged out, logged in and everything is working now.  

So in summary I got everything to work as it is supposed to work by going and deselecting the option
> /desktop/gnome/sound/enable_esd in gconf.

And just to note I almost did a backflip when this worked because it is the first thing that I have solved 100% on my own with linux in my 1.5years with ubuntu so far. :)

---

