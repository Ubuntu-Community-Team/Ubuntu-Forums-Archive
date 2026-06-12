---
title: "How can I adjust my webcam settings?"
date: 2009-11-01
forum: Multimedia Software
---

### Post by DaftPyramid on 2009-11-01
I've been using Skype (2.1 Beta), but everyone says my video is very dark, laggy, and low resolution. I can't figure out how to adjust my webcam's brightness, contrast, etc. Is this possible?

By the way, I use Cheese, and the video appears bright and responsive, but it's bad in Skype. 

Any help would be greatly appreciated, thanks.

---

### Post by LarryMi on 2009-11-02
[This Viewer]("http://guvcview.berlios.de/downloads.html") allows me to adjust the brightness etc.

You are lucky to get Skype video working at all.  Whenever I begin to broadcast a video, Skype crashes, and then I have to log in again.

Which version are you using, and where did you get it?

---

### Post by tgalati4 on 2009-11-02
If logitech, install qc-utills.

man qc-set

---

### Post by bslaveboy on 2009-11-06
> **LarryMi said:**
> [This Viewer]("http://guvcview.berlios.de/downloads.html") allows me to adjust the brightness etc.

Thanks! I had the same issue, but that gucview fixed it for me. :)

> You are lucky to get Skype video working at all.  Whenever I begin to broadcast a video, Skype crashes, and then I have to log in again.

Which version are you using, and where did you get it?

I'm busy using the skype from the Synaptic Package Manager in 9.10. It says that it's "Skype (Beta) Version 2.1.0.47. Try that.

Slaveboy
--

---

### Post by fonkamex on 2009-11-28
thanks!

---

### Post by fonkamex on 2009-11-28
> **LarryMi said:**
> [This Viewer]("http://guvcview.berlios.de/downloads.html") allows me to adjust the brightness etc.

You are lucky to get Skype video working at all.  Whenever I begin to broadcast a video, Skype crashes, and then I have to log in again.

Which version are you using, and where did you get it?

Hi everybody!

I had problems with my webcam and skype but now the problem is solved and my video is working too, but is too dark as well.

I found the solution for my video on skype forums:

[http://forum.skype.com/index.php?showtopic=252681&st=0](http://forum.skype.com/index.php?showtopic=252681&st=0)

good luck!

---

### Post by nerdy_kid on 2010-10-04
i know this is an old thread; but found a solution here:
[http://forum.skype.com/index.php?showtopic=106357&st=20&](http://forum.skype.com/index.php?showtopic=106357&st=20&)

use the v4lctl command to adjust the brightness, contrast and color of webcams.  works in realtime with skype 2.1.0.81.

---

### Post by VcDeveloper on 2010-10-28
> **tgalati4 said:**
> If logitech, install qc-utills.

man qc-set

I'm streaming using WebCamStudio to Ustream and I would like to able to adjust other features also for my logitech notebook webcam like the Vert/Horit.  This util said it needs:

Utilities to tweak parameters of your QuickCam Express or similar webcam, and
the quickcam kernel module.
These programs are completely useless without a qc-usb-modules package.

I'm running 10.10 and I don't see this package?

---

### Post by VcDeveloper on 2010-10-28
Cancel that! I found it in WebCamStudio effects tab.....

---

### Post by hesapotman on 2011-03-25
I've had good experiences with a little utility called "v4l2ucp". It provides an easy-to-use GUI for adjusting the properties of V4L2 video capture devices. It even has a live preview feature so you can see the effects of your adjustments in real-time.

After installation, you'll find it under "System -> Preferences -> Video4Linux Control Panel".

I don't know why this utility isn't part of a default Ubuntu install ... It's only like 250kB and VERY useful.

Hope that info helps someone!

---

### Post by saeed Firouzi on 2013-02-12
Ah, many thanks for the info I installed "guvcview" bang everything went tickety boo, there are lots of controls in it, but the default was an excellent choice for the whole lot, brightness, contrast, etc. When revoked Skype, got a well balanced webcam.

---

### Post by codemaniac on 2013-02-12
Thread closed.
As per the Ubuntu Forums Code of Conduct, please do not post in threads more than one year old.

Thanks!

---

