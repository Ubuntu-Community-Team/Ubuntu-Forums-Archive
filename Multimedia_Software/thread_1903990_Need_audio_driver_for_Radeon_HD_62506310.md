---
title: "Need audio driver for Radeon HD 6250/6310"
date: 2012-01-03
forum: Multimedia Software
---

### Post by duncang92 on 2012-01-03
My system has on-board audio on the motherboard and supports 5.1 surround sound. The driver loaded by Ubuntu 11.10 only supports 2 channel stereo :( Note: I do have sound albeit only 2 channel.

lspci -nn|grep '0403'
00:01.1 Audio device [0403]: ATI Technologies Inc Wrestler HDMI Audio [Radeon HD 6250/6310] [1002:1314]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)

aplay shows:
root@xbox:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 1: ALC887-VD Digital [ALC887-VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


The "HD-Audio Generic" driver only gives me a 2 channel option.

Does anyone have a link etc. to the correct driver so I can get 5.1 surround sound over HDMI? I've searched everywhere to no avail.

Thanks, Duncan

---

### Post by cbowman57 on 2012-01-03
Looking around I don't think there is one, though there was a post somewhere that said somebody had successfully created one within the last week or so.  If that's the case it should trickle down within a few weeks.

---

### Post by duncang92 on 2012-02-12
I found that upgrading to Catalyst 11.12 allowed me to use the custom passthrough capabilities in XBMC giving me what I needed.

Before I upgraded to 11.12 (was on 11.11) that XBMC would complain that it could not initialise the audio device when attempting to playback a video with any sound format when attempting to use the custom passthrough device.

---

### Post by nikkkko on 2012-03-26
Hi,

You get sound out of line out or from hdmi or both?  I have the same on-board sound and I get nothing.  Still, this is only day one...

---

### Post by duncang92 on 2012-03-30
Hi Nikkkko

I only use HDMI for my sound.

Weirdly after I upgraded Catalyst and got the sound characteristics I was looking for from XBMC I lost the Ubuntu login sound and also all menu sounds from XBMC.

But since the main use of the PC is as an HTPC running XBMC and I get my sound output through to my sound system for movies and tv shows and music then I'm not touching it any more any breaking it. Especially since the gf is sick of me keep "improving" things and then she can't find the menus or I break something.

---

### Post by nikkkko on 2012-05-14
Should have mentioned this earlier, but I upgraded to 12.04 and everything works as it should, no special tweaks.

Nick

---

