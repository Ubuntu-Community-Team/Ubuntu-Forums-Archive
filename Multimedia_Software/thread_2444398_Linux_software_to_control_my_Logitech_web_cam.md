---
title: "Linux software to control my Logitech web cam?"
date: 2020-05-29
forum: Multimedia Software
---

### Post by SeijiSensei on 2020-05-29
I switched over to Windows today for a Zoom call.  Before I did so, I installed the utility application from Logitech to control my camera (a 9000 Pro, I believe).  That allows me to pan the camera and zoom in and out.  I can't find any equivalent software for Linux.  Any suggestions?  Things like Cheese don't seem to support these kinds of controls.  Moreover I could control the camera with the utility while on the call and see the effects immediately.

---

### Post by TheFu on 2020-05-29
I have a C920 Pro.  None of the easy-to-use software does the panning, but OBS can.  OBS is pretty much overkill and you have to setup a virtual webcam (kernel module) for the video conference software to see. OBS generates the output for that virtual webcam. OTOH, with OBS, you can generate any special effects you like regardless of what the conferencing tool supports or doesn't support.  Want to have a green screen setup with you warping through space or sitting on a white-sand beach in the Carribean?  Not a problem. ;)

There is also a CLI tool to send V4L2 commands ... 
```
$ v4l2-ctl -d /dev/video0 -c zoom_absolute=200
$ v4l2-ctl -d /dev/video0 -c brightness=100
```
are the ones I use, but there has to be 50 other -c options.

---

### Post by SeijiSensei on 2020-05-30
I'm on the planning committee for the 50th Reunion of my college class a year from now. As you can imagine, we're considering methods to convene virtually if necessary including live streaming of some events like symposia.  OBS looks like it might come in handy for that.

I'll take a look at the vl42 commands.  Thanks!

---

### Post by Autodave on 2020-05-31
You may also want to look at* gucview.*

---

