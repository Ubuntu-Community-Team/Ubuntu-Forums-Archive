---
title: "Audio through setup/JACK muting other programs"
date: 2010-07-18
forum: Multimedia Software
---

### Post by panda21 on 2010-07-18
I have my audio working just fine with the default out of the ubuntu box setup for almost all of what I do, but I need to be able to pass through audio from the line-in to the system output.

The only way I could find to do that is to use JACK and connect the system input to the system output. The problem is that as soon as I start JACK control, even before I start the actual JACK system, all other programs are suddenly unable to play any sound.

I'm somewhat confused about how audio is setup in ubuntu and how the various options interact/co-exist (alsa/pulse/oss/JACK etc), but ideally I'd like to be able to do this without using JACK at all, but having JACK not block all other programs from making any sound would be enough.

I'm taking input from the motherboard built in sound and the output is to a usb soundcard.

---

### Post by cchhrriiss121212 on 2010-07-18
You should be able to playback your line-in using audacity. Set up a track and then go to preferences and select the appropriate input and outputs, then check the software playthrough box. Then just monitor the track.

Sound in Ubuntu is like this by default:
Soundcard>ALSA>Pulse>Software
Jack is stopping all sounds as it is a sound server that acts on top of ALSA, as is Pulse audio, so when you start jack, pulse is stopped.
You can get many regular programs to play sound through jack, but it is not designed for that purpose. Jack is for low latency audio work and music production programs, so it sounds like you don't really need it.

---

