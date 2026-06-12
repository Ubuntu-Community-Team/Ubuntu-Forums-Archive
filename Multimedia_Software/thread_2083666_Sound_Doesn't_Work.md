---
title: "Sound Doesn't Work"
date: 2012-11-13
forum: Multimedia Software
---

### Post by Yunito on 2012-11-13
Today I installed Gnome-Alsamixer because PulseAudio doesn't work very good, and I removed Pulseaudio. Then I wanted to listening music in my USB Headphone, for this reason I removed Gnome-Alsamixer and I reinstalled PulseAudio.

But when I want to listening to music normally (With or Without USB Headphone) the sound doesn't work.

Help-me, I searched information in Google and in this forum but I didn't finf the answer

Thanks
[EMAIL="mjcarrio@gmail.com"] [/EMAIL]

---

### Post by WiReIs on 2012-11-13
You checked your sound settings are ok?

System > Preferences > Sound

You must have a driver missing for your sound card or try a reboot

hope this helps

---

### Post by Yunito on 2012-11-13
I reboot the system, and my Audio Settings are Okey...

What's the problem?

---

### Post by Yunito on 2012-11-14
Please help me, I want to listening music and listening sounds

Sorry for double reply

---

### Post by Yunito on 2012-11-16
Up!

(Reply to search Answers)

---

### Post by BicyclerBoy on 2012-11-16
I find it unlikely that pulse audio has caused any of your problems..

Install/run pavucontrol

then check your configuration (far right tab) then check the output format..

pavucontrol can also save setups for individual apps.

The driver for the USB soundcard/headphones would have been alsa.
It is possible to use a pulse plugin for alsa (no pulse audio install) or it is possible to play directly to alsa device with "clementine" or VLC mplayer etc.
Pulse audio does not prevent this or interfere..

---

### Post by Yunito on 2012-11-20
> **BicyclerBoy said:**
> I find it unlikely that pulse audio has caused any of your problems..

Install/run pavucontrol

then check your configuration (far right tab) then check the output format..

pavucontrol can also save setups for individual apps.

The driver for the USB soundcard/headphones would have been alsa.
It is possible to use a pulse plugin for alsa (no pulse audio install) or it is possible to play directly to alsa device with "clementine" or VLC mplayer etc.
Pulse audio does not prevent this or interfere..

Pavucontrol doesn't work. 

It said: Fatal Error, Unabled to connect PulseAudio

---

### Post by BicyclerBoy on 2012-11-21
Either you did not re-install pulseaudio or pulseaudio server will not start.

Should be able to find some info in the log files..just not sure where..

Check your "user" is a member of the "pulse" & "pulse-access"  groups.

---

### Post by Yellow Pasque on 2012-11-21
> Should be able to find some info in the log files..just not sure where..[https://wiki.ubuntu.com/PulseAudio/Log](https://wiki.ubuntu.com/PulseAudio/Log)
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

One of the first things I try with pulse issues is moving the user-config files out of the way and letting it generate fresh ones:
```
rm -rf ~/.pulse*
```
Then, log out and back in.

---

### Post by Yunito on 2012-11-22
I think when I removed pulseaudio, I remove accidentaly some libs of pulseaudio, what can I do to solve all problems? :S

---

### Post by Yunito on 2012-11-26
Any Help?

---

### Post by Yunito on 2012-11-30
Please helpme

---

