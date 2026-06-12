---
title: "Cheese shows an error, temporarily solved by playing with the resolution"
date: 2022-12-13
forum: Multimedia Software
---

### Post by Paddy Landau on 2022-12-13
The last time when I used Cheese (30th September), it worked perfectly.

Today, it's playing a new game. When I start Cheese, it gives the message, "There was an error playing video from the webcam."

To solve this, I have to:


[LIST=1]
[*]Preferences > change the resolution for both Photo and Video to its lowest setting (160×120)
[*]Close Cheese and reopen it *immediately*
[*]Preferences > change the resolution for both Photo and Video to another setting
[/LIST]
Then, Cheese works. But once I close Cheese, it stops working again the next time I reopen it (unless I reopen it *immediately*).

Running Cheese from the terminal when it's not working gives this message:
```
(cheese:20335): cheese-WARNING **: 11:31:40.287: Internal data stream error.: ../libs/gst/base/gstbasesrc.c(3127): gst_base_src_loop ():
/GstCameraBin:camerabin/GstWrapperCameraBinSrc:camera_source/GstBin:bin18/GstPipeWireSrc:pipewiresrc1:
streaming stopped, reason not-negotiated (-4)
```
Running Cheese from the terminal when it's working gives this warning message if I'm using higher settings (e.g. 1920×1080):
```
(cheese:20706): cheese-WARNING **: 11:33:29.694: A lot of buffers are being dropped.: ../libs/gst/base/gstbasesink.c(3143): gst_base_sink_is_too_late ():
/GstCameraBin:camerabin/GstViewfinderBin:vf-bin/ClutterGstVideoSink:cluttergstvideosink0:
There may be a timestamping problem, or this computer is too slow.
```
Running Cheese from the terminal when it's working gives no message if I'm using one of the lower settings.

I'm using Ubuntu 22.04 with the default Cheese installation version 41.1.

What can I do to fix this, please?

---

### Post by Paddy Landau on 2023-06-17
Well, Cheese is still not working, and it's worse. The temporary fix mentioned in the first post doesn't work any more. Cheese just doesn't work, period.

Any ideas?

---

### Post by sina-imani on 2023-10-06
I had the same issue on Ubuntu 22.04. I finally was able to cope with the problem by disabling Wayland on Ubuntu.
This can be done by editing the /etc/gdm3/custom.conf file. Open a terminal and type:

$ sudo nano /etc/gdm3/custom.conf

At the 7th line change the value of WylandEnable to false.
Then save and close the file.
Finally, close every program other than terminal (REMEMBER TO SAVE YOUR WORK) and restart gdm3:

$ sudo systemctl restart gdm3

The above command would log you out and you should log into your account.
I was able to work with cheese at this step.
(I'm not sure if 'sudo systemctl restart gdm3' is necessary or a manual logout/login will do the job. I just did it for having done a full restarting operation and it worked fine)

---

### Post by Paddy Landau on 2023-10-06
> **sina-imani said:**
> I finally was able to cope with the problem by disabling Wayland on Ubuntu.
Unfortunately, that didn't work with me (I even restarted the computer to check).

That's unsurprising, because I wasn't using Wayland anyway; I've been using X.Org because of certain functionality that I need.

Oh, well.

---

### Post by faliagas on 2023-12-02
I had the same problem. I removed the deb application (with purge) and installed the snap app, which was version 44.1. That worked for me.

---

### Post by Paddy Landau on 2023-12-02
> **faliagas said:**
> I had the same problem. I removed the deb application (with purge) and installed the snap app, which was version 44.1. That worked for me.
Thank you for the idea.

[LIST]
[*]I uninstalled cheese (version 41.1). I note that you can't uninstall cheese-common, but that's OK.
[*]I installed snap's cheese (version 44.1). Alas, I had the same problem!
[*]I uninstalled snap's cheese, and instead installed flatpak's cheese (version 43.0). This time, it worked!
[/LIST]
So, for me, the flatpak version works, while neither the snap nor the PPA version works.

Thank you!

---

