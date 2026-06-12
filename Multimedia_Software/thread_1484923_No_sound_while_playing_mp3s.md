---
title: "No sound while playing mp3s"
date: 2010-05-16
forum: Multimedia Software
---

### Post by adityak28 on 2010-05-16
Hi,
I'm new to linux and I've installed kubuntu 10.04 recently. I'm following the guide at [http://kubuntuguide.org/Lucid](http://kubuntuguide.org/Lucid) to set-up the system. I've installed the kubuntu-restricted-extras package however I do not get any sound while playing mp3s. The sound system is working as I get the kde tune when I start up. I have tried playing mp3s in amarok, audacious, kaffeine and vlc. None of them work. 

I opened system settings -> multimedia. It shows four devices and only the one which says 'ALC883(analog)' works in all categories (notifications, music, video, etc etc) when I click test. However sometimes I get a notification saying that the device doesn't work. I'm confused!

Another thing I noticed was that the mp3s play when Dolphin shows a preview of the file when it is selected. I mean that there is a preview part in the right hand part of the window. When I press play there, the mp3s play. But there is no sound when I play movies and mp3s in amarok, audacious, vlc or kaffeine

The motherboard I'm using is Gigabyte M61PME-S2P. Its an nForce 430 motherboard with integrated graphics and sound.

---

### Post by lidex on 2010-05-16
Are you able to play other audio files in those programs? ogg, flac, etc?

Try this thread:
[http://ubuntuforums.org/showthread.php?t=1016523]("http://ubuntuforums.org/showthread.php?t=1016523")

---

### Post by adityak28 on 2010-05-17
Thnx for the reply.. I tried an ogg file and its plays fine in amarok. Amazingly now mp3s seem to be working in amarok. They aren't playing in any other players though. This is getting confusing.

---

### Post by adityak28 on 2010-05-17
I came across this in 'Comprehensive Multimedia and Video Howto' which is a sticky in the multimedia and video section of the forums. 

> **sudo apt-get install alsa-oss faac faad flashplugin-nonfree  libk3b2-extracodecs libmp3lame0 libtunepimp5-mp3 libxine1-ffmpeg  non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar**

Will this help in any way? What is alsa-oss and what is xine?

---

### Post by lidex on 2010-05-17
> **adityak28 said:**
> I came across this in 'Comprehensive Multimedia and Video Howto' which is a sticky in the multimedia and video section of the forums. 

Will this help in any way? What is alsa-oss and what is xine?
OK. You obviously didn't read the thread I linked to or you'd know what xine is. Go back there and use the info (and click on the links as well) in the thread and remember you're using kde, not gnome.

This should get you started. In a terminal="Applications->Accessories->Terminal"
```
sudo aptitude install libxine1-all-plugins
sudo aptitude install phonon-backend-xine
sudo aptitude remove phonon-backend-gstreamer
```

---

### Post by adityak28 on 2010-05-18
OK. Thanks for your patience with a n00b like me.

libxine1-all-plugins was installed. phonon-backend-xine was already  present. phonon-backend-gstreamer was not present.

Also this is my output from xine-list-1.1
```

aditya@Aditya-Home:~$ xine-list-1.1 | sed 's/;/\n/g' | grep mpeg
video/mpeg
video/x-mpeg
audio/mpeg2
audio/x-mpeg2
audio/mpeg3
audio/x-mpeg3
audio/mpeg
audio/x-mpeg
audio/x-mpegurl
audio/mpegurl

```Could you explain this behavior? 
When I start amarok for the first time I get a notification saying "The audio playback device HDA(ALC 883)does not work". If I try playing an mp3 I get no sound although the progress bar seems to be moving. When I play an ogg file sound works and mp3s play normally thereafter.
This same trick to get mp3s to work does not work in audacious or kaffiene or vlc.

Sound doesn't work in movies as well.

---

