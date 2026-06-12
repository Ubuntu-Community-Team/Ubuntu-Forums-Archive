---
title: "Phonon crashes when advancing a track in Amarol"
date: 2010-06-25
forum: Multimedia Software
---

### Post by devehf on 2010-06-25
I have experienced that Phonon will crash occasionally when I advance to the next track in Amarok. After Phonon crashes, Amarok can't play sound. The only remedy appears to be restarting.

I would like to avoid the crashing. I have heard that Phonon and PulseAudio do not work well together. I would like to know how to disable PulseAudio when using Amarok. Any hints?

I am using the Xine backend in Amarok. In the Config Phonon window, I have  configured Phonon's hardware preferences to work directly with the sound hardware on the MoBo first. I have deprioritized PulseAudio to the bottom of the hardware list. Unfortunately the "remove" button is grayed out in the Phonon config window.

I am running Ubuntu 9.10 - the Karmic Koala w/ Gnome so I don't want to uninstall PulseAudio.

Thanks,
Dave

---

### Post by ADani on 2011-03-13
Same problem here. Laptop with Kubuntu 10.04 and Amarok 2.3.
I recently installed pulseaudio to solve my mic-in problem. Now Amarok crashes my sound card (I get a phonon message saying it's no longer working). In my case it doesn't happen every time I advance a track, but apparently having a youtube video playing at the same time always makes it crash.
The only solution I found is rebooting.

---

### Post by devehf on 2011-03-13
I suspect that the issues have to do with the backend you are using. I have switched from Xine to GStreamer. I still get segmentation fault crashes that randomly occur. But at least I can just restart the app instead of having to restart the OS.

People have said that version Phonon 4.4.4 resolves the crashing issue. I can't figure out how to compile it though.
[http://apachelog.wordpress.com/2011/01/21/phonon-family-4-4-4/]("http://apachelog.wordpress.com/2011/01/21/phonon-family-4-4-4/")

I think that version is coming with Natty.
[http://packages.ubuntu.com/natty/sound/phonon-backend-gstreamer](http://packages.ubuntu.com/natty/sound/phonon-backend-gstreamer)

---

### Post by ADani on 2011-03-14
Oh, thanks for shedding some light on this noob :)
I think I'll wait for kubuntu 11.04 and see, compiling is a bit out of my league for now.

---

### Post by rallen71366 on 2011-04-13
I'm currently running the Kubuntu 11.04 beta, and Phonon goobered up during the install, now when I play any format of video my system crashes enough to log me out. I don't want to uninstall/reinstall Phonon because it looks like the entire media playback system rides on it. My audio is working fine. Amarok is working great. Is there a way to have apt-get re-install Phonon?

Thanks for any help.:)

---

