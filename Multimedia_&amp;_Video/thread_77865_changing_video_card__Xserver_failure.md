---
title: "changing video card : Xserver failure"
date: 2005-10-17
forum: Multimedia &amp; Video
---

### Post by hela on 2005-10-17
I made a test install with Ubuntu 5.10 and changed my video card afterwards. new one : ATI Rage Pro 128. Startup screen (boot splash) is okay, but I get no graphic login. Loged in in text mode "sudo Xorg -configure -verbose" ends with missing output driver. 

What is missing?

Where can I find another script for creation of /etc/X11/xorg.conf?

---

### Post by Corvillus on 2005-10-17
Did you try
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by hela on 2005-10-17
yes, the same failure, but I removed the framebuffer option from xorg.conf and the Xserver runs fine!

---

