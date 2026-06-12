---
title: "Sony Vaio volume control"
date: 2008-11-29
forum: Multimedia Software
---

### Post by dbhsatx on 2008-11-29
I have an issue that I would say is not a problem but an inconvenience.

I have a Sony Vaio FZ series laptop. I was having trouble getting the internal microphone working until I found in another thread that this line "options snd-hda-intel model=vaio" added to the alsa-base file then opening the volume control and selecting the mic under the switches tab has fixed the problem for other vaio laptops. It worked great for me as well until later when I was listening to some music and tried to turn down the volume with the jog-dial. The volume icon popped up on the screen and indicated the volume was going down but there was no change in the level. I suspected that the change I had made to the alsa-base file was the cause so I went into the file and commented the line out and rebooted and the jog-dial started working again but the mic didn't

I am running Ubuntu 8.10 with the latest updates as well as the latest version of ALSA

The attachment is the output of lspci with other info.

---

### Post by dbhsatx on 2008-11-29
*bump*

---

### Post by barrin on 2010-02-16
I have exactly the same problem with Ubuntu 8.04 on Sony Vaio VGN-FZ21E. This site

[http://www.palmix.org/vaio-en.html](http://www.palmix.org/vaio-en.html)

Have the following steps:

1)Install ALSA 1.0.15 (or above):

    alsa-base
    alsa-oss
    alsa-utils

Create the file /etc/&#8203;modutils/&#8203;alsa
and insert:

# ALSA portion
       alias char-major-116 snd
       alias snd-card-0 snd-hda-intel
       # module options should go here
       
       # OSS/Free portion
       alias char-major-14 soundcore
       alias sound-slot-0 snd-card-0
       
       # card #1
       alias sound-service-0-0 snd-mixer-oss
       alias sound-service-0-1 snd-seq-oss
       alias sound-service-0-3 snd-pcm-oss
       alias sound-service-0-8 snd-seq-oss
       alias sound-service-0-12 snd-pcm-oss

and save.
Now add at the end of the file /etc/modprobe.d/alsa-base the line:

options snd-hda-intel model=vaio

and add at the end of the file /etc/modprobe.d/sound:

alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel index=0 model=vaio

Save the files.

I don't know if it works, but may help.

---

