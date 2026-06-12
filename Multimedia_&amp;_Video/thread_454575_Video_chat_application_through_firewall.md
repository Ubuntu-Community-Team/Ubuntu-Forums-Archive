---
title: "Video chat application through firewall"
date: 2007-05-25
forum: Multimedia &amp; Video
---

### Post by lexarrow on 2007-05-25
Hello,

I'm behind a cache http proxy in my university campus and I am looking for a video chat application that will work through the firewall. I already tried amsn and ekiga but they don't work.

On Windows Skype was working, but skype for linux doesn't have webcam features yet.

Additional information: Skype on Windows used ports 80 and 443 as alternates.

Thanks in advance!

---

### Post by anoir on 2007-05-26
I'm not knowledgeable about firewall and port forwarding, but I do recommend that you try Wengo instead of Skype. It has all the functionalities of Skype, while it follows open standard and the software, wengophone, is an open source software. As a bonus, its UI is pretty slick unless you are using GNOME without qtconfig-qt4.

At my home, Ekiga has never worked, but with Wengo I can talk to people with video.

Wengo in repos are quite old and thus it is advised to download the latest 2.1 binary distribution from their website.

---

### Post by lexarrow on 2007-05-27
I've got 2 problems: 

1 When I try to run wengo 2.1 I get the following error:
```
(debug) 12:59:19 int main(int, char**): WengoPhone started
(debug) 12:59:19 virtual void WebcamDriver::cleanup(): Cleaning up the Meta webcam driver
(debug) 12:59:19 virtual bool FileReader::open(): loading /home/alex/.wengophone/config.xml
(debug) 12:59:19 virtual bool FileWriter::open(): saving to /home/alex/.wengophone/config.xml
(debug) 12:59:19 virtual bool FileReader::open(): loading /home/alex/.wengophone/config.xml
```

2. After installing wengo from the repository I can't use the webcam (in ekiga works).
Note: I use the V4L2 drivers from uvc

Thanks!

---

### Post by anoir on 2007-05-27
> 
1 When I try to run wengo 2.1 I get the following error:


This message doesn't look like an error. Wengo aborts after spitting this?

> 
2. After installing wengo from the repository I can't use the webcam (in ekiga works).
Note: I use the V4L2 drivers from uvc


You are using a high resolution webcam from Logitech, right? I experienced the same problem with Qcam for notebook. Although uvc works with those webcams and wengo does work with V4L2, it can't work with webcams that handle only mjpeg stream as of now. Now I'm using a rather old little webcam for video with V4L1. For me this is ok, because the video quality is usually determined by bandwidth, not by cams.

---

### Post by lexarrow on 2007-05-29
I got it to connect, but can't use the webcam. I have a Ricoh built-in webcam for my dv2025nr HP laptop.

Any suggestions?

Should wengo detect the webcam automatically or do I have to add something?

---

### Post by anoir on 2007-05-29
In my experience, wengo auto-detects webcams as long as its driver is correctly installed, although in some cases choosing a webcam results in abortion. I don't know what kind of cam is integrated in your laptop, but it might be the cases that the webcam only supports mjpeg and thus can't work with the current version of wengophone. It would be good to ask wengo stuff about that. They might know.

---

### Post by lexarrow on 2007-05-29
I  asked wengo and I am waiting for an answer.

Thank you very much for your support!

---

