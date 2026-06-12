---
title: "Sound Question"
date: 2008-04-14
forum: Multimedia &amp; Video
---

### Post by Terratoch on 2008-04-14
I am running Ubuntu 7.10 with a M2N32 Motherboard. I am using the onboard 5.1 surround sound sound device (MCP55 Chipset). I have 5.1 speakers plugged into it, but I am only getting sound out of two of them. I have looked for, found, read and tried countless how-to guides with absolutely no success. Can someone help me out?

---

### Post by DkkD on 2008-04-14
First try:

```
speaker-test -c6 -Dplug:surround51 -twav
```

If you can hear the sound from every speaker, it means your sound card is properly configured. Now, all you have to do is edit your .asoundrc file. Enter this in your console (presuming you are in your /home/yourUserName/ directory):

```
gedit .asoundrc
```

Try entering one of those options in your .asoundrc file:

```
pcm.!default {
type plug
slave.pcm “surround51&#8243;
slave.channels 6
route_policy duplicate
}
```

OR

```
pcm.!default {
         slave.pcm surround51
         slave.channels 6
         type route
         ttable.0.0 1
         ttable.1.1 1
         ttable.0.2 1
         ttable.1.3 1
         ttable.0.4 0.5
         ttable.1.4 0.5
         ttable.0.5 0.5
         ttable.1.5 0.5
}
```

Hope it helps.

---

### Post by Terratoch on 2008-04-14
I've tried that before. I only get sound out of my two front speakers (left and right) and my bass speaker.

---

### Post by DkkD on 2008-04-14
Try:
```
aplay -l
```
If that doesn't list your card, enter this in terminal:
```
lspci -v
```
If it is listed here, check out this thread for detailed instructions about alsa drivers instalation:
[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

Although if you can hear the sound on more than two speakers with
```
speaker-test -c6 -Dplug:surround51 -twav
```
first try to check if your other speakers are connected the way they should be.

---

### Post by Terratoch on 2008-04-14
> 
aplay -l:

card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Everything appears to be plugged in the way it should be.

Thanks for walking me through this, by the way.

---

### Post by Terratoch on 2008-04-14
> 
If it is listed here, check out this thread for detailed instructions about alsa drivers instalation:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)


I've checked that guide out as well. Perhaps not thoroughly enough, I will check it again, but what I did read didn't help me.

---

### Post by DkkD on 2008-04-14
I am not really sure how your aplay output should look like, but I think it should list 3 or 4 devices, at least one for each pair of speakers. This is what I get (I have SB Live):

```

card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Have you checked volume levels at alsa mixer?

---

### Post by Terratoch on 2008-04-14
> 
Have you checked volume levels at alsa mixer?

Yes.Everything is unmuted and at maximum levels.

---

### Post by DkkD on 2008-04-14
If you are using Ubuntu 8.04 beta, you should go to System->Preferences->Sound and put alsa mixer as your default device. I have read that people have problems with getting surround sound using pulseaudio.

---

### Post by Terratoch on 2008-04-14
> **DkkD said:**
> If you are using Ubuntu 8.04 beta, you should go to System->Preferences->Sound and put alsa mixer as your default device. I have read that people have problems with getting surround sound using pulseaudio.

I'm using Ubuntu 7.10, and I am relatively certain it is.

---

### Post by Terratoch on 2008-04-15
Still looking for some answers to this problem.

---

### Post by Terratoch on 2008-04-15
I'm still looking for some help with this.

---

### Post by simonjcruse on 2008-04-29
same problem here, i've added a .asoundrc file to my home folder,

pcm.ca0106 {
type hw
card 0
}

ctl.ca0106 {
type hw
card 0
}

pcm.!dmix {
type plug
slave {
pcm surround71
channels 8
}
}
pcm.!default {
type plug
slave.pcm "dmix"
slave.channels 8
route_policy duplicate
}

I also made sure in the alsa config my ca0106 is loaded first. The strangest thing is it will upmix at desktop level, such as desktop sounds and beeps, but it will not up mix from firefox, amsn. So thinking the must be down to some other configuration. 7.1 upmix only works on the jungle start up sound when you log-into ubuntu?

Its had me stumpted on 7.10 as well although i did achieve full 7.1 upmix on alsa.

Really really stuck, the ca0106 has reported problems with configuration and i dont think its restricted to ubuntu. Looking thru google this has had reported problems for a couple of years now. 

Help please. Many thanks

---

