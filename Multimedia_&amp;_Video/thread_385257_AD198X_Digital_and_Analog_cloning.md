---
title: "AD198X Digital and Analog cloning"
date: 2007-03-15
forum: Multimedia &amp; Video
---

### Post by lank23 on 2007-03-15
Hello All;

I seem to not be able to get my digital spdif and my analog outputs to clone the audio output.  So what I have is either digital or analog, but not both at the same time.

I would like to have all sound to be outputted on both the digital and analog, and when I play a movie and send AC3 pass through that sound is down mixed or converted to output on the analog at the same time as the digital.

Here is aplay -l

```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```

Here is my ~/.asoundrc for analog

```

pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"

}


pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,0"
period_time 0
period_size 2048	#1024
buffer_size 32768	#4096
			#periods 128
rate 48000		#44100
}
bindings {
0 0
1 1
}
}


```

Here is my ~/.asoundrc for digital

```

pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"

}


pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,1"
period_time 0
period_size 2048	#1024
buffer_size 32768	#4096
			#periods 128
rate 48000		#44100
}
bindings {
0 0
1 1
}
}


```


Thanks for you help.
lank23

---

