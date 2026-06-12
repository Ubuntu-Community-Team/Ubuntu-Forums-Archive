---
title: "Skype, Gizmo, Ekiga- nothing captures my microphone, except audio-editing s/w..."
date: 2006-09-04
forum: Multimedia &amp; Video
---

### Post by kendals on 2006-09-04
Heya all.

I can't get my USB microphone to work in any of these voice programs (it's a Logitech AK5370). I'm running 6.06, and the latest of all of these programs, yet none of them can hear me (i.e. echo test, etc.)- I've got them set up to use the input device, AK5370 and still doesn't work. I even edited the .asoundrc file to say this:

```
pcm.!default { 
  type hw 
  card 0 
} 

ctl.!default { 
  type hw 
  card 0 
}
```

I also tried this:

```
pcm.!default {
type plug
slave.pcm "combined"
}

pcm.combined {
type asym
playback.pcm "playback"
capture.pcm "hw:1,0"
}

pcm.playback {
type dmix
ipc_key 1024
slave {
pcm "hw:0,0"
period_time 0
period_size 1024
buffer_size 4096
rate 44100
}
bindings {
0 0
1 1
}
}

ctl.dmixer {
type hw
card 0
}
``` (from [http://crache.net/blog/2006/05/06/logitech-usb-desktop-microphone-in-linux/)](http://crache.net/blog/2006/05/06/logitech-usb-desktop-microphone-in-linux/)).

My devices are as follows:

```
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
root@kenny:/home/kendal# arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 1: Intel ICH - MIC ADC [Intel ICH6 - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 2: Intel ICH - MIC2 ADC [Intel ICH6 - MIC2 ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 3: Intel ICH - ADC2 [Intel ICH6 - ADC2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [AK5370          ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Any ideas? I've tried what SEEMs to be everything. Here was me thinking I could buy this Logitech USB mic tonight ($50 :(), and Ubuntu being so 'just works' oriented, I'd plug it in, and voila!

How wrong I was *sniff*

Any help would be most appreciate, guys! :-k :(

---

### Post by MatthewMetzger on 2008-06-30
I have the same microphone and I'm also having problems getting it to work with ubuntu. I also want it to work with Gizmo, but so far no luck.

If anyone has experience with this USB microphone and Ubuntu or resource documentation on USB mics with Ubuntu, I would be very grateful.

thanks,

Matthew

---

