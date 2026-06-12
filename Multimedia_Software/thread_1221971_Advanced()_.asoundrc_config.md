---
title: "Advanced(?) .asoundrc config"
date: 2009-07-24
forum: Multimedia Software
---

### Post by vikjon0 on 2009-07-24
Hello!

I have two .asoundrc configs. 

a) Sends the output to both spdif & hdmi
This is working fine but I get static on spdif when I e.g. switch mp3 in the middle of a track.

b) is fixing the statics and spdif works perfectly. But no sound on HDMI.

I am using xbmc in Ubuntu 9.04 on an ION 330.

Any pointer how to combine these two configs into one is welcome. I have tried a few combination with no success.

//J


a)Multi
--------
```
pcm.!default {
type plug
slave {
pcm "both"
}
}

pcm.both {
type route
slave {
pcm multi
channels 4
}
ttable.0.0 1.0
ttable.1.1 1.0
ttable.0.2 1.0
ttable.1.3 1.0
}

pcm.multi {
type multi
slaves.a {
pcm "tv"
channels 2
}
slaves.b {
pcm "receiver"
channels 2
}
bindings.0.slave a
bindings.0.channel 0
bindings.1.slave a
bindings.1.channel 1
bindings.2.slave b
bindings.2.channel 0
bindings.3.slave b
bindings.3.channel 1
}

pcm.tv {
type hw
card 0
device 3
channels 2
}

pcm.receiver {
type hw
card 0
device 1
channels 2
}

```

b) mixer
--------
```
pcm.!default {
type plug
slave.pcm "dmixer"
}

pcm.dsp0 {
type plug
slave.pcm "dmixer"
}
pcm.dmixer {
type dmix
ipc_key 1024
slave {
pcm "hw:0,1"
period_time 0
period_size 1024
buffer_size 8192
#periods 128
rate 44100
}
bindings {
0 0
1 1
}
}
ctl.mixer0 {
type hw
card 0
}
```

---

### Post by markbuntu on 2009-07-24
You should just get pulseaudio 0.9.15. It detects spdif and hdmi and makes them available for use.  Then you can just turn on Simultaneous Output. There is a PPA for 0.9.15. from Luke Yelavich who is the ubuntu pulseaudio maintainer 

[https://launchpad.net/~themuso/+archive/ppa](https://launchpad.net/~themuso/+archive/ppa)

---

### Post by vikjon0 on 2009-07-25
> You should just get pulseaudio 0.9.15.

I will give it a try next week. Problem is that I am not sure if it is possible to get digital passtrough from xbmc. All the howtos is for ALSA.

---

### Post by markbuntu on 2009-07-25
Hmm, I have not tried xbmc but maybe I should give it a whirl to see what it does.

---

### Post by pt123 on 2009-07-26
any update on the results

---

### Post by vikjon0 on 2009-07-27
I have made the upgrade and turned on Simultaneous Output.
For the moment the result is that only spdif is playing. 

I am not even sure if it is going over pulseaudio or not though. Couldnt find any info about xbmc settings for pulseaudio. I set the audio device to default and the spdif started to work. Thats it.

I will have to get some more info from xbmc.org before I can continue.

Thanks, Jonas


> Hmm, I have not tried xbmc but maybe I should give it a whirl to see what it does.
It is probably the best media center applicattion available.
Does not include tv recording nativly though.

---

