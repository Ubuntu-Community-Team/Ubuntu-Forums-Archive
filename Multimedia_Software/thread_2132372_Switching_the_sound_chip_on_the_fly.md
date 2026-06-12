---
title: "Switching the sound chip on the fly"
date: 2013-04-04
forum: Multimedia Software
---

### Post by Sworddragon on 2013-04-04
My system has a common sound chip and a HDMI port. Now I want to change the sound output to the HDMI port on the fly with the terminal. Is there a command to do this? Currently I'm solving this with a .asoundrc as a workaround but this is not on the fly.

---

### Post by CatKiller on 2013-04-05
Pulse Audio will quite happily shift audio streams around; it's what it's for. I only know how to do so in the GUI, though, not the command line.

---

### Post by Sworddragon on 2013-04-05
After looking a little more on Google it seems it would be possible to manipulate the .asoundrc and restart alsa. I will try later to put such a mechanism into a script.

---

### Post by CatKiller on 2013-04-05
You can find the indexes of your sinks with ```
pacmd list-sinks
``` and the indexes of any audio streams with ```
pacmd list-sink-inputs
``` and then it's simply a case of, in the case of moving stream index 2 to sink 0, say ```
pacmd move-sink-input 2 0
```
You can refer to the sinks by name instead if you prefer, which is probably advantageous since I think the numbers change on reboot. I haven't yet found another way of referring to the stream, and the index number could well be anything, but  if you're putting it in a script anyway there's no reason why you couldn't use some regex fun to look up the index number in the output of *list-sink-inputs*. Scripts already exist for this sort of thing, so that's a reasonable starting point.

More info at **man pulse-cli-syntax** or just something like searching for "pulseaudio command line move audio stream."

---

### Post by Sworddragon on 2013-04-06
On my system is no PulseAusio server running and these commands aren't available too (because it is a minimalistic system). Theoretically I could install a PulseAudio server but this would occupy some ressources so I'm looking for a more essential solution. Just if this fail I will take a look to PulseAudio.

---

### Post by CatKiller on 2013-04-06
If you're using ALSA, you might find it easier to route things to all outputs & selectively mute/unmute to get the signal you're after. Just a thought.

FWIW, it's only if you're doing significant resampling that Pulse uses much by way of resources. It doesn't use anything if there's no audio, and it's a couple of percent when there is. Might not be what you want if you're resource-constrained and don't want to put audio over the network or similar, though.

---

