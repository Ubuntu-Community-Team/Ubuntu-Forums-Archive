---
title: "Hauppauge! WinTV HVR-1600 - IR Remote"
date: 2009-09-03
forum: Mythbuntu
---

### Post by fermulator on 2009-09-03
Hey all.

Does anyone have any experience or guidance on how to setup and configure the Hauppauge WinTV Remote?  It came with the WinTV HVR-1600 TV Tuner.  The Model is: "A415-OH/S 1-4"

I'm completely new to this "TV remote" stuff on Linux.  I've been using Linux for ~3 years now, and am an advanced user, so don't be afraid to ask me to do weird stuff.

**_What I've Tried So Far_**

I'm sort of "half-aware" of different options:
 * LIRC - I installed this through apt package manager, but during installation it prompted me for the "type" of remote, and mine wasn't listed, so I just chose the Hauppauge DVB-s option.  This didn't seem to work.
 * gnome-lirc-properties - I tried this as well to 'autoconfigure' the remote, but again the remote isn't listed in the available remotes, and the "connection test" doesn't give any feedback.
 * Also tried these instructions: [http://rtr.ca/hvr1600/](http://rtr.ca/hvr1600/), but that doesn't seem to work either.

**_Some Hardware Details:_**

```
sudo lspci | grep Conex
```
> 05:02.0 Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder

2.6.28-15-server

```
lsmod  |grep ir_kbd_i2c
```
> ir_kbd_i2c             15632  0 
ir_common              52228  1 ir_kbd_i2c

```
dmesg | grep lirc
```
> [ 3881.532356] lirc_dev: IR Remote Control driver registered, major 61

---

