---
title: "Skype Microphone and Sound OK"
date: 2009-09-19
forum: Multimedia Software
---

### Post by rykel on 2009-09-19
Hi all,

I frequently have problems getting Skype to work on Ubuntu Jaunty. (no sound and microphone not working)

I finally found a solution which I hope can help someone else here:

[B]> $ killall pulseaudio
$ sudo apt-get remove pulseaudio
$ sudo apt-get install esound
$ sudo rm /etc/X11/Xsession.d/70pulseaudio[/B]

Remember to Unmute the microphone under the Recording tab in Volume Control. (see screenshot)

---

### Post by Wokm4n on 2009-09-19
Thanks a lot! :)

---

### Post by wieman01 on 2009-09-19
The latest beta version (v2.1) works well with Alsa though.

---

### Post by rykel on 2009-09-21
Yes, the latest version is great. (Skype 2.1)

HOWEVER, on Karmic, my microphone is cracking and I am still troubleshooting the problem. Pulseaudio problem... again.   :)

---

### Post by rtalcott on 2009-09-21
Skype is working perfectly for me on Karmic 64 bit using the latest Skype....this is the first time it's worked perfectly....and it is definitely using PulseAudio.
rt

---

### Post by sherwinraavi on 2009-09-24
Ok, this didn't work for me. I'm getting frustrated. 

I'm on Jaunty using skype beta 2.1.0.47. I loaded Jaunty on a HP 6707us laptop that has mic and webcam built in. 

When I click on Volume Control, my devices are:
HDA Nvidia (Alsa Mixer)
Conexant CX20561 (Hermosa) (OSS Mixer)

Also, In the Sound Preferences, all the choices under sound capture results in the same error message which I have attached a screenshot of here. 

Can anyone help me PLEASE?

---

### Post by mao_dze_dun on 2009-09-25
Well I tried the given advice and now I don't have sound. Sure when I test it from the sound settings I hear a sound but other than that my PC is mute. I'll be really thankful if you can tell me how to reverse this. I liked my pc more without a working microphone, rather than with neither a microphone, nor sound.

---

### Post by hblaw on 2009-09-26
Removing pulseaudio (and installing esound) solved all problems of audio. This bloatware should be purged. hiahia. I am wondering what benefits pulseaudio gives us, other than the super function (for aliens) to play your audio to another computer. I have a feeling that the pulseaudio developers are using innocent users as testing rabbits (and very irresponsibly).

---

