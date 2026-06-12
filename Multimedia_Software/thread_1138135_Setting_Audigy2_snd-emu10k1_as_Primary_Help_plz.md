---
title: "Setting Audigy2 snd-emu10k1 as Primary Help plz"
date: 2009-04-26
forum: Multimedia Software
---

### Post by exProphecy on 2009-04-26
Hello, I'm fairly new to Ubuntu and I'm having some trouble with my sound card. I went to System > Preferences > Sounds and set my Audigy2 as my sound for Sound Events, Music and Movies, etc. When I play music, the card works. When I play music from Firefox, the internal laptop speakers play. How do I change it so everything plays from my Audigy2 card?

---

### Post by kostkon on 2009-04-26
You need to install the *PulseAudio Device Chooser* from *Synaptic*. When you run it (it will have a menu entry in *Applications &#8594; Sound & Video*), right-click on its icon in the system tray and select *Volume Control*.

From there you will be able to select the default card for input and output. In the *Input Devices* and *Output Devices* tabs you should see your Audigy listed. Just right-click on it and enable the *Default* option to set it as the default input and output device.

For this to work you'll need to set your sound playbacks (i.e. for Sound Events, Music and Movies, as you said) in your sound preferences (i.e. *System &#8594; Preferences &#8594; Sound*) to *Autodetect*. You can do the same for your inputs, set them to *Autodetect*.

Hope that helps.

---

### Post by exProphecy on 2009-04-27
[FONT=Verdana][SIZE=1][COLOR=Purple]Ahh it worked! But when I played Pandora on Firefox, it didn't work right off. I had to go into "Volume Control" > "Playback" then change the ALSA plug-in [firefox]: ALSA Playback by right clicking it and "Move Stream" over to my Audigy2 ZS. Does it usually take this much work to make this specific card work? It's a Creative SoundBlaster Audigy 2 ZS Notebook. Is there another way to do it without having to install PulseAudio?[/COLOR][/SIZE][/FONT]

---

### Post by kostkon on 2009-04-28
> **exProphecy said:**
> [FONT=Verdana][SIZE=1][COLOR=Purple]Ahh it worked! But when I played Pandora on Firefox, it didn't work right off. I had to go into "Volume Control" > "Playback" then change the ALSA plug-in [firefox]: ALSA Playback by right clicking it and "Move Stream" over to my Audigy2 ZS. Does it usually take this much work to make this specific card work? It's a Creative SoundBlaster Audigy 2 ZS Notebook. Is there another way to do it without having to install PulseAudio?[/COLOR][/SIZE][/FONT]
Yes, you'll need to do this for some applications, not for many though. In theory, PulseAudio will remember your choice and the next time you will run this application it will use the same audio device for it.

Actually you didn't install PulseAudio. You just installed a utility that allows you to use some features of it, like the ability to move an audio stream from one device to another on-the-fly, individual volumes per application and some more. 

Anyway, PulseAudio comes with Ubuntu by default, it is a software audio mixer and let's say simply that it controls everything audio related on the desktop.

You can remove it, yes, but I wouldn't recommend it.

---

