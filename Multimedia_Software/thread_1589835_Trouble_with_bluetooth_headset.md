---
title: "Trouble with bluetooth headset"
date: 2010-10-07
forum: Multimedia Software
---

### Post by lupusnoctu on 2010-10-07
I have a bluetooth headset that I use for voice chat, but I've been having some trouble with the microphone since switching back to Ubuntu from that last round of disappointments with Windows 7. 

I can pair and connect the headset just fine, but I cannot adjust the playback or recording volume.  The playback volume isn't so much of a problem as my headset has buttons to do that on it's end, and it doesn't fluctuate at all on the computer's end. But the recording volume is a massive problem. Usually it is WAY too quiet. My friends in Ventrilo (I actually use Mangler) have to turn me WAY the heck up. But once in a while, especially if I reboot without disconnecting the headset first, the recording volume sky-rockets to the point were an almost inaudible whisper sounds like I'm yelling, and talking becomes nothing but garbled, clipped, static garbage. I have tested to see if it was Mangler by using gnome-sound-recorder, and the audio I'm getting from that matches what they're describing on Ventrilo exactly.

I have tried to adjust both recording and playback volume for the headset through PulseAudio in Sound Preferences, but that has no effect. I have also tried running alsa-mixer on the command line, but that only lets me choose my computer's built-in soundcard, and none of the sliders affect my headset. I have also found that when the microphone is being amplified, if I unplug the bluetooth radio on my computer, then plug it back in and reconnect my headset, it goes back to being too quiet.

My question: how do I adjust the volume, especially recording volume, for my bluetooth headset, and is there a way to completely fix these issues?

I'm running Ubuntu 10.10
pulseaudio 0.9.21-63-gd3efa-dirty

---

### Post by lupusnoctu on 2010-10-07
Hate to do this, but... BUMP!

---

### Post by P4man on 2010-10-07
You sure it doesnt show up in the sound preferences? 
You can try installing the package "paman" then run it, go to devices, select the bluetooth source , properties and adjust there?

---

### Post by lupusnoctu on 2010-10-09
> **P4man said:**
> You sure it doesnt show up in the sound preferences? 
You can try installing the package "paman" then run it, go to devices, select the bluetooth source , properties and adjust there?

Thank you for the reply. After reading the preview of my post, I realized I might be coming off as condescending below. Please don't take it as such, I am merely trying to point out details you appear to have missed in my original post. It's for everyone's benefit. :)

I'm sure it DOES show up in PulseAudio when I open the "Sound Preferences". Like I said, the sliders for the volume on my headset have no effect, but they ARE THERE. It was never an issue of PA not seeing the headset. Where I said it DOES NOT show up is in ALSA-MIXER, where it does not show any cards except for my laptop's built in audio device.

I tried installing paman to see if that would fix it anyways, or yeild further clues.  When I tried to change the volume sliders for my headset in paman, they would move, then when I released the mouse button, they'd snap back to where they were. I've seen something like that once before, back in the days of Ubuntu 8.x with USB headsets. If memory serves, it was a permissions issue. Could that be happening here? If so, how do I check for it? I wouldn't even know where to begin checking for such a thing with a Bluetooth headset.

---

### Post by lupusnoctu on 2010-10-12
Anyone? Or is it really that uncommon to use Bluetooth?

---

