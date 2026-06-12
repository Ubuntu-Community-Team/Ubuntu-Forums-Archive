---
title: "[SOLVED] How can I switch Pulse between two sinks easily?"
date: 2008-11-20
forum: Multimedia Software
---

### Post by Sirron on 2008-11-20
I'm using 8.10 and was very pleased to discover that this time Pulse Audio is delivering on its initial promises, out of the box.

I've got two sound cards; an xfi xtreme gamer (using the latest driver from Creative, which works perfectly in stereo), and an on-board 5.1 channel sound card (which has always worked fine).

I have a surround sound headset connected to the on-board card, and some old-yet-good quadrophonic speakers connected to the xfi. On Windows Vista, when I want to switch between headset and speakers, I just change the default sound device. No messing with cables.

With pulse audio, the only way I can see to do it is by using the PulseAudio Applet to select a new sink, and clicking "Other..." then pasting in the long name of the sound card I want to select;

alsa_output.pci_1102_5_sound_card_0_alsa_playback_0

For example.

Obviously, it's a pain having to keep a file with the names of the sound cards in it, and paste one into that box every time I want to switch.

Is there a way to get the sound cards to appear in the menu under "Default Sink" in the PulseAudio Applet? Or can I write a short script to change the default sink and create a launcher for it?

Thanks in advance!

---

### Post by psyke83 on 2008-11-20
Don't use the Device Chooser (it's handy for quick links to the various GUI tools, but the chooser itself is obsolete).

Open the PulseAudio Volume Control. On the Output Devices tab you can right-click on a sink and make it default. Additionally, on the Playback tab you can assign a different sink per-application (if needed). These settings are saved.

See: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by Sirron on 2008-11-20
> **psyke83 said:**
> Open the PulseAudio Volume Control. On the Output Devices tab you can right-click on a sink and make it default. Additionally, on the Playback tab you can assign a different sink per-application (if needed). These settings are saved.

Perfect, thanks a lot. The interface isn't the most straightforward I've ever seen, but it does appear cover all the features and more.

---

### Post by psyke83 on 2008-11-20
> **Sirron said:**
> Perfect, thanks a lot. The interface isn't the most straightforward I've ever seen, but it does appear cover all the features and more.

I'm in total agreement with you ;). Once you know about this functionality, however, PulseAudio seem a lot more useful.

---

### Post by markbuntu on 2008-11-20
If you want playback on both your sound cards at the same time you can go to Configure Local Sound Server in the PA dev chooser and check the box in the Simultaneous Output tab. This will put a virtual Simultaneous output..... device in the PA Volume Control that you can use like any other device.

---

