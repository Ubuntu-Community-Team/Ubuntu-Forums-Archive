---
title: "Logitech v20 Speakers, Youtube, and ALSA"
date: 2009-03-10
forum: Multimedia Software
---

### Post by monkeys on 2009-03-10
I bought Logitech v20 USB speakers! Great for my Gateway laptop which has pretty quiet speakers. However, when I play videos on Youtube, the sound doesn't work unless I turn the Devices back to the laptop speakers (**ALSA** or **HDA Intel STAC92xx Analog (OSS)**).

Presently, I have configured the Sound -> Devices all to **Logitech Logitech USB Speakers USB Audio (OSS)**, with the exception of **Logitech USB Speaker (Alsa mixer)** for the** Default Mixer Tracks.**

I saw on another forum that if I set all the settings to ALSA (save for the Default Mixer Tracks) and set my soundcard to Speaker (already did) that my Youtube sound would play, however, whenever I do that only my laptop sound works.

Using **Logitech Logitech USB Speakers USB Audio (ALSA)** results in:
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open audio device for playback.
```

Any suggestions? s:

---

### Post by kostkon on 2009-03-12
> **monkeys said:**
> I bought Logitech v20 USB speakers! Great for my Gateway laptop which has pretty quiet speakers. However, when I play videos on Youtube, the sound doesn't work unless I turn the Devices back to the laptop speakers (**ALSA** or **HDA Intel STAC92xx Analog (OSS)**).

Presently, I have configured the Sound -> Devices all to **Logitech Logitech USB Speakers USB Audio (OSS)**, with the exception of **Logitech USB Speaker (Alsa mixer)** for the** Default Mixer Tracks.**

I saw on another forum that if I set all the settings to ALSA (save for the Default Mixer Tracks) and set my soundcard to Speaker (already did) that my Youtube sound would play, however, whenever I do that only my laptop sound works.

Using **Logitech Logitech USB Speakers USB Audio (ALSA)** results in:
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open audio device for playback.
```

Any suggestions? s:
Please see [my post here]("http://ubuntuforums.org/showpost.php?p=6855292&postcount=2"), if you like.

---

### Post by markbuntu on 2009-03-16
Go here

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by erikthedrink on 2009-09-08
I've got logitech usb speakers too.  In Xubuntu, go to Applications, then Accessories, then Terminal.  In Terminal, type

[FONT=Georgia][SIZE=4]asoundconf set-default-card 1[/SIZE][/FONT]

Then close and re-open your browser (Mozilla Firefox) or restart your system.
:P
Note, if you unplug your usb speakers, your laptop speakers will take over.  In order to re-establish contact with the usb speakers, you will need to (plug them back in) restart the system.

---

