---
title: "Logitech S-150 USB Digital Speaker"
date: 2009-08-19
forum: Multimedia Software
---

### Post by BuntuFirstTimer on 2009-08-19
I have Ubuntu 9.04 (AMD64) and there is a problem with my sound system. I can't find a way to work out my Logitech S-150 USB Digital Speaker.

As for System > Preference > Sound, I can't get the **HDA ATI ALC883 Digital (ALSA)** to sound-test it and it gets.

```
Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'
```

And as for the asoundconf list, I got

```
Names of available sound cards:
SB
default
```

Is there a way to make the sound work?

---

### Post by erikthedrink on 2009-09-08
I've got logitech usb speakers too.  In Xubuntu, go to Applications, then Accessories, then Terminal.  In Terminal, type

[FONT=Georgia][SIZE=4]asoundconf set-default-card 1[/SIZE][/FONT]

Then close and re-open your browser (Mozilla Firefox) or restart your system.
:P
Note, if you unplug your usb speakers, your laptop speakers will take over.  In order to re-establish contact with the usb speakers, you will need to (plug them back in) restart the system.
Also, replacing the one with a zero would also reset your sound to your laptop speakers.

---

