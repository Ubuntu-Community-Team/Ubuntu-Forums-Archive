---
title: "Ubuntu 11.04, Subsonic 4.5 Jukebox mode with PulseAudio Equalizer"
date: 2011-11-16
forum: Multimedia Software
---

### Post by bigtdp on 2011-11-16
I'm running Ubuntu 11.04 desktop vanilla, with Subsonic 4.5 (build 2384).

I have really bass-y speakers, so need to have an equaliser running on my media hub so I don't get complaints from the neighbours. I installed PulseAudio Equalizer and it does a grand job Eq-ing all the different audio sources I've thrown at it (VLC, SMPlayer, banshee etc) EXCEPT for the jukebox mode on Subsonic. If I switch to the standard web player, the audio is equalised, but using the jukebox player it is not.

I guess that this is a java issue, and that the standard web player is flash?

Initially I had no audio from the Jukebox mode, so I installed the sun java jdk instead of the open one, and I now have audio.

I looked at this [Subsonic Wiki]("http://sourceforge.net/apps/mediawiki/subsonic/index.php?title=Players#Selecting_the_Soundcard") and I have the following devices:

```

Available mixers:
Intel [plughw:0,0]
Intel [plughw:0,1]
Intel [plughw:0,2]
SAA7134 [plughw:1,0]
Port Intel [hw:0]
Port SAA7134 [hw:1]
```



actually, when I ran that earlier I also had 2 extra lines, not sure what I've done to get rid of them, but they were:

```

Select all
PulseAudio Mixer
default [default]
```



anyways, anyone got any ideas why the jukebox audio is not being equalised? or a different system-wide eq that will work for me?

ta,

xTx

---

### Post by bigtdp on 2011-11-17
Bump...

Help!

:D

xTx

---

### Post by bigtdp on 2011-11-27
Still no luck here...

Surely someone knows something about Java audio that can help?

xTx

---

### Post by nymusicman on 2012-06-16
.

---

### Post by apos on 2012-06-27
Running the program with special arguments might help:

> -Djava.library.path=/usr/lib/jvm/java-6-openjdk/jre/lib/amd64/ (so it picks up the libpulse-java.so)
-cp /usr/lib/jvm/java-6-openjdk/jre/lib/ext/pulse-java.jar

[https://answers.launchpad.net/ubuntu/+source/pulseaudio/+question/176480](https://answers.launchpad.net/ubuntu/+source/pulseaudio/+question/176480)

might help ?!

---

