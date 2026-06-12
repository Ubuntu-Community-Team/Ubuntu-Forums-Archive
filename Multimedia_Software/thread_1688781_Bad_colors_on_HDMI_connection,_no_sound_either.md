---
title: "Bad colors on HDMI connection, no sound either"
date: 2011-02-15
forum: Multimedia Software
---

### Post by whiterabbit7500 on 2011-02-15
I'm having an issue with output from my HDMI port on my Lenovo Z560 laptop with an i3 and built-in Intel Hd graphics. I'm using Ubuntu x64 10.10

-When I plug in the HDMI cable to the port, Ubuntu detects the TV as a monitor, and I can change the resolution independently, or clone the output.

-the picture on the TV comes out in a greenish hue. It's not the TV settings, or the HDMI cable as both work perfectly fine on their own. Is there a way to change some settings to get this to work?

-Ubuntu doesn't detect the HDMI device as a sound source, even though in theory it should.

I've done this through Windows 7 hundreds of times, and used dual-monitors in Linux on my desktop, and never seen a problem like this. Any ideas how to detect and solve the problem?

---

### Post by BicyclerBoy on 2011-02-16
The colour issue may caused by YUV (YCbCr) v.s. RGB colour-space.

HDMI TVs tend to default to YUV.
The PC input mode may change the TV to RGB.
YUV is a superior colour encoding for video.

The nvidia driver allows YUV or RGB colour-space I do not know about the i915 i965 driver.

HDMI audio support must be in the video driver. I do not know if any intel driver has HDMI audio.

---

### Post by hizaguchi on 2011-02-19
Same audio problem on my i3.  Pulse isn't picking up all your available audio outputs.  Check in the sound settings GUI... probably says analog output rather than HDMI.

Fix:
1) Open terminal and do "aplay -l"

Sample output:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC887 Analog [ALC887 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 7: INTEL HDMI 1 [INTEL HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

2) Review the output and decide which device should be handling your audio.  In my case, HDMI 1, so device 7.

3) Edit /etc/pulse/default.pa adding (or modifying) a line to explicitly enable the desired device

Sample:
```
load-module module-alsa-sink device=hw:0,7
```
(That's card 0, device 7 from the aplay -l output)

4) Reboot and hope for the best.

5) If it isn't working after reboot, go into the sound preferences GUI and manually enable HDMI audio, which should show up as an option now.

---

### Post by Emris Echo on 2013-02-17
Hey i am having the same problem as you all but after running aplay -l and finding the appropriate output unbuntu is saying load-module command not found i checked google for a source for this thinking it is a third party command program but it doesnt look like it any tips?

---

### Post by Emris Echo on 2013-02-17
i checked many bash command lists and none of them have the load or load-module command, you seem to know what you are doing so is there another command i should be using or a package i need to install? this green screen is killing me :(

---

