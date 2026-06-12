---
title: "No sound from right channel speaker"
date: 2012-02-28
forum: Multimedia Software
---

### Post by evil gnome on 2012-02-28
I have no sound coming out of the right channel.
At first thought maybe the right side speaker is dead or the cable is cut, but checked with a functional headphone and it there was no sound coming from the right channel again.

Sound card is onboard AC'97

---

### Post by evil gnome on 2012-02-28
bump

---

### Post by Yellow Pasque on 2012-02-28
Please do this: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by evil gnome on 2012-02-29
> **Temüjin said:**
> Please do this: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)
Thank you.
This is the link: [http://www.alsa-project.org/db/?f=abef7bbce73b7b8eb13e7f490f7204610188feea](http://www.alsa-project.org/db/?f=abef7bbce73b7b8eb13e7f490f7204610188feea)

---

### Post by Yellow Pasque on 2012-02-29
Everything looks in order, but I would try checking alsamixer to see if there's some 'Mono' option.

---

### Post by evil gnome on 2012-02-29
Typed "alsamixer" in terminal and this was the result. please tell me what to change

---

### Post by Yellow Pasque on 2012-02-29
I see you already have it set to '2ch' so I'm out of ideas at the moment. Perhaps pulseaudio is doing something funny :\

---

### Post by Rodney9 on 2012-02-29
These two manuals give good advice for solving sound problems:

[Sound Troubleshooting Guide]("https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit")
(by Lkjoel and Wildmanne39)


[Sound Troubleshooting Procedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")
(by Mark Rijckenberg)

```
sudo apt-get install pavucontrol
```

PulseAudio Volume Control (pavucontrol) is a simple GTK+ based volume
control tool (mixer) for the PulseAudio sound server. In contrast to
classic mixer tools this one allows you to control both the volume of
hardware devices and of each playback stream separately. It also allows
you to redirect a playback stream to another output device without
interrupting playback.

For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

