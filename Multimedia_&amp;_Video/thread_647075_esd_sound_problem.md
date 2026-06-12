---
title: "esd sound problem"
date: 2007-12-21
forum: Multimedia &amp; Video
---

### Post by antbully on 2007-12-21
Hello,

I am new to Ubuntu, having come by way of gentoo (and redhat a long time ago).  I am trying to get sound to work sensibly and I've tried following a few threads but they either don't work or don't really apply.  I should say that sound *does* work, in a limited way.  I would like to get the full ESD experience, but so far, no can do.

Here's the setup: ASRock 939 Dual VSTA (AMD 64 x2) with onboard audio.  This shows up as a USB audio device.  I installed gutsy and have only installed updates since.

Output from [B]aplay -l
**** List of PLAYBACK Hardware Devices ****
card 2: default [PnP Audio Device        ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/B]

Now, I try to do alsamixer, but it fails with this message:

**alsamixer: function snd_ctl_open failed for default: No such device**

Going under System->Preferences->Sound, I find that sound only works if I select "USB Audio" from the Devices pulldown list.  Setting to ALSA gives this message when I click test:

**audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.**

Setting to ESD gives this message:

**audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not establish connection to sound server**

As I said, setting the Device to "USB Audio" does give me sound, but the volume control in the taskbar does not control the sound.  RhythmBox plays fine with USB Audio, but fails with "Could not open resource for writing" or "Could not establish connection to sound server" when using ALSA or ESD, respectively.

I have a Logitech iTouch keyboard and the volume control buttons bring up a nice on-screen display (looks like a Mac!), but does not affect the sound, since I'm using the USB Audio device.

I have also installed gutsy on a Pentium 3 laptop (IBM T23) and sound works just fine out of the box.  So I figure it must be something with my setup, but what?

Any and all clues welcome...

Antbully

---

### Post by antbully on 2008-01-08
Bump...

---

