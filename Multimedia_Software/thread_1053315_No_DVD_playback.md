---
title: "No DVD playback"
date: 2009-01-28
forum: Multimedia Software
---

### Post by rullingen on 2009-01-28
Okay just installed Kubuntu 8.10 on my gf's laptop after having great success with it on my mothers although she watches DVD's this seems to be a problem.

The laptop is a 1.6ghz celeron D with 512mb RAM, Intel 943GML graphics chipset and acl883 sound chipset.

Whenever I try to play a DVD I get either nothing back (the play button unselects itself) and I've tried this with kaffeine, vlc and dragon player.

A speedy answer would be appreciated so that my *** isn't grilled.

Thanks in advance, Alex.

---

### Post by mc4man on 2009-01-28
I'll give you a few things to look at while waiting for someone who uses kubuntu 8.10 (I had it installed off and on since the beta, finally threw the livecd away last month.

Kaffeine definitely needs libxine1-ffmpeg installed along with libdvdcss2.

Vlc should be ok with just libdvdcss2

Many times when players don't respond (silently crash), it's due to the audio and or video outputs used. Maybe try adjusting in each players settings.

You should try to produce an error message. For vlc open it from a konsole, first with just vlc or then vlc -vv (vlc may output nothing, vlc -vv may output more than you'll want to see

For kaffeine try navigating to /media/cdrom0 (or /media/cdrom1), find the video_ts folder, right click -> open with kaffeine, that may show something.

I forget if a dvd icon shows up on the screen, if so right click on it to see if it's mounted.

---

### Post by Bablefish on 2009-01-28
Head to medibuntu site and get the codecs they have for download. If that fails all I can suggest is Automatrix.

---

### Post by iNaitvad on 2009-01-28
Try installing OGLE and Ogle-gui, but first install all codecs, I dont rembember if they are in Ultamatix or in Ubuntu Tweak, both are very good. I use VLC for all my videos and dvds. Open the IFO file. 
sorry for my bad english

---

### Post by Therion on 2009-01-28
Cut and Paste to the rescue!

```
sudo apt-get install kubuntu-restricted-extras
```

---

