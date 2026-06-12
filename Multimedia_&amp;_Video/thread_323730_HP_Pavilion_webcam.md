---
title: "HP Pavilion webcam"
date: 2006-12-22
forum: Multimedia &amp; Video
---

### Post by Yako on 2006-12-22
Hi,

I have a HP Pavilion dv1000 series (dv1668ea) laptop, and it has a webcam embedded in the screen. Problem is, i can't seem to get it working.
I have read how-to's about the pavilion dv2000/dvXXXX webcams, but none work. uvc-video doesn't do anything.

Device manager says the thing is a USB2 imaging interface.
Any help is greatly appreciated.

---

### Post by patrimesa on 2007-08-01
Hey

I think I have the same problem as you! I've got an HP dv 1000 with embedded webcam... the only thing is that I don't really know much about how Ubuntu works or how to install stuff in it... did you ever solve your problem? could u help me out?
many thanx!

---

### Post by asatishc on 2007-08-02
I tried installing webcam drivers. After trying some of the softwares, I found out tht ekiga is the only software that makes the webcam work. rest give an error message saying device not found /dev/video0

So, try installing v4l2 and uvc video, and then see if ekiga works.

---

### Post by Yako on 2007-08-02
Hi, after a lot of searching I found it.

This worked for me, though the image quality is far from excellent:
[http://lsb.blogdns.net/ry5u870/](http://lsb.blogdns.net/ry5u870/)

---

### Post by ckung on 2008-01-18
> **Yako said:**
> Hi, after a lot of searching I found it.

This worked for me, though the image quality is far from excellent:
[http://lsb.blogdns.net/ry5u870/](http://lsb.blogdns.net/ry5u870/)


Hi Yoke. 

I have the same problem but the link you provided is not working.

Can you help to post the solution again?

Thank you!
Charles

---

### Post by Yako on 2008-01-20
[Here](http://avilella.googlepages.com/vaiosz). Scroll down a bit to get to the download link. (r5u870-0.10.0.tgz)

---

