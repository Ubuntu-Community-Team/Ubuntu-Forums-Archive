---
title: "No sound for Flash Video in Firefox, Kubuntu 10.10"
date: 2010-11-06
forum: Multimedia Software
---

### Post by derrick1985 on 2010-11-06
Hi,

I am having a problem getting sound to work in flash-videos in Kubuntu 10.10.

My system currently has two working sound cards, the one integrated into my motherboard and the other is a USB Logitech headset. After installation, the speakers were set as my default output device which I did not want. I was able to move all the sounds over to the USB headset using phonon. While Amarok works, videos work (downloaded, wmv, avi, divx, etc) I cannot get flash video to work in Firefox. I set up my prefered device as the USB headset for everything in Phonon, but still the sound will only come out of my integrated soundcard (speakers). 

I'm not sure what exactly I am missing, I set everything up, but still it's a no go. What switch did I miss? I haven't used Kubuntu for a while, but i'm pretty sure this worked fine in Ubuntu 9.04 (when I last used it). 

Thanks in advance.

---

### Post by efflandt on 2010-11-06
Flash uses default **alsa** sound (whatever shows up as default in **alsamixer**) instead of **pulse** audio.  I don't know if KDE uses pulse audio, but in gnome to have flash sound come from whatever I set as the Output device in gnome Sound Preferences (which uses pulse audio) I have to put the following in /etc/asound.conf (I created that file which did not exist).  But make sure that you do not have ~/.asound in your home directory that contradicts anything in /etc/asound.conf.

Try **sudo nano /etc/asound.conf** (or **gedit** instead of nano) and put the following in that file:

```
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}
```After I did that, flash audio uses whatever Output I set in gnome Sound Preferences. If that does not work simply **sudo rm /etc/asound.conf** and find out what KDE uses for sound instead of pulse audio.

If you ever get a video card that has HDMI, you may need to do something additional to get HDMI audio working.

---

### Post by m_zeid on 2010-11-06
Hi

from synaptic install :PulseAudio Volume Control & PulseAudio Volume Meter.

after installing them you can find them in applications>sound & video.
I'm still a beginner here but I know that this will help for sure.You still can google about it to know how to use use it for your needs. By using it you can choose which sound card plays the sound for a specific program.
I've used it once and solved my problems.

---

### Post by derrick1985 on 2010-11-07
> **m_zeid said:**
> Hi

from synaptic install :PulseAudio Volume Control & PulseAudio Volume Meter.

after installing them you can find them in applications>sound & video.
I'm still a beginner here but I know that this will help for sure.You still can google about it to know how to use use it for your needs. By using it you can choose which sound card plays the sound for a specific program.
I've used it once and solved my problems.

Perfect, that worked great! Of all the devices and outputs, it was set to Alsa mixer on my soundcard, instead of my headset. 

Thanks again, problem solved.

---

### Post by m_zeid on 2010-11-08
congrats
glad I can help :D

---

### Post by slegrand on 2012-01-26
Hey. I don't seem to have pulseaudio-volume control or meter in the repos?
Should I be enabling or adding a special source?

---

