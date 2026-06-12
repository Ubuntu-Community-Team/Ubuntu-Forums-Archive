---
title: "Change device /dev/video0 to /dev/video1"
date: 2011-05-27
forum: Multimedia Software
---

### Post by superori on 2011-05-27
Hi, I my system detects my TV tuner in /dev/video0 and the webcam in /dev/video1

I need to put webcam in /dev/video0 because some programs, like google-talk takes the /dev/video0 device and don't let me change to another.

How can I config that always webcam is configured into /dev/video0 and TV tuner in /dev/video1?

Thanks.

---

### Post by psusi on 2011-05-27
There has to be a way to specify which device google-talk should use...

---

### Post by superori on 2011-05-29
> **psusi said:**
> There has to be a way to specify which device google-talk should use...

I can't find any configuration on googletalk to configure video source

---

### Post by AKADAP on 2011-05-29
Probably won't help, but look up udev rules.
It will let you create a softlink that always points to the same device, but I have not found a way to use it to make sure /dev/video0 points at the device I want it to, or even always point to the same device.

---

