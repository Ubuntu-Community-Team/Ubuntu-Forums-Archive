---
title: "Switch between soundcards (ALSA)"
date: 2011-01-09
forum: Multimedia Software
---

### Post by frankbooth on 2011-01-09
I've been trying to figure out how to easily switch between two soundcards (one integrated and one USB soundcard). With PulseAudio it's rather simple, but with ALSA it's a different story.

I'd like to create a script (or two scripts) that switches between my integrated soundcard and USB soundcard.

What I've tried so far:
```

user@computer:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC259 Analog [ALC259 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Headset [Sennheiser USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

With this information I created a file called '.asoundrc' in my home folder:
```

pcm.!default {
	type hw
	card 1
}
ctl.!default {
	type hw
	card 1
}

```

Hoping that this would make my system use the USB soundcard (since aplay labeled it as 'card 1') as the default soundcard, it did not however. If I could get this working, or something similar, making scripts to change the configs shouldn't be too hard.

Any ideas how I can solve this?

---

### Post by efflandt on 2011-01-09
Someone did come up with a script to switch output to an added usb device, but I do not know what search terms can find it.  It used **pacmd** to have pulse switch the output, but was rather complicated.

Unfortunately **man pacmd** does not provide any details, but it apparently uses commands similar to statements in /etc/pulse/default.pa.  Some info is provided in **man pactl**, but all I was able to do with pactl was toggle an active sink (output) off or on.  It would be nice if there was a simple single command to change the default output sink for pulse.

---

### Post by frankbooth on 2011-01-13
Right, so I found this application called 'asoundconf-gtk' which features a GUI to switch between soundcards using only ALSA.

However... Switching soundcards didn't really work, it even b0rked my configuration so I ended up with no sound at all.

So I reverted all the changes in the end... But has anyone got it to work?

---

### Post by frankbooth on 2011-01-15
bump

---

### Post by frankbooth on 2011-01-15
bump

---

### Post by lidex on 2011-01-16
> **frankbooth said:**
> Right, so I found this application called 'asoundconf-gtk' which features a GUI to switch between soundcards using only ALSA.

However... Switching soundcards didn't really work, it even b0rked my configuration so I ended up with no sound at all.

So I reverted all the changes in the end... But has anyone got it to work?

It's been deprecated.

---

