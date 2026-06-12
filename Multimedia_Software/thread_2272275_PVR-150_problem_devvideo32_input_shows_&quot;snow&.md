---
title: "PVR-150 problem: dev/video32 input shows &quot;snow&quot; picture as if input is disconnected."
date: 2015-04-05
forum: Multimedia Software
---

### Post by lukon on 2015-04-05
I'm trying to record AV through my Hauppauge 26552 PVR-150 video capture card on my Ubuntu 14.04 computer (an HP MediaCenter desktop). No success.

So far, I have installed the ivtv utilities thing and VLC through the software center.

So in VLC, I select Media>Open Capture Device and pick Capture mode = TV - analog. 

Then I'm offered 3 devices in the Device name box:

/dev/video0
/dev/video24
/dev/video32

Picking any of them will give me a "Play" button to click.

I tried to play all 3 devices.

The /dev/video0 and /dev/video24 showed blank black screens in the VLC player. Only the /dev/video32 responded with anything resembling an active connection. But the screen looked like a TV tuned to an empty channel - just a bunch of snow-noise.

As I tested all 3 devices, I also picked Video standard = NTSC M

I am using the composite video input of the PVR-150.

I therefore attempted to set the PVR-150 to use the composite video input, using the ivtv command for doing so.

v4l2-ctl -i 2 or 4

These didn't fix anything. So I tried them all.

v4l2-ctl -i 0 = Tuner 1
v4l2-ctl -i 1 = S-Video 1
v4l2-ctl -i 2 = Composite 1
v42l-ctl -i 3 = S-Video 2
v42l-ctl -i 4 = Composite 2

None of these worked. Regardless of selected input, I get "snow noise."

The PVR-150 does work. My computer is a multi-boot system. The PVR-150 does record as connected via WinTV 7 in Windows 7.

So, does anyone know what the problem might be?

---

