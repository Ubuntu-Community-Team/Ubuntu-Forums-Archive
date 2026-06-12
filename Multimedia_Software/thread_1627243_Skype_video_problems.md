---
title: "Skype video problems"
date: 2010-11-21
forum: Multimedia Software
---

### Post by Stavroscph on 2010-11-21
Hi,

I am using Ubuntu 10.10 and I am experiencing some video problems when i am using Skype. I am using a Dell Studio 1535 Laptop with a Creative Lab Integrated Camera. 
More specific during a video call my contacts can receive my video, thus my camera works, but on the contrary I can't see them when they open their camera. 
In the call dialog box of Skype there is only a white window and it looks like something trying to pop up but in the end nothing happens. What is more, I cannot also see my self when I open my camera.

I hope there will be any solution:)

Thank you in advance.

---

### Post by xc3RnbFO8P on 2010-11-21
Try to start Skype in Terminal:
> LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

---

### Post by Stavroscph on 2010-11-22
> **Ringi said:**
> Try to start Skype in Terminal:

Hello and thanks for your reply.

I did what you mentioned but then the following error occurs:  

X Error, request 133, minor 18, error code 8 BadMatch (invalid parameter attributes) 

I would really appreciate any help:)

---

### Post by xc3RnbFO8P on 2010-11-22
Do you have cairo dock?

---

### Post by Stavroscph on 2010-11-26
Hello,

Yes I have a Cairo dock installed but fortunately I solved this issue since Cairo dock was removed from my start up applications.The Cairo dock was the problem and this issue solved from me.Thanks a lot for your reply and suggestion.

---

### Post by shriyanshi on 2011-02-15
My creative web cam doesnt work on linux while it works perfectly in windows xp kindly help

---

