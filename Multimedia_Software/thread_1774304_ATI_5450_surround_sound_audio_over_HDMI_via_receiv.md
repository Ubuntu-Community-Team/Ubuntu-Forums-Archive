---
title: "ATI 5450 surround sound audio over HDMI via receiver"
date: 2011-06-03
forum: Multimedia Software
---

### Post by craigdabbs on 2011-06-03
Hi there,

im hoping someone here can help me with this issue im having, im a fairly new linux user and a bit of a novice when going into advanced configs.

I am trying to setup my HTPC using ubuntu 11.04 with a ATI 5450 using a HDMI into a 5.1 Yamaha receiver, then onto the TV.  I have disabled the onboard sound card.

I am able to get sound from the front 2 speakers only

The issue i have at the moment is that i can only select 2 channel stereo as a profile
[IMG]http://dl.dropbox.com/u/8384353/Screenshot-Sound%20Preferences.png[/IMG]

aplay -l output

```
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```alsamixer not showing much :)
[IMG]http://dl.dropbox.com/u/8384353/Screenshot-craig%40HTPC%3A%20%7E.png[/IMG]

Everything is working fine in windows so i know the hardware is capable.

Im not sure if it makes a difference but the graphics drivers detect my display as a LG TV (which is 2.0 stereo) and not the receiver so not loading up the other profiles?
[IMG]http://dl.dropbox.com/u/8384353/Screenshot-Catalyst%20Control%20Center.png[/IMG]
 Any help or insight would be greatly appreciated.

Thanks

Craig

---

