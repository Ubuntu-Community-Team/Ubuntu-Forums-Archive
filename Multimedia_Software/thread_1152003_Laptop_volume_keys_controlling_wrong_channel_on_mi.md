---
title: "Laptop volume keys controlling wrong channel on mixer"
date: 2009-05-07
forum: Multimedia Software
---

### Post by inspired on 2009-05-07
Hi folks,
I have a volume up and down and mute key on my laptop.

Some time ago it worked fine. It would control the Master Volume sound output channel.

Then, at some point, it stopped working. I think this happened when I followed a bunch of instructions to finally get Pulseaudio working properly. All audio now works perfectly. Except for the volume (and mute) controls mapping to the wrong channel.

They currently appear to control the Microphone output channel. This is the channel that controls the volume of mic input playing through the speakers. Why it switched to controlling that, I have no idea. Seems pretty random.

I have looked into the Keyboard Shortcut config... here is what they map to:
- Volume mute = XF86AudioMute
- Volume down = XF86AudioLowerVolume
- Volume up = XF86AudioRaiseVolume

I would greatly appreciate it if someone were able to tell me where do I change what channel is being controlled by these buttons?

With much thanks...

Jonathan

---

### Post by inspired on 2009-05-12
Okay... just a note to say that I figured out how the mapping works. Very simple. Hadn't noticed it before.

In the volume control window one simply selects the track in the white panel at the bottom that lists the various tracks under a mixer drop down selection box.

:guitar:

---

