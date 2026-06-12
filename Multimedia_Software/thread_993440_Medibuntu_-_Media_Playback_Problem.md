---
title: "Medibuntu - Media Playback Problem"
date: 2008-11-25
forum: Multimedia Software
---

### Post by Zaraphrax on 2008-11-25
Yesterday, I did a fresh install of Intrepid 8.10 (64 bit). I wanted to have it set up, so I could play all video files (and DVD's) with VLC and audio files with Amarok. I tried following the guide at the top of this page, but something got messed up. Whenever I tried to play a file, Totem Movie Player would crash. It would play like a second of the file, and then disappear, never to return. I tried restarting the X server, I tried rebooting, I tried reinstalling the packages from the repository and nothing seemed to make a difference. I also couldn't set file associations to VLC player. I didn't even bother trying to install Amarok, and figured that I'd just format my Ubuntu partition and start again (now typing this on the same machine from Windows, lol). I'll have to install Intrepid again later to try out what you guys suggest.

So, my question.

1) What packages do I need to install so that I can play every sort of video file (including DVD's) with VLC Player, and all sorts of audio files with Amarok (or, is there something better than Amarok? I'd prefer something lightweight yet functional.)?

2) How do I set file associations to these applications?

3) After this, how do I remove all other AV apps from my system? Which packages are able to be removed without breaking something? I don't want to have Totem Movie Player or any of that installed, I just want what I need.

Any help is appreciated - Sorry if this is a dumb question, I'm not that skilled with stuff like this.

---

### Post by soxs on 2008-11-25
> **Zaraphrax said:**
> Yesterday, I did a fresh install of Intrepid 8.10 (64 bit). I wanted to have it set up, so I could play all video files (and DVD's) with VLC and audio files with Amarok. I tried following the guide at the top of this page, but something got messed up. Whenever I tried to play a file, Totem Movie Player would crash. It would play like a second of the file, and then disappear, never to return. I tried restarting the X server, I tried rebooting, I tried reinstalling the packages from the repository and nothing seemed to make a difference. I also couldn't set file associations to VLC player. I didn't even bother trying to install Amarok, and figured that I'd just format my Ubuntu partition and start again (now typing this on the same machine from Windows, lol). I'll have to install Intrepid again later to try out what you guys suggest.

So, my question.

1) What packages do I need to install so that I can play every sort of video file (including DVD's) with VLC Player, and all sorts of audio files with Amarok (or, is there something better than Amarok? I'd prefer something lightweight yet functional.)?

2) How do I set file associations to these applications?

3) After this, how do I remove all other AV apps from my system? Which packages are able to be removed without breaking something? I don't want to have Totem Movie Player or any of that installed, I just want what I need.

Any help is appreciated - Sorry if this is a dumb question, I'm not that skilled with stuff like this.

Get what you need:
various media players:```
 sudo apt-get install -y mplayer mencoder vlc qtiplot 
```gstreamer codecs:
```
sudo apt-get install -y gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-good gstreamer0.10-ffmpeg gstreamer0.10-fluendo*  gstreamer0.10-schroedinger gstreamer0.10-pulseaudio gstreamer0.10-sdl python-gst0.10

```xine codecs:
```
sudo apt-get install -y libxine1-plugins libxine1-all-plugins
```dvd stuff:

```
sudo apt-get install -y libdvdcss2 libdvdread3 libdvdnav4
```Setting file associations is easiest, right clicking a file and defining the open with default for that media type you just clicked on.

Amarok is quite fast. there are other solutions (with bling bling and without, with and without ....), but most of them are _A LOT_ slower than Amarok (in case they are as feature rich).

For leightweight only, I suggest ```
sudo apt-get install -y audacious
```

---

### Post by Zaraphrax on 2008-11-26
> **soxs said:**
> Get what you need:
various media players:```
 sudo apt-get install -y mplayer mencoder vlc qtiplot 
```gstreamer codecs:
```
sudo apt-get install -y gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-good gstreamer0.10-ffmpeg gstreamer0.10-fluendo*  gstreamer0.10-schroedinger gstreamer0.10-pulseaudio gstreamer0.10-sdl python-gst0.10

```xine codecs:
```
sudo apt-get install -y libxine1-plugins libxine1-all-plugins
```dvd stuff:

```
sudo apt-get install -y libdvdcss2 libdvdread3 libdvdnav4
```Setting file associations is easiest, right clicking a file and defining the open with default for that media type you just clicked on.

Amarok is quite fast. there are other solutions (with bling bling and without, with and without ....), but most of them are _A LOT_ slower than Amarok (in case they are as feature rich).

For leightweight only, I suggest ```
sudo apt-get install -y audacious
```

Hey, thanks for the help so far. There must be something I'm not doing right. Everything was working fine up until the

```
sudo apt-get install -y libdvdcss2 libdvdread3
```

It came up and said that libdvdcss2 has no installation candidate. Just to try and troubleshoot it, I added the Medibuntu repository to the sources list to no avail. I also ran a:

```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_amd64.deb
```

To try and install the package manually, but that didn't do anything either.

If I try and play an AVI file with VLC or Totem, I get the same thing. The file begins to play, then the player disappears. The same thing happens with MP3 files.

Any ideas on what's going on?

---

### Post by Zaraphrax on 2008-11-26
Just got Amarok installed. MP3's play fine with it. What the heck?

---

### Post by mc4man on 2008-11-26
Just go here and download directly, you can square up your sources later

[http://packages.medibuntu.org/intrepid/libdvdcss2.html](http://packages.medibuntu.org/intrepid/libdvdcss2.html)

There's not that much of value from medibuntu for intrepid atm anyway

list - [http://packages.medibuntu.org/intrepid/index.html](http://packages.medibuntu.org/intrepid/index.html)

---

### Post by Zaraphrax on 2008-11-26
> **mc4man said:**
> Just go here and download directly, you can square up your sources later

[http://packages.medibuntu.org/intrepid/libdvdcss2.html](http://packages.medibuntu.org/intrepid/libdvdcss2.html)

There's not that much of value from medibuntu for intrepid atm anyway

list - [http://packages.medibuntu.org/intrepid/index.html](http://packages.medibuntu.org/intrepid/index.html)

Ok, have done that. AVI files still won't play, nor will DVD's. The player opens, then disappears again.

---

### Post by mc4man on 2008-11-26
And what player would that be?
And how are you trying to access the video?

---

### Post by Zaraphrax on 2008-11-26
> **mc4man said:**
> And what player would that be?
And how are you trying to access the video?

I've tried both Totem Movie Player and VLC Player.

The files are stored on an NTFS formatted internal disk. I'm simply going Right Click>Open with VLC from File Explorer.

---

### Post by mc4man on 2008-11-26
As far as accessing a ntfs volume I can only do so in 8.04 with vlc 0.9.6.

It plays a video_ts fine, as far as .avi's, I've only a couple, one it plays the other it doesn't.
Vlc can be a little picky as to the encoding whereas mplayer or totem-xine have no issues.

I'd try with the .avi's with something else.

Playback of dvd disks you should be fine with vlc in 8.10


Totem movie player (gstreamer) is pretty much worthless in 8.10, I wouldn't waste your time, certainly with dvd's.

---

### Post by Zaraphrax on 2008-11-26
> **mc4man said:**
> As far as accessing a ntfs volume I can only do so in 8.04 with vlc 0.9.6.

It plays a video_ts fine, as far as .avi's, I've only a couple, one it plays the other it doesn't.
Vlc can be a little picky as to the encoding whereas mplayer or totem-xine have no issues.

I'd try with the .avi's with something else.

Playback of dvd disks you should be fine with vlc in 8.10


Totem movie player (gstreamer) is pretty much worthless in 8.10, I wouldn't waste your time, certainly with dvd's.

MPeg's don't play either. Totem, VLC, nothing works.

---

### Post by mc4man on 2008-11-26
Try putting a dvd in the drive, hold down the shift button and you'll get a pop up asking you what to do. Pick 'open with Vlc.. ' What happens? 
Vlc opens and closes?

If so maybe try adjusting your audio and or video output modules (tools -> preferences.

Otherwise start vlc in terminal with debug logging, then go file -> open disc

vlc -vv  or vlc-vvv ( start with 2 v's to limit info

---

### Post by Zaraphrax on 2008-11-26
Hey man, thanks.

I got it working by installing the proper drivers for my video card. I figured since Compiz was working, the ones that are installed by default were fine, but obviously not. Everything is working great now, thanks for your help. Much appreciated. :)

---

### Post by soxs on 2008-11-26
> **Zaraphrax said:**
> Ok, have done that. AVI files still won't play, nor will DVD's. The player opens, then disappears again.
  You have to do the DVD playback part again after adding medibuntu repositories.

---

### Post by sandbox4us on 2008-11-26
Zaraphrax,

What video card do you have?  I'm having the same problem.  I use an ATI card, but when I use the proprietary driver, I get problems with configuring a dual monitor setup.

---

