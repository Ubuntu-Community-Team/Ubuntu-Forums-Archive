---
title: "Ubuntu 13.04, sound ok but can't access audio peripheral"
date: 2013-09-21
forum: Multimedia Software
---

### Post by matteo-dagord on 2013-09-21
Hello,
I've recently upgraded to Ubuntu 13.04 64bit and all was well, since I probably messed up something after using Skype internal audio setting.
In short, audio and system sounds are normally reproduced by os and all applications, but I can't access audio settings in the control panel: I mean that when I open audio settings I don't see any peripheral... so I can't manage system volume too... (even if I can adjust it by the internal mixer of the single applications). :confused:
This happens only using my main user account; other accounts works fine, so I think it's a permission issue. Any ideas?
Thank you in advance!

---

### Post by Yellow Pasque on 2013-09-21
Try resetting user pulse config and restarting pulseaudio (as affected user):
```
rm -r ~/.config/pulse; pulseaudio -k
```

---

### Post by matteo-dagord on 2013-09-22
> **Temüjin said:**
> Try resetting user pulse config and restarting pulseaudio (as affected user):
```
rm -r ~/.config/pulse; pulseaudio -k
```

Hmm... it say's that the directory doesn't exists and, moreover, that pulseaudio daemon is not running.

If a try with a simple
```

pulseaudio

```

I obtain this result
```

W: [pulseaudio] authkey.c: Failed to open cookie file '/home/matteo/.config/pulse/cookie': File o directory non esistente
W: [pulseaudio] authkey.c: Failed to load authorization key '/home/matteo/.config/pulse/cookie': File o directory non esistente
E: [pulseaudio] module-ladspa-sink.c: Master sink not found
E: [pulseaudio] module.c: Failed to load module "module-ladspa-sink" (argument: "sink_name=ladspa_output.mbeq_1197.mbeq master= plugin=mbeq_1197 label=mbeq control=5.3,2.6,2.6,-8.5,-10.5,-11.2,-16.0,-14.7,-6.6,-5.7,-3.0,3.0,6.7,7.3,7.3"): initialization failed.
E: [pulseaudio] main.c: Module load failed.
E: [pulseaudio] main.c: Inizializzazione del demone non riuscita.

```

So it seems there is a missing module...
I tried to completely remove and then reinstall pulseaudio, but nothing changes... (by the way, audio is reproduced normally even if pulseaudio is uninstalled :confused:: is it normal?)

---

### Post by Yellow Pasque on 2013-09-22
> So it seems there is a missing module...
No, the module won't load because "Master sink not found" (maybe because pulseaudio can't access the sound device).
Did you have Skype running when you tried to start pulseaudio?

---

### Post by matteo-dagord on 2013-09-22
> **Temüjin said:**
> No, the module won't load because "Master sink not found" (maybe because pulseaudio can't access the sound device).
Did you have Skype running when you tried to start pulseaudio?

No, I don't have Skype running.
Sound works but can't manage sound devices: it seems a permission issue, again...

---

### Post by Yellow Pasque on 2013-09-22
Did you change permissions in /etc/group?

```
since I probably messed up something after using Skype internal audio setting.
```
Be more specific.

---

### Post by matteo-dagord on 2013-09-23
> **Temüjin said:**
> Did you change permissions in /etc/group?
No... or at least not intentionally

> **Temüjin said:**
> ```
since I probably messed up something after using Skype internal audio setting.
```
Be more specific.

I mean that in audio settings default device didn't work so I had to manually selected the proper one (I have a usb webcam/microphone)
Moreover, I unchecked the "let skype adjust mixer" option.
I had a Skype call and at the following login my audio devices disappeared.
Even reverting to Skype default settings (or unisntalling it) doesn't fix anything.

---

### Post by Yellow Pasque on 2013-09-23
Let's look at: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

