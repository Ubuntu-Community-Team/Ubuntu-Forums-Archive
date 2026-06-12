---
title: "Canon PowerShot A70 as a Webcam"
date: 2010-02-18
forum: Multimedia Software
---

### Post by deepee_oz on 2010-02-18
Hi All

There are Windows programs like extrawebcam that can capture live video natively from these cameras for use with conferencing apps like Skype.

I've had a look at the UVC driver list and can't see anything there.

Anyone have any tips?

This little project is really just for a bit of fun as I have one of these lying around and it would be good to "recycle" it!

Thanks
deepee

---

### Post by tgalati4 on 2010-02-18
There are remote control programs but the older powershots don't have a webcam mode.  My  A70 died recently.  Its  second death.

---

### Post by deepee_oz on 2010-02-18
Thanks, I think the windows programs exploit the remote control capability of these cameras to make them work like webcams.

I'm hoping there may be a Linux equivalent?

---

### Post by tgalati4 on 2010-02-18
There is a gstfakevideo hack, but I couldn't get it to work.   You could install the remote control, run the live view mode and see what /dev/video gets created.  Set that device in skype and see if you can share the video device.

---

### Post by deepee_oz on 2010-02-18
Thanks, I'll give it a go over the weekend and post back.

---

### Post by tgalati4 on 2010-02-18
My A70 died (LCD intermittent) so I can't test it.  If you can get the psremote to display a live image then get the name of the /dev/videodevice and put that in skype, it might work.

---

### Post by xc3RnbFO8P on 2010-02-18
I use Canon A590 IS.
[http://ubuntuforums.org/showpost.php?p=6550721&postcount=2]("http://ubuntuforums.org/showpost.php?p=6550721&postcount=2")

---

### Post by deepee_oz on 2010-02-18
Thanks, Ringi.
I know that's one way of achieving it but I would like to avoid using any extra hardware.

tgalati4, you mention psremote, I did a search and see it's a Windows app.
Is there anything similar for Linux?

---

### Post by tgalati4 on 2010-02-19
Yes, there is, but I can't remember what it's called--you will have to search for it.

---

