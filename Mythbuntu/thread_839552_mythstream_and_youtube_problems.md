---
title: "mythstream and youtube problems"
date: 2008-06-24
forum: Mythbuntu
---

### Post by sr_guy on 2008-06-24
I'm trying to stream thai videos for my wife (you guessed it, she's from Thailand). I've tried it two ways:

1. I tried using an RSS feed + the youtube parser and I get a list of thai youtube vid links but get an error "no url's found".

(parser site [http://googlesystem.blogspot.com/2008/01/youtube-feeds.html](http://googlesystem.blogspot.com/2008/01/youtube-feeds.html))

2. I tried with the direct youtube vid link (see below), but all I get is the youtube side menu in text list form (Home, sites, Favorites, Signin Etc...) using the link below:

[http://youtube.com/watch?v=vnFgiuTMV98](http://youtube.com/watch?v=vnFgiuTMV98)

Any tips would be appreciated

---

### Post by sgunther on 2008-06-24
I posted a bug;

[https://bugs.launchpad.net/mythbuntu/+bug/223781](https://bugs.launchpad.net/mythbuntu/+bug/223781)

It is a relatively easy fix.

---

### Post by sr_guy on 2008-06-24
Should that fix both the RSS feed and single vid link issue?

---

### Post by sgunther on 2008-06-24
Yes

---

### Post by ctpaterson on 2008-06-24
> **sgunther said:**
> I posted a bug;

[https://bugs.launchpad.net/mythbuntu/+bug/223781](https://bugs.launchpad.net/mythbuntu/+bug/223781)

It is a relatively easy fix.

I've installed the fix (thanks for that); and YouTube videos are now playing; but the audio is significantly out of step with the video.  The audio is several seconds ahead.

Anyone know what's causing this?  I've switched my audio driver from PulseAudio to ALSA to deal with some volume control issues I had on my initial install.  Besides that, don't know what else I might have done to cause the problem.

Cheers.

---

### Post by ctpaterson on 2008-06-29
> **ctpaterson said:**
> I've installed the fix (thanks for that); and YouTube videos are now playing; but the audio is significantly out of step with the video.  The audio is several seconds ahead.

Anyone know what's causing this?  I've switched my audio driver from PulseAudio to ALSA to deal with some volume control issues I had on my initial install.  Besides that, don't know what else I might have done to cause the problem.

Cheers.

Got a tip from the mythtv-users mailing list.  A/V sync can be adjusted with the + and - keys.

I haven't found any way of storing such a setting so I don't have to do it on a subsequent playing of the video, but it's still a big improvement.

---

### Post by sr_guy on 2008-06-29
Yes, everything is working fine with the parser, and I can get a list and play the youtube vids. The vid/audio synch issue seems to be on the lower bitrate vids on youtube. Other higher bitrate vids are fine with no synch problems most of the time.

I don't have any + or - keys on my hauppauge remote. I have the standard remote for the PVR-150. Any further suggestions would be apprectiated.

---

### Post by ctpaterson on 2008-06-29
> **sr_guy said:**
> Yes, everything is working fine with the parser, and I can get a list and play the youtube vids. The vid/audio synch issue seems to be on the lower bitrate vids on youtube. Other higher bitrate vids are fine with no synch problems most of the time.

I don't have any + or - keys on my hauppauge remote. I have the standard remote for the PVR-150. Any further suggestions would be apprectiated.

An IR keyboard.

I'm not being flippant.  I've got the same setup as you (an Hauppauge remote with no mapped keys for +/-).  For this, and a number of other issues that have come up requiring keybaord use - I'm leaning towards getting an IR keyboard...I'm just trying to figure out how to keep it away from the wee ones.

I suppose you could also remap some keys in the lirc.conf, but I haven't tried that so far myself.

---

### Post by ctpaterson on 2008-07-05
> **sr_guy said:**
> Yes, everything is working fine with the parser, and I can get a list and play the youtube vids. The vid/audio synch issue seems to be on the lower bitrate vids on youtube. Other higher bitrate vids are fine with no synch problems most of the time.

I don't have any + or - keys on my hauppauge remote. I have the standard remote for the PVR-150. Any further suggestions would be apprectiated.

I think we have something here:

I've had to remap some remote buttons to do the trick.

The CH/PG up and down buttons don't do anything in mplayer, and they
seemed suitable options, so I remapped those.

In the front end, select Setup -> Edit Keys -> Stream, and bind the
CH/PG up and down buttons to AVDEC and AVINC.

Now, when I play a stream that's out of sync, I can just hit the
buttons on my remote until it all lines up again.

Cheers.

---

### Post by LabRat79 on 2008-07-06
I was also wrestling with the audio sync issue on youtube. I finally switched my default player to vlc like so:

[http://mythtvbox.blogspot.com/2006/10/switching-from-mplayer-to-vlc.html](http://mythtvbox.blogspot.com/2006/10/switching-from-mplayer-to-vlc.html)

This cured all my sync issues so far on all the videos that used to be out of sync...there's also a guide on that site for setting up manual syncing with vlc too.

Edit: (but keep in mind the settings he talks about for setting up controls are in /.lirc/vlc NOT /.vlc/vlcrc this isnt very clear so took me a minute.

---

