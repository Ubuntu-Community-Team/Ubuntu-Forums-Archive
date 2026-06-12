---
title: "Relationship between pulseaudio and alsa"
date: 2012-04-11
forum: Multimedia Software
---

### Post by PeterTaps on 2012-04-11
Folks,


I understand that pulseaudio is the new thing in Ubuntu and it has a plugin to make alsa work through pulseaudio. I also understand that alsa is more reliable than pulseaudio at the moment.

I am trying to get six channel out on the onboard audio. By following the following link, I got it to work:

[http://www.webupd8.org/2009/06/enable-surround-sound-in-ubuntu-linux.html](http://www.webupd8.org/2009/06/enable-surround-sound-in-ubuntu-linux.html)

What I am confused about is the relationship between pulseaudio and alsa in this case. How can modifying /etc/pulse/daemon.conf (which is at the topmost stack) change the behavior of speaker-test (which is at a lower stack)?

Also, how can you find out if pulse-audio is using alsa and not some other plugin?

Thank you in advance for your help.

Regards,
Peter

---

### Post by kostkon on 2012-04-11
Both of them work together. PulseAudio is a software sound server. It "sits" on top of Alsa.

Alsa provides the means (drivers) that allows the OS and the rest of the software to communicate with the audio hardware. It also provides a simple mixer (dmix) but in Ubuntu (and Gnome, in general) it is replaced by PulseAudio.

Thus, in simple words, PulseAudio takes the audio from Alsa, mixes it and maybe applies various other modifications to it and then it sends it back to Alsa in order to be played back by the hardware.

There is an PulseAudio Alsa plugin; what it does it that allows PulseAudio to take over the role of dmix and thus any application that it's written to send its audio to dmix (and not directly to PulseAudio) will not know the difference.

Hope that helps a little.

---

### Post by kostkon on 2012-04-11
Here
> Alsa provides the means (drivers) that allows the OS and the rest of the software to...
I meant to say
> Alsa provides the means that allows the OS (drivers) and the rest of the software (library) to...(

---

### Post by PeterTaps on 2012-04-12
Thank you for your help.

I am working on configuring the sound part of a media server device based on Ubuntu. It is a requirement that 5.1 surround must work from onboard 5.1 channels, onboard SPDIF output and onboard HDMI output. Another requirement is that the sound must be stutter-free. 

Given these requirements, I would like to get your (and other's) recommendation on whether I should use alsa or pulseaudio. The media server is a commercial device. The only application it will ever run is only one instance of VLC.

Appreciate your help.

Regards,
Peter

---

### Post by PeterTaps on 2012-05-23
I got alsa to work as expected. Here are my findings. Hope others may find them useful.

1. PulseAudio may depend on alsa but alsa does not depend on PulseAudio.

2. Even if you don't get any speaker sound from PulseAudio, it is okay. As long as alsa is working, any other alsa-aware application such as vlc will work fine. All you need to do is make sure that you specify proper alsa hw device.

Regards,
Peter

---

