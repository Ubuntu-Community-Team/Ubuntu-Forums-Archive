---
title: "No Sound, clean install of Mythbuntu 10.10 64-bit"
date: 2010-10-19
forum: Mythbuntu
---

### Post by chrismurf2900 on 2010-10-19
Recently I upgraded my Mythbuntu 10.04 64-bit system to 10.10 64-bit and then my sound stopped working.  After trying to fix it, I just decided to do a fresh install of Mythbuntu 10.10 64-bit.  Still, no sound was working.

My sound codec is Realtek ALC887. As stated above, I previously had it working when I had 10.04, but when I upgraded it to 10.10, sound no longer worked in anything. So I did a fresh install to see if that would resolve the issue. It didn't.

The hardware is being recognized by Mythbuntu, all outputs are un-muted, but still no sound.

I've got it connected via the digital optical audio-out port to my receiver. No issues with receiver (just as an FYI).

I ran the sound diagnostics and have gotten back the following information (see ALSA info): [http://www.alsa-project.org/db/?f=e14c4a3d92881cc6439fe1b45bf67968f648bcf8](http://www.alsa-project.org/db/?f=e14c4a3d92881cc6439fe1b45bf67968f648bcf8)

Any assistance would be greatly appreciated.  I hate not having sound, it makes the device not usable.

Thanks in advance for all the help!

---

### Post by LowSky on 2010-10-19
open a terminal

type
```
alsamixer
```
make sure nothing is muted

---

### Post by chrismurf2900 on 2010-10-19
First, I just want to thank you for replying and trying to help me get things to work.

I have double checked to make sure everything is un-muted from alsamixer.  Still, no sound.

---

### Post by chrismurf2900 on 2010-10-20
I've attached an image of my alsamixer if that helps any.  Again, I've got my speakers connected via the digital optical port.

Please help!

---

### Post by LowSky on 2010-10-20
In alsam ixer press F6 to see if you have other sound cards listed and unmute what is there

can you please show the outpt of the command

```
aplay -l
```

that is a lower case L

---

### Post by chrismurf2900 on 2010-10-20
Thanks LowSky... I updated Ubuntu today, and after that I restarted... It started to work again!  Maybe an update or something fixed it.

Thanks for your help!

---

