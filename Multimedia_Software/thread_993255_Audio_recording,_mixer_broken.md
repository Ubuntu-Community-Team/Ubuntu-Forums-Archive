---
title: "Audio recording, mixer broken"
date: 2008-11-25
forum: Multimedia Software
---

### Post by Rob Glenn on 2008-11-25
I have a desktop system that is generally unable to capture and record audio, either from the line input or from other running applications.  This was broken in Ubuntu 7.10, and with a new install of 8.10, still does not work.  Command line programs, such as arecord or esdrec, either record silence or crash, regardless of what settings I try in pavucontrol, system->preferences->sound, or alsamixer.  (I did find one precise combination that allowed the sound recorder app, specifically, to record from the line input, although I could not enable the line input to be heard through the speakers directly, or get it to work with any other apps.)

I've checked all the obvious things, such as correct sources selected in the mixer apps, unmuted, enabled for capture, volume level turned up.  Based on the fact that everything works as it should on an old laptop I have that is running Ubuntu, I expect this is some sort of low level ALSA driver or configuration issue that is specific to my desktop's hardware.  I have an Asus M2N motherboard with the nForce 430 chipset, and am using the onboard sound.

Searching other posts on the forums, I have not found an answer.

Can anyone give any suggestions for troubleshooting?  How can I validate that it is using the right driver and that it is configured properly?

Thanks!
Rob

---

### Post by Toet on 2008-11-25
Go to the /proc/asound directory.

Have a look at the following files:

cards
devices
pcm

At my pc, I have to do this from the terminal/command line:

> cat /proc/asound/cards
etc.

You can also check the other files and subdirectories.

---

### Post by Rob Glenn on 2008-11-26
OK, I did this, here is what I got.

rglenn@cydonia:/proc/asound$ cat devices
  2:        : timer
  3:        : sequencer
  4: [ 0- 1]: digital audio playback
  5: [ 0- 0]: digital audio playback
  6: [ 0- 0]: digital audio capture
  7: [ 0]   : control
rglenn@cydonia:/proc/asound$ cat modules
 0 snd_hda_intel
rglenn@cydonia:/proc/asound$ cat cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xdddf8000 irq 11

It seems to at least have correctly identified the hardware.  Anybody know what else I might look for?

Thanks,
Rob

---

### Post by Toet on 2008-11-27
You could also try Audacity. You can configure the capturing port at it's config (Edit-Preferences-Recording). For some reason when having trouble with recording, Audacity always seems to help me.

---

### Post by Rob Glenn on 2008-11-30
I followed the directions in another post to download and install the newest alsa drivers (1.0.18a), and this has partially fixed the problem.  The arecord program now works for some cases.  It is now possible to record loopback sound by setting the capture input to "aux" (counter-intuitively, not "mix".  This seems wrong.)  However, it is still not possible to monitor line input through the speakers (although it can be recorded).

---

