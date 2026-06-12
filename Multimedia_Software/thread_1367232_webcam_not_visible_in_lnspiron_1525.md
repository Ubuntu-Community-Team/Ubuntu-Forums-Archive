---
title: "webcam not visible in lnspiron 1525"
date: 2009-12-29
forum: Multimedia Software
---

### Post by jaydeeep on 2009-12-29
I am working on Inspiron 1525 laptop, I have inbuilt webcam , but i cannt open my webcam nor i can take my picture or video. in sort I dont have any software to run my inbuilt webcam.
How can i start my cam?

---

### Post by emergingtechnologies on 2010-01-24
> **jaydeeep said:**
> I am working on Inspiron 1525 laptop, I have inbuilt webcam , but i cannt open my webcam nor i can take my picture or video. in sort I dont have any software to run my inbuilt webcam.
How can i start my cam?

I just searched these forums and found the answer to this question and it worked for me and my Insiron 1525:


Code:

sudo rmmod uvcvideo
sudo modprobe uvcvideo


Try it.

---

