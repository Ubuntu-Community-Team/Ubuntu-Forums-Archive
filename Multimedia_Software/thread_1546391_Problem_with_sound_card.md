---
title: "Problem with sound card"
date: 2010-08-05
forum: Multimedia Software
---

### Post by zumus on 2010-08-05
Hi all! I've just updated my Koala to Lynx and got some strange problems with my soundcard.

At the beginning everything used to work fine, but at one day sound disappeared. I can see the soundcard device in the list of attached devices, all kernel modules and drivers are installed and seem to work properly, my audio device is listed in PulseAudio configuration tool and enabled, but there is no sound =(

I tried to renew my pulseaudio configuration, as i found here at the forum but it didn't help. So i have no ideas how to solve my problem.

---

### Post by zumus on 2010-08-05
Some additional info: audio device is CA0106 and the same audio device is chosen as default audio output, and the mode of device is Analog Stereo Duplex.

As i can see, my device works well as input because i see some noise in input mixer but i cant' test it 'cause i don't have a microphone . And of course speakers are fine.

---

### Post by lidex on 2010-08-06
Try removing your old pulse config files:
```
rm -r ~/.pulse
```
Reboot

---

### Post by uylug on 2010-08-06
> **lidex said:**
> Try removing your old pulse config files:
```
rm -r ~/.pulse
```Reboot

That should work... though It might be a better idea to move the folder, just in case they don't wanna lose their settings.

You could also create a new user, and see if things work from the different environment.

---

