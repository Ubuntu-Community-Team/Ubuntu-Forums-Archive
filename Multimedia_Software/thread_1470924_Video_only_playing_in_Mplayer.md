---
title: "Video *only* playing in Mplayer"
date: 2010-05-03
forum: Multimedia Software
---

### Post by whitefort on 2010-05-03
I'm a dunce with this stuff, so any help will be much appreciated.

I upgraded to Lucid.  I THINK video played OK at first after the update (though I wouldn't swear to it), but something has gone badly wrong.

In Totem, VLCPlayer, and Dragon Player, I can hear the soundtrack to the videos, but they show only a blank screen.

But if I run the video from a terminal and use Mplayer, it plays perfectly.

I'm clueless where to even start fixing this, but I'm hoping that the fact that vids play in Mplayer might provide a clue.  Help?

I'll happily provide any other info that's needed.

---

### Post by doom's day on 2010-05-03
Which codec does the video use? If it is not Ogg Theora, then it could be deal with the codecs you can play. You need to install these packages:

[list]
[*]gstreamer0.10-plugins-good
[*]gstreamer0.10-plugins-bad
[*]gstreamer0.10-plugins-ugly
[*]gstreamer0.10-plugins-base
[*]gstreamer0.10-ffmpeg
[/list]

Greets, Doom's day.

---

### Post by whitefort on 2010-05-03
Hi, & thanks for the reply.

I don't seem to be missing any of those codecs - they're all installed.

I hope this isn't going to be one of those 'impossible to fix' things...

---

### Post by Aepervius on 2010-05-09
I have the exact contrary symptom of what you have. I have everything functionnning under VLC, Totem, but when trying to open a video , be it AVi or MKV I get a signal 11 from mplayer (and a blank screen). 

I tryed the re-install in synpatic, but it did not bring anything. 

Maybe I should try to de-install and re-install...

---

### Post by Jose Catre-Vandis on 2010-05-09
Have you
```
sudo apt-get install ubuntu-restricted-extras x264 ffmpeg libvdpau1 
```

(Enable the vdpau ppa for libvdpau1, and choose your flavour for restricted-extras)

---

