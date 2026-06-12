---
title: "High-pitched noise at startup"
date: 2009-04-06
forum: Multimedia Software
---

### Post by jolindbe on 2009-04-06
Hi!

I've read a couple of threads with people having similar issues, but nothing has helped, so I try creating an own one. Here goes:

First, sound has been working well earlier, this is something that changed recently. I have a Dell Latitude D830 with a docking station, and this weekend I decided to fix some trouble where Skype had a conflict with Rhythmbox and Flash applications while the computer was docked. I followed the steps in this guide: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) (which I have used to solve this problem when the laptop is un-docked, but this did not help for the docked setup).

Since then, a screeching, high-pitched noise/beep at maximum volume comes out of my speakers, starting somewhere halfway through booting, and continuing indefinitely - until I plug something into the headphone jack to silence it (if I plug in headphones, the noise comes out of them instead). The noise is independent of mute, volume change, etc. If I play a sound, I still only hear the noise. I have tried to uninstall ALSA and pulseaudio, nothing helps. I have also gone through the Comprehensive Sound guides in this forum without success.

While tweaking around with the ALSA installation, I now also get an error message after logon, telling me that something is wrong with the certificate for bugtrack.alsa-project.org:443. This error, however, started after the noise error started.

I have no issues at all in Windows Vista (the computer is dual-boot), neiter in Ubuntu when the computer is in its docking station.

I am quite new to Ubuntu, so the more basic steps you include, the better (I know how to start the terminal, execute commands as root, but not much more than that.)

---

### Post by WatchingThePain on 2009-04-06
Hi,

This is something you've probably already tried, but turning off wifi can help.
The sound is likely due to interference.

---

### Post by jolindbe on 2009-04-06
> **WatchingThePain said:**
> Hi,

This is something you've probably already tried, but turning off wifi can help.
The sound is likely due to interference.

Nope, doesn't help. And the wifi is turned on even in the docking station, so it should be unrelated.

I copied the error message from ALSA (which might not be related):
(I am using a Swedish version of Ubuntu, so I have translated it.)

"bugtrack.alsa-project.org:443 is using an invalid security certificate.

The certificate is not trustable since the issuer certificate is not trustable.

(Error code: sec_error_untrusted_issuer)"

More info: I have tried all the suggestions in this thread without success: [http://ubuntuforums.org/showthread.php?t=310938](http://ubuntuforums.org/showthread.php?t=310938)

---

### Post by jolindbe on 2009-04-06
Btw: If anyone knows a way of resetting all audio settings and drivers to the original settings without doing a clean re-install, that might be very helpful to me.

---

### Post by jolindbe on 2009-04-06
Progress!

I reinstalled Pulseaudio again, but that didn't help. But then I went into the volume control and disabled "Capture: ALSA PCM on front:0 (STAC92xx Analog) via DMA (PulseAudio Mixer)". Thus, I turned off my desktop microphone, which solved the problem.
But why does this happen, and can I get my mic working again?

---

### Post by jolindbe on 2009-04-06
Update:
I think this might be related to sinks, sources and captures, but I don't really know.
My default sink is "alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0", and default source is "alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0.monitor". With this configuration, I have no noise, but the microphone is not working. If I instead activate "alsa_input.pci_8086_284b_sound_card_0_alsa_capture_0" as the default source, I get the horrible beep. The sound input now gets a signal in the PulseAudio Volume Meter, but this signal is not related to me tapping on the microphone.

If I in the Ubuntu Volume Control go to the tab "Alternatives", and change the "Input Source" (which have two identical drop down menus, with alternatives "Mic" and "Front Mic") both to be "Mic", the beep changes to a buzz (not as strong as the horrible beep). Still nothing through the mic, though.

---

### Post by jolindbe on 2009-04-10
*bump*

Any ideas of how I get the mic working without a horrible beep at all times?

---

### Post by jolindbe on 2009-04-25
Finally, solved the problem. Just in case anyone else gets the same:
In the volume control, under the "Switches" tab, disable Analog loopback. I have no idea what this is for, or why I had enabled it, but disabling it killed the noise!

---

### Post by woodbrick on 2009-06-10
Hi JolinB. THanks for posting on this. I have a very similar problem. I am using pulseaudio server on Intrepid (8.10). I have also followed the howto you mentioned. 

The source of the noise in my case seems to be the front mic input, which I can mute in the Gnome ALSA mixer application. I still have some background noise (not as bad) even when this input is muted, and obviously any mic plugged into the input will not work.

You mention a "switches tab". I can't find this. Can you give more direction?

---

### Post by woodbrick on 2009-06-18
OK I figured it out. Way down at the far end of alsa mixer, which I opened using this command:

alsamixer -Dhw

I found a "mic booster" channel. As soon as I dropped the fader on this channel, Presto! Annoying sound gone!

---

