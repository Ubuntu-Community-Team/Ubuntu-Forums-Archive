---
title: "How do I set a limit to master volume?"
date: 2009-07-14
forum: Multimedia Software
---

### Post by Oscar07202 on 2009-07-14
First I apologize if I posted this thread in the wrong place but I did not know where else to put it.

I am having problems were family members are raising the volume to its max. and I am afraid that sooner or later the speakers are going to blow out or decrease in performance. :-({|= So I am looking for a way to put a limit to the maximum master volume, with the ability to change the master volume from 0%-max. limit, and password protecting this limitation would be great. 

Thank you for your time.

---

### Post by Oscar07202 on 2009-07-18
Bump

Anyone have a solution?:(

---

### Post by markbuntu on 2009-07-18
Hmmm, we need more info. Are you using pulseaudio?

---

### Post by Oscar07202 on 2009-07-27
I think, I am using pulseaudio but I am not sure.  I went to Synaptic Package Manager, searched for "pulseaudio" and the only thing that was green checked was libpulse0 verison 0.9.10-ubuntu1.1.

I originally installed xubuntu 8.04 and later on installed gnome-desktop.

Sorry for the long delay in response time.

---

### Post by martinbaselier on 2009-07-27
Do you have multiple slicers to set the volume, maybe one for master and one for pcm, or front or something equivalent. You could then turn one down and hide it then, so they just don't see it.

---

### Post by xzero1 on 2009-07-28
If you use only alsa via pulse or not, then you could easily create a default plugin set to amplify your sound by any chosen factor. In your home directory create an .asoundrc file containing something like this:
```

pcm.!default {
    type plug
    slave.pcm amp
}

pcm.amp {
  type plug
  slave.pcm "plughw"
  ttable {
    0.0=    0.7     #amplication factor
    1.1=    0.7     #amplication factor
  }
}
```

---

### Post by Oscar07202 on 2009-07-29
> **martinbaselier said:**
> Do you have multiple slicers to set the volume, maybe one for master and one for pcm, or front or something equivalent. You could then turn one down and hide it then, so they just don't see it.


Thank you very much, I was making to much of the problem :)

---

### Post by Oscar07202 on 2009-07-29
> **xzero1 said:**
> If you use only alsa via pulse or not, then you could easily create a default plugin set to amplify your sound by any chosen factor. In your home directory create an .asoundrc file containing something like this:
```

pcm.!default {
    type plug
    slave.pcm amp
}

pcm.amp {
  type plug
  slave.pcm "plughw"
  ttable {
    0.0=    0.7     #amplication factor
    1.1=    0.7     #amplication factor
  }
}
```


The code above didn't help also when I removed .asoundrc from /home/   any program that played sound shuts off such as watching a video on youtube would make firefox close.:(

Thank you for time.:)

---

### Post by xzero1 on 2009-07-29
The original 'empty' .asoundrc file should have the following code at least in Jaunty:
```
# ALSA library configuration file

# Include settings that are under the control of asoundconf(1).
# (To disable these settings, comment out this line.)
</home/USERNAME/.asoundrc.asoundconf>
```make sure you change USERNAME to your username
do not modify your .asoundrc.asoundconf!

Now add this code to the .asoundrc file:
```
pcm.!default {
    type plug
    channels 2
    slave.pcm amp
}

pcm.amp {
  type plug
  slave.pcm "plughw"
  ttable {
    0.0=    0.7     #amplication factor
    1.1=    0.7     #amplication factor
  }
}
```Notice that I have added channels 2 to the pcm!default code. If you have a different setup, change this appropriately. Hopefully this will fix your firefox issue. Anyway, if you leave out the added code, you should be back to normal. Sorry for the bug.

---

### Post by Sutur on 2010-10-07
Hi mate, just searching around for methods of amplifying audio in linux with ALSA.

I was really happy to find your post, but it's not working for me.

I added a missing parenthesis to the end of the file.

I changed:

```
    0.0=    0.7     #amplication factor
    1.1=    0.7     #amplication factor
```

to

```
    0.0=    5     #amplication factor
    1.1=    5     #amplication factor
```

In an effort to amplify the PCM volume five times.

But nothing has changed, it's the same volume. Can you help me please? I only have two speakers.

```
aplay -l
```
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

> **xzero1 said:**
> The original 'empty' .asoundrc file should have the following code at least in Jaunty:
```
# ALSA library configuration file

# Include settings that are under the control of asoundconf(1).
# (To disable these settings, comment out this line.)
</home/USERNAME/.asoundrc.asoundconf>
```make sure you change USERNAME to your username
do not modify your .asoundrc.asoundconf!

Now add this code to the .asoundrc file:
```
pcm.!default {
    type plug
    channels 2
    slave.pcm amp
}

pcm.amp {
  type plug
  slave.pcm "plughw"
  ttable {
    0.0=    0.7     #amplication factor
    1.1=    0.7     #amplication factor
  }
}
```Notice that I have added channels 2 to the pcm!default code. If you have a different setup, change this appropriately. Hopefully this will fix your firefox issue. Anyway, if you leave out the added code, you should be back to normal. Sorry for the bug.

---

