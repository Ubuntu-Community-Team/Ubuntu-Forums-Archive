---
title: "Help - Acer notebook onboard mics not working"
date: 2009-02-02
forum: Multimedia Software
---

### Post by CraigFoote on 2009-02-02
Last week I obtained the Jaunty alpha and decide to give it a try. I backed up everything, installed it, saw it wasn't ready in a number of ways so decided to reinstall Intrepid with a full format and fresh install. Sound playback and recording (including Skype) had worked perfectly before all this but not now. I don't think I did anything special with my original Intrepid; it just worked out of the box. I can't imagine trying out Jaunty is involved because of the format and fresh install. I've reinstalled three times with the same result: I cannot record sound.

My machine is an Acer 5920G notebook and has two built-in microphones on either side of the webcam, as well as mic, line-in and headphone jacks on the front edge.

I've followed the excellent thread at [http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506) and I'm hoping someone here can point me in the right direction. Perhaps there's something evident in the displays while performing the prescribed steps.

Step 1: Set Sound preferences to "PulseAudio Sound Server" except Default Mixer Tracks which is set to "Realtek ALC888 (OSS Mixer)". The tracks listed at the bottom are: Volume, Line-in, Microphone, PCM-2, In-gain, Digital-1. Only Volume is selected.

Step 2: Panel Volume Control - Device is set to "Realtek ALC888 (OSS Mixer)". All sliders are at max and none muted.

Step 3: GNOME ALSA Mixer - Displays: Master, PCM, Front, Line, Mic (mic input jack?), Mic Boost (for mic input jack?), Capture and Capture (2 of them, hopefully representing onboard mikes). All are at max, both Captures have "Rec" checked, and the list at bottom has only Headphone checked; IEC958, IEC958 Default PCM, Input Source and Input Source (both) are unchecked.

Step 4: PulseAudio Device Chooser (panel applet): Volume Control: Output Device listed as "Alsa PCM on front:0(ALC888 Analog) via DMA". Both sliders are at max and neither muted (speaker icon not toggled on).

Step 5: Rhythm Box plays fine.

Thus ends the post but Sound Recorder hangs when I press its Record button and closing it causes a Force Quit dialog.

Something that I find unusual is the PulseAudio Device Chooser panel applet's "Volume Meter (Recording)" display. Both its meters are bouncing, one at about 40%, the other at 20%. Tapping the built-in mics causes them to jump to 100%, yet speaking at anything less than a shout has no effect.

So if anyone sees anything wrong with these settings or if you have any suggestions whatsoever I would greatly appreciate the help.

Craig

---

### Post by CraigFoote on 2009-02-02
Oops, meant to add that Sound Recorder's display shows "Record from input" as "Master", the only option available. Not sure where that comes from.

Craig

---

