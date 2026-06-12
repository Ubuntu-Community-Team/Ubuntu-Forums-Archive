---
title: "Sound plays.. then crackels and stops"
date: 2009-06-04
forum: Multimedia Software
---

### Post by jag7720 on 2009-06-04
I can play sound. Usually for about a minute or two... then it crackles and stops.

If I shut down the app and restart it I can play sound again and the same thing happens.

It happens on mp3s, youtube video, hulu video, (the video stops too).

I am using PulseAudio

```
$ aplay -l
 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1

```

system sounds work as they don't play but for a few seconds.

Any idea what is going on and how to fix it?

---

### Post by jag7720 on 2009-06-05
So, today I noticed that when I play a youtube video... the video works and then the sound stops but the system sounds still function.

e.g.  I was playing a video and there was no sound... but when someone logged into their IM account Pidgin's notification sound played fine.

---

### Post by connorh123 on 2009-06-05
Here, try this:
1. In terminal, type 
```
sudo apt-get aumix
```
2. Then, when it's done, it should open.
3. Their will be a lot of ruler looking things. The first one is what you wanna look at. It has a V and what looks like a ruler to the side of it. So all you do is use the right-arrow to move it to the right, and their's your sound.

---

### Post by jag7720 on 2009-06-05
```
sudo apt-get install aumix
```

it was set all the way to the right already.

---

### Post by connorh123 on 2009-06-06
The V bar was?

---

### Post by jag7720 on 2009-06-07
Yes, the volume was a the max...

I don't think the volume is the issue.. because I am listening to a song or watching a video and a decent volume and then the whole thing cuts out...If I close the program and restart it, the sound returns... but will eventually do the same thing.

Plus, I can hear some very light popping and crackles.

---

