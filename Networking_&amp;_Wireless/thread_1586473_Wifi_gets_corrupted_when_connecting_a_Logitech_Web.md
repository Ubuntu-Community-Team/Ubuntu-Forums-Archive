---
title: "Wifi gets corrupted when connecting a Logitech Webcam"
date: 2010-10-02
forum: Networking &amp; Wireless
---

### Post by jubantu on 2010-10-02
Hi there,

I installed Skype on my Ubuntu 10.04 laptop and tried my webcam. When I connect the cam via USB my Wifi connection gets corrupted. Actually it happens right in the moment when I click the "Test" button inside the Skype software -> Options -> Video. Then my Wifi internet connection is gone forever. I had to download a Realtek driver to restore it with the following steps:

```
tar xzf r8101-1.019.00.tar.bz2 
cd r8101-1.019.00 
sudo -E make clean modules   
sudo make install   
sudo depmod -a
sudo update-initramfs -u

Restart!
```
Well, if I connect the webcam again and try "Skype -> Options -> Video -> Test" again, the Wifi connection is ruined again. 

What can I do to get my Wifi and Logitech webcam working?

---

