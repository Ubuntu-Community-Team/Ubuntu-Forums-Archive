---
title: "list of issues makes watching DVD movies painful"
date: 2010-09-21
forum: Multimedia Software
---

### Post by bobdobbs on 2010-09-21
Hi all. I'm using lynx.
I'd like to be able to watch DVD's with ease, but alas this is not the case.

* When I fullscreen vlc or totem, they crash.

* Sometimes totem will go to fullscreen mode, and the screen will be blank. I still get sound, but no video.

* When I insert a DVD into the drive, I can't see the disc in 'places', even though the OS picks it up. I can tell the OS picks it up, because I can tell vlc to load from /dev/scd0

* Telling vlc to play from the device is a pain. When I go to 'media -> open disc', the default text string in the 'disc device' textarea is garbled glyphs. I have to enter the device name in manually.

* Xine won't play DVD's. It tells me that it lacks the available plugin.

All of this makes me want to tear my hair out.

How can I set things up so that I can simply and easily play DVD's from one of these players? vlc seems to be the least painful player I've used to far. Is there a way to reduce the pain further?

---

### Post by garvinrick4 on 2010-09-21
I use VLC and it is nice to use looks simple but is better than rest. Not the packages fault.
even plays ripped dvds in .vob
make sure you have.
```
sudo apt-get install libdvdcss2
```

---

### Post by bobdobbs on 2010-09-21
Hi.

I have libdvdcss2 already.

---

### Post by garvinrick4 on 2010-09-21
Have you gived smplayer a go if having trouble with rest.

---

### Post by Yellow Pasque on 2010-09-21
A few thoughts:

Are you still using Ubuntu 9.04? That could be an issue. If not, try using the latest stable gstreamer: [https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)
It might help the totem issues. Smplayer is nice too, especially if you have an nvidia card with vdpau. While I'm on the suject, what video chip do you have?
```
sudo lshw -C video
```

---

### Post by bobdobbs on 2010-09-21
> **garvinrick4 said:**
> Have you gived smplayer a go if having trouble with rest.

smplayer fails to play DVD's.

On my first attempt, it couldn't find the DVD device. This had to be hand configured.
smplayer was nice about this failure though, and told my why it happened and guided me to the configuration dialogue.

After I configured the device and attempted to play the DVD, I got an instant failure: a dialogue appears with this
"Mplayer has  finished unexpectedly. Exit code 127"

A quick googling shows that this error code could come from any number of causes.

---

### Post by bobdobbs on 2010-09-21
> **Temüjin said:**
> A few thoughts:

Are you still using Ubuntu 9.04? That could be an issue. If not, try using the latest stable gstreamer: [https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)
It might help the totem issues. Smplayer is nice too, especially if you have an nvidia card with vdpau. While I'm on the suject, what video chip do you have?
```
sudo lshw -C video
```

I'm using Lynx.

output from the command yields:

```

-display               
       description: VGA compatible controller
       product: NV42 [GeForce 6800 XT]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:fd000000-fdffffff memory:d0000000-dfffffff(prefetchable) memory:fc000000-fcffffff memory:fe9e0000-fe9fffff(prefetchable)


```

---

