---
title: "[success]Surround Sound on 8.04"
date: 2008-05-11
forum: Multimedia Software
---

### Post by kakyoism on 2008-05-11
It works perfect now after a few days of investigation.
Now I find no reasons to return to Windows anymore.

My recipe:
   0. Sony VAIO VGN-NR298D
   1. Soundcards: Builtin Intel (hw:0), SB Live! 24-bit 5.1 (hw:1)
   2. Sound device: pulse-audio (new in 8.04 Hardy Heron)
   3. There should be two ways of configuring surround sound: low-level one with ALSA, and through the high-level delegate pulse-audio.
   4. With ALSA I never succeeded by creating and tweaking the ~/.asoundrc, where I specified channel duplicates to route the PCM through all my available speakers; I referred to at least 5 different tips from online peer ubuntu users. But with pulse-audio you simply have to do this:
   5. in System -&gt; Preference -&gt; Sound, turn on pulse-audio as the devices for all audio applications, and use your surround-equipped soundcard as the hardware mixer.
   6. Install the package pavucontrol, which raises the linux speaker configuration to the Windows level (many linux hardcore followers hate to and have to admit it). By default the menu item is hidden in the Applications menu, you need to edit this utility to check it under the category Sound & Video.
   7. Under pavucontrol, you will see a dialog with three tabs. Look at the tab playback, right-click the labels on the left and check the checkbox that "moves the stream" to your surround device.
   8. Move on to the tab Output Devices, find your surround devices, and right-click the label again, check the checkbox default. You can go on with the Input Devices tab to select your default input device, but that's unrelated to the surround playback.
   9. Reboot and it's done.

I still keep one specific setting from the earlier ALSA attempt without testing what would happen by turning it off: under /etc/pulse/daemon.conf, uncomment the line with default-sample-channels, set the value to 6 if it is not there yet.

In general, pulse-audio does a pretty good job, although the GUI tool pavucontrol is not perfect; the right-click-on-label thing would be really confusing to a computer newbie who doesn't have the habit of wild clicks with the mouse.

Anyways, I'm listening to the excellent Deep Space Mix series from ASC, recommended by my friend from lab, on the Ubuntu-hosted surround-sound party!!

---

