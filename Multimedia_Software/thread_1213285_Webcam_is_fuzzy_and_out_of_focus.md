---
title: "Webcam is fuzzy and out of focus"
date: 2009-07-14
forum: Multimedia Software
---

### Post by Buce on 2009-07-14
I'm trying to get a Logitech Quickcam to work with an installation of ubuntu from the Minimal CD. On previous installations (Arch and the default Ubuntu install) this worked fine. This time, though, the video is fuzzy and out of focus -- although, I've only tried running it under skype.
 
I know this is probably a simple issue that can be fixed with a package or two, but I'm having a really hard time finding tutes or just general advice geared towards building a desktop around a Minimal CD installation, and I'm not sure where to go from here.

Here's what I get when I try running luvcview:
```
$ luvcview
luvcview version 0.2.1 
Video driver: x11
A window manager is available
video /dev/video0 
Unable to set format: 16.
 Init v4L2 failed !! exit fatal 
```

---

### Post by Buce on 2009-07-14
Oh wow, I am so silly. I thought there must be some kind of software component that would automatically focus the webcam for me. Turns out you can manually focus it just by turning a little dial around the lens. Woops.

---

### Post by t0n1 on 2010-02-10
Thanks, that solved my problem as well :)

---

### Post by g0r33k on 2011-05-02
I feel silly but I thought it is right to share that this also worked for me! I too was looking for a software issue!!! :oops:

---

### Post by FuzzShifter on 2011-05-02
The real question is...

Why is framerate so poor.:(

---

### Post by no2498 on 2011-05-02
if the light is low they go slow

if you need to change the colors install v4l2ucp
it comes up/in system, preferences as videl4linux control panel

---

