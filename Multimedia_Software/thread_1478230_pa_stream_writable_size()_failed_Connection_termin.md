---
title: "pa_stream_writable_size() failed: Connection terminated"
date: 2010-05-09
forum: Multimedia Software
---

### Post by Howard Roark on 2010-05-09
Music files will play for anywhere from 10 sec to 2 min then no sound progress bar advances through rest of song almost instantly message given is:
An error occurred
pa_stream_writable_size() failed: Connection terminated 

Can anybody out there tell me what this means and how to fix it.
Thanks.

---

### Post by AlexanderDGreat on 2010-05-12
pa_stream_writable_size() failed: Connection terminated - yeah I also experience this when using the default Movie Player in Lucid. That's why I'm using VLC.

Why is this like this? It also happens when you access a video or mp3 over the network.

---

### Post by pjalegria on 2010-05-19
Same problem where... any fix?

---

### Post by lidex on 2010-05-20
PulseAudio? Try this:
```
rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```

Logout/in

---

### Post by applejuicekiss on 2010-05-24
i have the same issue using totem in Lucid Lynx when playing video files over wireless.  this was never an issue in karmic with the same video files.  mplayer(smplayer) plays same files without problems.  i would be happy enough if i could get smplayer to be the default action when opening .avi files.

---

### Post by mc4man on 2010-05-24
> would be happy enough if i could get smplayer to be the default action
Just r. click on any .avi - properties -> open with and pick smplayer (or go to 'add' if smplayer isn't available.

---

### Post by lidex on 2010-05-25
There is a bug report here:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/496616]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/496616")

Perhaps an updated version of pulse:
[https://launchpad.net/~ubuntu-audio-dev/+archive/ppa?field.series_filter=]("https://launchpad.net/~ubuntu-audio-dev/+archive/ppa?field.series_filter=")

---

### Post by mc4man on 2010-05-26
It's possible this error message is of the generic type - there may be different causes.

I only have seen it on an install that uses 5.1 analog output  - it first occurred during beta and initially only affected ac3 audio.

As of recently pretty much all audio in video resulted in error ( exception .avi with mp3

I have other installs with 2, 2.1 sound where issue doesn't exist, and it's possible a fresh install could resolve the affected install ( but I've no interest in doing so.

Because I don't use gstreamer for 5.1 playback (vs. 6 ch output), I resolved here by removing the gstreamer pulseaudio plugin which restored all playback in gstreamer

---

### Post by MaXMhZ on 2010-08-24
Just had the same error in Lucid 32bit.

Installing Ubuntu extras and Audacious through Software Center seems to have solved it.

---

### Post by zeron on 2010-12-24
i had the same problem! i tried a lot of thinks but nothink worked ,in the end i opened synaptic and i completle uninstall gstreamer and gstreamer-plugins and other gstreamer tools(gstreamer ffmpeg,gstreamer-pulseaudio), then i completle uninstall pulseaudio ( pulseaudio sound server), after that i already had vlc installed so i reinstalled vlc (from synaptic) ,then logout login and everythink is plaing so far i tested only mp4(videos) and mp3 i left a playlist for some hours with no problem. IF anyone is going to do this be carrefull
because now i have only vlc installed ,uninstalling all these i have no more mplayer (media player).just be carrefull this worked omy machine but i dont know what will do to others!

---

### Post by zeron on 2010-12-24
i had the same problem! i tried a lot of thinks but nothink worked ,in the end i opened synaptic and i completle uninstall gstreamer and gstreamer-plugins and other gstreamer tools(gstreamer ffmpeg,gstreamer-pulseaudio), then i completle uninstall pulseaudio ( pulseaudio sound server), after that i already had vlc installed so i reinstalled vlc (from synaptic) ,then logout login and everythink is plaing so far i tested only mp4(videos) and mp3 i left a playlist for some hours with no problem. IF anyone is going to do this be carrefull
because now i have only vlc installed ,uninstalling all these i have no more mplayer (media player).just be carrefull this worked omy machine but i dont know what will do to others!

---

### Post by shadowgodd on 2011-02-18
yea i have both pa_stream_writable_size failure and pa_stream_cork failure 
Im using Ubuntu

i got ubuntu cuz i heard it was easier to use then lucid but all its bugs and glitches are really pissing me off i should have linux pay me for my other laptop i destroyed cuz it glitched during a damn presintation i was working on for like 3 hours straight, yea like all linux products it crashed and i lost everything guess i shoulda learned my lesson then and said screw linux all 2gethr but the only other software is microsoft... i hate microsoft too microsoft in general lota problems with that crappy software. im just hating tech all 2gether now i mean all the bugs glitches crashes and anger just isnt worth it honestly so what i do now is i take my vids and music im working on listening to or watching and i put them on a flash and play them thru the only thing that actually works in the tech world my PS3 best thing ive ever had... to bad it dont have all the software i need and use cuz then i would never touch a PC again lol 
~the old PS3s had the OS option to add linux software worked good till my virus proof PS3 got a virus and then died on me thanx linux free software my *** so far linux has cost me about 2k$

best fix run your stuff thru a PS3 via Flash drive or External harddrive better bigger display and better sound too

---

