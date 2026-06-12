---
title: "Wrong Nvidia driver"
date: 2007-03-20
forum: Multimedia &amp; Video
---

### Post by Kasper42 on 2007-03-20
Hi,

I was trying to install Beryl and first I read I had to install Nvidia drivers. I followed [this guide]("http://news.softpedia.com/news/Install-Nvidia-and-ATI-video-drivers-on-Ubuntu-Edgy-44388.shtml") and I was reading around the nvidia drivers and heard about the Envy Script. Anyway, I foolishly installed Envy and the nvidia driver as well as installing the nvidia driver through the guide above. Envy reqused that I restart after the nvidia driver was installed, so I did but when I restarted the X-server it seemed to be broken.

> Failed to start the X server(your graphical interface). It is likely that it is not set up correctly

So I looked at the error log which read (at the bottom of the log)

> (WW) NVIDIA(0): The NVIDIA GeForce4 MX 4000 GPU installed in this system is
(WW) NVIDIA(0):        supported through the NVIDIA 1.0-96xx Legacy drivers.
(WW) NVIDIA(0):        Please visit
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) for
(WW) NVIDIA(0):        more information. The 1.0-9746 NVIDIA driver will ignore
(WW) NVIDIA(0):        this GPU. Continuing probe...
(EE) No devices detected.

Fatal server error:
no screens found

Do I need to reinstall the other Nvidia driver then? Please help! Thanks :)

---

### Post by Kasper42 on 2007-03-21
Sorry to double post but I'm not sure what to do :confused: 

Should I try to reinstall the nvidia driver through envy in recovery mode?

---

### Post by Kasper42 on 2007-03-21
I managed to fix this so this may come in handy for people who have the same/similar problems.

I uninstalled the old driver and I tried to install the nvidia driver through envy but this seemed to fail. I then chose to install the Nvidia driver manually, I was greeted with three options-9755, 9631 or 7184. I tried both the 9755 and 9631 drivers but neither worked but on my final attempt,7184 seemed to work!

I can now log back into ubuntu!

I have now installed beryl [using this guide]("http://news.softpedia.com/news/Ubuntu-Edgy-Desktop-Effects-with-Beryl-44785.shtml") but I am greeted by the error:> **************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension


I've searched for this error and other threads seem to suggest rolling back to an earier beryl. Do I have any other options? Thanks:)

---

