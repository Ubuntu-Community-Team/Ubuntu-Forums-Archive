---
title: "Bluetooth Headset Problems"
date: 2010-10-12
forum: Networking &amp; Wireless
---

### Post by Darkness134 on 2010-10-12
Hello guys, I am completely new here, and pretty new to linux and ubuntu as well. I can get most things done but one of the problems i have been having is that my headset will not connect through my bluetooth. I am running Ubuntu 10.10 on a laptop with a bluetooth usb dongle. I can get it paired and connected to my Motorola S9 headset, its just i can never get the computer's audio to go through it. Is there some kind of command i have to give so that my computer audio comes out of the headset. Please Help :)

---

### Post by kostkon on 2010-10-12
To connect it, left click on the bluetooth icon and select the *Connect* option in the headset's submenu. Then you can just select the *Open Sound Preferences* option to set it as the default output device.

A better solution would be to install the *PulseAudio Volume Control* utility (using the software centre) for a more finer control on what sounds will be sent to your headset (sound only from specific applications, etc.)

Hope that helps.

---

### Post by Darkness134 on 2010-10-12
> **kostkon said:**
> To connect it, left click on the bluetooth icon and select the *Connect* option in the headset's submenu. Then you can just select the *Open Sound Preferences* option to set it as the default output device.

A better solution would be to install the *PulseAudio Volume Control* utility (using the software centre) for a more finer control on what sounds will be sent to your headset (sound only from specific applications, etc.)

Hope that helps.

Thanks alot :) i could get it connect, but never knew about making it the default output audio device. Its works YAY!

EDIT: My motorola S9 is a stereo bluetooth headset, but it only has the opition for mono, which uses only one of the ears of the headset(the left one) is there any way i can change this, because it doesnt sound good. Guess i am just too spoiled with setero :)

2nd EDIT: I figured it out, i used the audio controller you suggest and it thought it was a HSP/HFP device when i really had a High Fidelity Playback device, Thxs again :)

---

