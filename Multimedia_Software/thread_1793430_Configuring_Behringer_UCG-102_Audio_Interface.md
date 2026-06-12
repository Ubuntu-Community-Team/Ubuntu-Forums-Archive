---
title: "Configuring Behringer UCG-102 Audio Interface"
date: 2011-06-29
forum: Multimedia Software
---

### Post by ericmo on 2011-06-29
I have bought a UCG-102, as many Linux users have succeded in using it.

When I run lsusb, aplay -l and arecord -l, I get these:

```

eric@ubuntu:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 08bb:2902 Texas Instruments Japan PCM2902 Audio Codec
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 6891:a727 3Com 3CRUSB10075 802.11bg
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

eric@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [USB Audio CODEC ], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

eric@ubuntu:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [USB Audio CODEC ], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

I have configured Input/Output devices with hw:1, forced 16bit and 44.1kHZ (to comply with UCG-102 specs) and raised frames/period to 2048.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=196308&stc=1&d=1309363826[/IMG]

Yet, I get no sound when I plug in my guitar.
Please help, what should I do?

---

### Post by cchhrriiss121212 on 2011-06-29
Does jack start OK? Are you seeing error messages anywhere?

---

### Post by ericmo on 2011-06-29
Yes, I opened up qjackctl, pressed start and got no errors in the messages window.
Then, I connected all the system inputs to all the system outputs in connections windows and got no sound, only a little noise/hum coming from the interface headphone output.
 
I'm currently at the office, working, so I can't test anything.
But which commands could I use to "debug" and find errors?

---

### Post by cchhrriiss121212 on 2011-06-29
Given the device should be plug and play, and it shows up in ALSA and jack, this might not be a software issue. (I would make a few small changes to your jack setup however, realtime should be checked and you can set input/ouput to default and use the device name as the interface.)
Have you checked the volume control on the device + your cabling?

---

### Post by ericmo on 2011-06-29
Since I came back from work, I've had a bunch of other problems with Ubuntu. I had to reinstall grub from LiveCD, it was not very pleasant! (Sometimes I think BSOD wasn't much of a big deal.)

Anyway. I'm not sure what happened, but I did check the realtime box and it started to work. In a very unstable manner, however. It stopped to work a couple of minutes ago.

And sometimes I needed to take the plug off my guitar and plug it in again. Also, apparently, I can't get any sound when I start jack and the guitar is already plugged in. Really weird.

I had not checked realtime, because I'm not running rt-kernel. It's not installed.

I'm pretty sure my wiring is ok. I'm pluging my guitar and headphone directly to the interface, and the interface directly to the usb port. Both the headphone and cable are new and just fine.

Thanks a lot for the help!
I'll try tweeking some more and post anything new.

---

### Post by ericmo on 2011-06-29
BTW, about the realtime kernel, I think there's no realtime and lowlatency kernels for Natty yet, so I guess I'll have to do without them.

Cheers.

---

### Post by ericmo on 2011-06-30
OMG, Can't get any sound of it again.

Don't know how I did it before to make it work, don't know how to do it again! I'm pretty sure it is a software problem, can anyone help me debug this?

---

### Post by ericmo on 2011-06-30
I tweeked my Jack config until it started to work, it was like that:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=196365&stc=1&d=1309412501[/IMG]

I honestly don't think that that matters. Because I used a couple of effects in Jack Rack which crashed, and since that, I can't get any sound again.

---

### Post by cchhrriiss121212 on 2011-06-30
Did you get any error messages when it stopped working?

What could be happening is that your USB device is being renamed to something other than hw:1 each time you plug it in or boot up. Double check the jack settings when you start up each time. Other than that I don't know what else to suggest.

Also: you do not need a realtime kernel to run jack in realtime mode, the newer generic kernels are actually pretty good for audio latency.

---

### Post by ericmo on 2011-07-01
Hi.

I played the guitar through UCG-102 last night, and it has worked fine from start to end.

In the end, I think it really was the cable. The cable is a brand new Planet Waves with lifetime warranty and I really don't have any problems with it when plugging it into the amp.

But when I touched the cable the sound failed and when I touched it again it came back, but I'm not sure what happens, because the cable is in a very good state.

Thanks a lot for your help!

---

