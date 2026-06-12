---
title: "Output audio to a specific audio output device on a per-program basis"
date: 2013-05-13
forum: Multimedia Software
---

### Post by Shamino on 2013-05-13
Is it possible to route audio to a specific output device on a per-program basis? And if yes, what's the best way?

So, here's the situation - I have two audio output devices (sound card and HDMI). I would like to have one program output through the HDMI and another program output through the sound card.

I am using Ubuntu 12.04

---

### Post by kostkon on 2013-05-13
Yes, you can, easily. Just install the PulseAudio Volume Control utility (pavucontrol).

Hope that helps.

---

### Post by Shamino on 2013-05-14
I checked PulseAudio Volume Control, but I did not see any options to change the output device for a specific program.
I have attached an image of what I see in pavucontrol Playback. I have also attached what I see in my sound settings.

[ATTACH=CONFIG]242570[/ATTACH][ATTACH=CONFIG]242571[/ATTACH]

---

### Post by kostkon on 2013-05-14
Strange, you should be seeing something like what is being shown in the attached screenshot.

EDIT: just saw your 2nd screenshot. Does the 'speakers' device work when you set it as the default output device?

---

### Post by Shamino on 2013-05-17
Yes it does.

I wonder how come I do not see the same options you see...

---

### Post by Shamino on 2013-05-21
Found a solution from here:

[https://wiki.archlinux.org/index.php/PulseAudio/Examples]("https://wiki.archlinux.org/index.php/PulseAudio/Examples")

Specifically, choose the default output in Ubuntu's volume control, then in pacmd, run:

```
load-module module-alsa-sink device=hw:x,x
```

Where hw:x,x is the other output device (the one not set to default).

Once this is done, then both outputs will show up in pavucontrol.

---

