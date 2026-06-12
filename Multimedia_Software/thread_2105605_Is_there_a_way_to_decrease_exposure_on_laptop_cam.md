---
title: "Is there a way to decrease exposure on laptop cam?"
date: 2013-01-16
forum: Multimedia Software
---

### Post by s1baker on 2013-01-16
Hi,
Is there a way to lower the exposure time on a laptop cam?

I have my laptop set up to look out the front window toward the driveway as a survelence device using "motion". It is networked and I can monitor the stream from my desktop at my worktable.
Problem is that the cam is adjusting the exposure for inside the house, and the outside light is so bright it overexposes and the window shows up as a glare, unable to see anything outside.

I tried setting the "brightness" setting in "motion", but this just lowers the overall brightness level.

---

### Post by tgalati4 on 2013-01-16
Most laptop cameras are crappy and designed for indoor, low lighting.  Try putting a neutral density filter in front of it (or a sunglass lens).  These cameras don't have an adjustable aperature, so what you get is what you get.  More advanced webcams have an auto-gain that helps, but to overcome sunlight glare, you need a real aperature or an ND filter to reduce the light.

As far are frame rate, you might be able to change it.  Do a search for the camera module that gets loaded:

```
lsmod
```

Then google "cameramodulename module options" and see if there are any load time options to increase framerate.  This might give you better exposure control in bright scenes--say from 30 fps to 60 fps would give you 1 stop of light reduction.

Don't get your hopes up.

Put the module and options in /etc/modules and reboot.

---

### Post by s1baker on 2013-01-16
thanks for your reply tgalati4

The motion config file has this:
```
# Maximum number of frames to be captured per second.
# Valid range: 2-100. Default: 100 (almost no limit).
framerate 10

# Minimum time in seconds between capturing picture frames from the camera.
# Default: 0 = disabled - the capture rate is given by the camera framerate.
# This option is used when you want to capture images at a rate lower than 2 per second.
minimum_frame_time 0

```

i'll try to set that and also try to put a sunglass in front of the lens.

---

### Post by DracoMaille on 2013-01-16
while not trying to make your computer too obvious through the window, you might try moving the camera closer to the window.  If the window is the only thing that the camera can see, it is more likely that it will (at least attempt to) auto-correct the exposure to the outside lighting.  No guarantees, but sometimes the answer to too much light is more light.  At least this used to work with my old digital camera.  Good luck!

---

