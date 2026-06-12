---
title: "Sound Really Screwed Up!"
date: 2010-04-24
forum: Multimedia Software
---

### Post by BobLand on 2010-04-24
Since installing Ubuntu Studio I've had nothing but problems with sound.  I've located numerous threads on various fixes.  The last one was the Karmic Sound tips (or something like that).  Using those "fixes" I now have no sound in any application.  The pulse audio playback monitor shows sound but nothing comes from the speakers.

All sound controls are on.

Is there a real fix for this issue or should I look to another distro?

---

### Post by JC Cheloven on 2010-04-24
Hi, Bob

Being that unspecific will not help others to help you. Surely posting further details will increase your chances. I had big problems with sound myself (due to a sort of bug in alsa affecting my soundcard), but eventually sorted them out with the help of mates over here.

And if you are in the mood of giving other distro a try, go for that. It's cheap ;-) I tried Musix and 64Sutio. I came back to Ubuntu Studio, though.

---

### Post by lidex on 2010-04-24
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by BobLand on 2010-04-25
```

uname -a
Linux maxland 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010 x86_64 GNU/Linux
```

```

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

```

cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Feb  8 2010 for kernel 2.6.31-20-generic (SMP).
```

```

head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ALC888

```

---

### Post by lidex on 2010-04-25
What is the make/model of the pc in question?

---

