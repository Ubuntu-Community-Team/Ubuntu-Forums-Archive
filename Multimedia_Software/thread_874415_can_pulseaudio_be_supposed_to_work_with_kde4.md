---
title: "can pulseaudio be supposed to work with kde4?"
date: 2008-07-29
forum: Multimedia Software
---

### Post by kofshower on 2008-07-29
Hey there.
I am an novice to KDE,but I use GNOME for years.In GNOME environment,pulseaudio works good in soft dmix.But in KDE4,it doesn't work.
    I know phonon provides countepart to pulseaudio in KDE environment.But I donnt know how to get it work.can pulseaudio be supposed to work with kde4? or other suggestions.Thx for your help :)

---

### Post by kofshower on 2008-07-30
up:(

---

### Post by ggaaron on 2008-08-09
> **kofshower said:**
> Hey there.
I am an novice to KDE,but I use GNOME for years.In GNOME environment,pulseaudio works good in soft dmix.But in KDE4,it doesn't work.
    I know phonon provides countepart to pulseaudio in KDE environment.But I donnt know how to get it work.can pulseaudio be supposed to work with kde4? or other suggestions.Thx for your help :)

KDE4 uses Phonon, a multimedia layer that can use several backends like Xine or GStreamer that in turn can use PulseAudio (either by plugin or ALSA redirection). So:

KDE4 application -> Phonon -> GStreamer or Xine -> PulseAudio -> ALSA

Phonon is not competing with PulseAudio, it is a different layer that can take advantage of PulseAudio.

My KDE 4.1 setup is Xine output and then PulseAudio as output device. You can setup it in Sytem Settings -> Sound. I had to mark 'show advanced devices' to get PulseAudio output.

---

### Post by kofshower on 2008-10-30
Thanks for your help,ggaaron. Once I thought phonon is a proxy layer for decoding sound stream. Pulseaudio is a proxy layer using alsa background.:)
My problem is how we can start pulseaudio normaly in KDE41 just as in Gnome.I am confused so much at it.

---

### Post by ggaaron on 2008-11-03
I'm quite confused too=) My setup simetimes just works so pulseaudio is started when I start an application using it but sometimes I have to start it manually. You could configure pulseaudio not to turn itself off after some time of not being used and start it on login.

---

