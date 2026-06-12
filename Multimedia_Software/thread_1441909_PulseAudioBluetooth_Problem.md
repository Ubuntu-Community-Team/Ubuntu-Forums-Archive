---
title: "PulseAudio/Bluetooth Problem"
date: 2010-03-29
forum: Multimedia Software
---

### Post by tracyandskye on 2010-03-29
I'm trying to setup Skype and initially had only bluetooth as the device used.  I couldn't get it to ring through the speakers & still have calls through bluetooth.

So I removed Pulseaudio to use alsa which allowed me to choose devices but also crashed Skype.  The Skype folks are no help with the crashing & are pointing me back to PulseAudio.

The problem is that PulseAudio does not see my blutooth at all now.  I do have device chooser & volume control installed.  The bluetooth used to be listed under the sinks, but it's not there now.  

Here is what I have in Synaptic:

bluetooth
libgnome-bluetooth7
gnome-bluetooth
pulseaudio-module-bluetooth
bluez
bluez-cups
pulseaudio-module-bluetooth-dbg
libbluetooth3
bluez-gstreamer
bluez-alsa

---

### Post by tracyandskye on 2010-03-31
Is this the wrong forum for this question?

---

### Post by Boondoklife on 2010-03-31
What release are you using? If it is karmic or higher, I have had great luck with using blueman instead of the gnome bluetooth applet. Install it and give it another go, you can even get the answer/hangup to work from your headset if you are lucky!

---

