---
title: "Intel Proshare Webcam"
date: 2009-02-28
forum: Multimedia Software
---

### Post by crokett on 2009-02-28
I have an Intel Webcam I am trying to get working with Ubuntu. xSane will scan an image with the camera except it is very wavy and grainy. 

lsusb shows it as detected, lsmod lists the  required spca505 module as being installed.  I looked around on the web and this is the info on the camera:

vendor: 0733 ("ViewQuest Technologies, Inc."), product: 0430 ("Intel Pro Share Webcam")

More research says that the camera is actually supported under spca501.  Does spca505 support spca505 and earlier, or is spca501 a different module and the one I should be loading?

---

