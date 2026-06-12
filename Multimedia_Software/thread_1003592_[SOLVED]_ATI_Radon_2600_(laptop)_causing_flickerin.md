---
title: "[SOLVED] ATI Radon 2600 (laptop) causing flickering video"
date: 2008-12-06
forum: Multimedia Software
---

### Post by Chris Watts on 2008-12-06
Hi, I have a Toshiba A200 Laptop with Radon 2600 mobility for which Ubuntu is running a proprietry ATI/AMD FGLRX graphics driver. When I run Google Earth there is a great deal of flickering of the window displaying a picture of the earth. I can zoom in and do everything normally but the flickering and occasional rectangle of brown "retrace" lines in the top left corner suggest the video drivers are suspect. The flickering can also happen when a window gains focus in front of a window displaying a flash video. Any news on better ATI drivers?

---

### Post by binbash on 2008-12-06
you have to disable compiz-fusion to video google earth without flickering.for video, go to your video player's preferences and set the video output to x11

---

### Post by Chris Watts on 2008-12-07
I am using Totem Movie Player 2.24.3 using GStreamer 0.10.21
In the preferences under the 'Display' tab there is no setting for x11.
Am I using the wrong player for DVD?

---

### Post by Chris Watts on 2008-12-07
Fixed Google Earth flickering video by installing Compiz Fusion Icon and then by right clicking it, from the drop-down list select Window Manager "Metacity". Good as gold ! Thanks for the heads-up on Compiz.

---

### Post by jcmorris on 2008-12-07
I have a 3840 that had the same problem. You need to add this to the section Device under fglrx or radeon depending on what driver you use.

Option      "VideoOverlay" "off"
Option      "OpenGLOverlay" "on"
Option      "TexturedVideo" "off"

---

### Post by Chris Watts on 2008-12-09
> **jcmorris said:**
> I have a 3840 that had the same problem. You need to add this to the section Device under fglrx or radeon depending on what driver you use.

Option      "VideoOverlay" "off"
Option      "OpenGLOverlay" "on"
Option      "TexturedVideo" "off"

I have read forums dedicated to this subjet of adding the lines you have specified above, unfortunately once those lines are added to xorg.conf, aticonfig won't recognise them as a valid format for the file. It is all too difficult for me. I will wait for ATI to remedy their problem.

---

### Post by namaste on 2008-12-09
Thanks jcmorris. Added the options to X11, restarted and flickering has stopped.

---

### Post by robertpolson on 2008-12-10
> **jcmorris said:**
> I have a 3840 that had the same problem. You need to add this to the section Device under fglrx or radeon depending on what driver you use.

Option      "VideoOverlay" "off"
Option      "OpenGLOverlay" "on"
Option      "TexturedVideo" "off"

That works. Thank you.

---

