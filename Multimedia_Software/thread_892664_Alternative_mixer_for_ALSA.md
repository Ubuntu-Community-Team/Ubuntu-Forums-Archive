---
title: "Alternative mixer for ALSA?"
date: 2008-08-17
forum: Multimedia Software
---

### Post by elecompte on 2008-08-17
I was wondering if there is any other mixer applications other than alsamixer. I am looking for something that can adjust volumes according to program. For example, many times, I would like to have SeaMonkey at a low volume, but I want Amarok up at max.

---

### Post by kostkon on 2008-08-19
> **elecompte said:**
> I was wondering if there is any other mixer applications other than alsamixer. I am looking for something that can adjust volumes according to program. For example, many times, I would like to have SeaMonkey at a low volume, but I want Amarok up at max.
*PulseAudio* maybe? It is the default mixer in 8.04. So if you use 8.04 then you'll have to install the *PulseAudio Device Chooser* utility (its package is called *padevchooser*).

If you don't use 8.04 then you will have to install *PulseAudio* yourself from *Synaptic*.

If you run it (it will be in your *Applications -> Sound & Video* menu) its icon will appear in your taskbar. Left-click on the icon and then select the *Volume Control*. From there you will be able to control the volume levels of every application separately (and some other things you'll discover yourself).

If you want to make it to start every time your desktop loads, then left-click on its icon, select *Preferences* and enable the *Start applet on session login* option.

But in order for this to work 100%, you will have to follow [this how-to]("http://ubuntuforums.org/showthread.php?t=789578") in order to make any application that uses *ALSA* directly, to work with *PulseAudio*.

---

