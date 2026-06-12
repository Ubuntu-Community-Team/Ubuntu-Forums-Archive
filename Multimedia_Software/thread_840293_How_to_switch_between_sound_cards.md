---
title: "How to switch between sound cards ?"
date: 2008-06-25
forum: Multimedia Software
---

### Post by JackD on 2008-06-25
I have a T61, and everything is working pretty well (even a twin-head monitor setup with urandr). However, I have an external USB audio system that I'd like to be able to switch over to when the laptop is set in the docking station. I've read all the sound troubleshooting tips, and done several searchs, but I'm not even sure how to define the problem.

Current status:

- both sound systems work fine. Using system/preferences/sound I can successfully put tones through each system. 
- "aplay -l" and "lspci -v" both show the two devices (internal and USB)
- alsamixer sees the two devices, but I can't switch with it.
- changing the /etc/module.d/alsa-base settings for the USB device doesn't seem to make a difference.
- "asoundconf list" shows the two devices, and "asoundconf set-default-card device" will set the USB device for default. However, when the laptop is undocked, there is no switchover to the internal sound system.
- I then tried installing pulseaudio tools, but there doesn't seem a way to switch the sound systems (and now, I can't get the "asoundconf" to set the USB as default, but I'm guessing I need a deeper study of the pulseaudio tools).
- after installing the pulseaudio tools, the "asoundconf" settings no longer allow activating the USB device (but, it still tests as good).

Is there an audio device switcher? 

Or a way to set a default USB audio that would allow the internal audio to become active when there is no USB audio ?

---

### Post by markbuntu on 2008-06-25
As far as I know, there is no automatic audio card switcher and I never found a way to switch cards with pulseaudio that was relatively easy so I disabled pulseaudio and use alsa and asoundconf.gtk.

Pulseaudio basically sabotages alsa and makes it unusable.

I suppose you could write some sort of script to change asoundconf when the usb card is unmounted but I have no clue about how to do that. Other than that, you can go back to alsa and then use System/Preferences/Default Sound Card (asoundconf.gtk) to change cards when you dock/undock. It is just a few clicks of the mouse.

---

### Post by JackD on 2008-06-26
Well, I agree. I'm going to do what I can to disable pulseaudio and run through alsa. I have to say that the sound system is quite byzantine. Thanks !

---

### Post by aeiah on 2008-06-26
you'll have to write a script but it shouldnt be too tricky. or you could just have a button that switches it which would be easier but a bit more clumsy.

you might have to write a daemon if you want it automated. this daemon will trigger your 'asoundconf set-defaut...' command

---

### Post by MemoryDump on 2008-06-26
> **JackD said:**
> I have to say that the sound system is quite byzantine. Thanks !

yeppers.. pulse isn't ready for prime time! At least not until other dev/projects support it better (1 of them being Wine)

you'd think there would be a nice tool to setup everything, such as default card, switcher, mic, headset, speaker setup (2.0 4.1, 5.1, etc), etc.. having to modify a half dozen files manually isn't exactly user friendly.

---

### Post by JackD on 2008-06-27
OK ! Good News. Working with alsa is clearly the fix. I read the alsa documentation, redid my Internet searches and found some solutions. I followed the steps from [http://flavor8.com/index.php/category/howto/page/2/]("http://flavor8.com/index.php/category/howto/page/2/") and everything works.

It's not perfect, but it's workable.

---

### Post by kortas on 2011-03-22
what about:

pacmd set-default-sink [index number]

---

