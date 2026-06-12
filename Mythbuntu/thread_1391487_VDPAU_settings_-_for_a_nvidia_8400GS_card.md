---
title: "VDPAU settings - for a nvidia 8400GS card"
date: 2010-01-26
forum: Mythbuntu
---

### Post by neutron68 on 2010-01-26
I've got a Hauppauge HD-PVR and I'm recording HD programming off of a Directv satellite receiver.  As most you you know, the HD-PRV outputs a stream of h.264 encoded video.  I've got a nvidia 8400GS card in the pc.

I'm trying to figure out the best VDPAU settings for playback of HD video.  For now, I'm playing back on a 23 inch Acer LCD screen at 1920x1080 resolution.

I've noticed that "VDPAU normal" settings give somewhat of a choppy playback of 1920x1080 HD.  I finally tried "VDPAU Lite".  The playback seems pretty smooth.  I was surprised.  I figured that Lite would look bad.  Instead it looks better than normal!?  Why is that?  

Is the Lite setting using more of the CPU and less of the nvidia card??

Eric

---

### Post by Linuxforall on 2010-01-26
Exactly what player are you using to select lite and regular VDPAU? I use SMPLAYER and that don't seem to have this option.

---

### Post by neutron68 on 2010-01-27
I'm using the built-in Mythtv player.  This is the Mythbuntu forum, after all. ;)

The VDPAU settings are in the Mythtv setup menus, under the PLAYBACK settings.

---

### Post by pilesofspam on 2010-01-27
I'm doing almost the same thing as you- HD-PVR (H.264) off of a dish network box on an Nvidia 8400.  I've got my dish box set to output ONLY 720p, since that is the native resolution of my projector, and vdpau is set to normal.  Works great.  The processor is an AMD X2 3600, and it's running at like 15% during playback.

---

### Post by neutron68 on 2010-01-27
I got an nvidia 8400GS card because it was the minimum entry point for VDPAU.  I chose one with 512MB of onboard memory.
My processor is an AMD Athlon64 X2 4200+  

I'm mainly recording off of HDNET which is a full HD channel (1920x1080 resolution).  I want my recordings to be full HD too, so I'm only recording in 1920x1080.

**Any idea why the Lite setting gives smoother playback than the Normal setting?  There must be a technical reason for it.**

Eric

---

### Post by blazerw on 2010-01-31
> Any idea why the Lite setting gives smoother playback than the Normal setting? There must be a technical reason for it.

The differences between those two settings includes different settings for de-interlacing. The 8400GS does not support the more complicated de-interlacing methods. If it doesn't support them, it can't do them in the hardware and you end up with really bad video. You can use the Normal setting if you change the de-interlacing to One Field, Bob, or None. Some of the others work as well. See the table on the MythTV wiki here: [http://www.mythtv.org/wiki/Vdpau](http://www.mythtv.org/wiki/Vdpau)

---

### Post by neutron68 on 2010-01-31
Thanks blazerw!

That was a very informative reply!

I just changed my Mythtv deinterlace settings set to Bob2x.
The chart shows that the 8400GS card can manage that for full 1080 HDTV...and it does.

What is the best deinterlace setting in your opinion?

Thanks!
Eric

---

