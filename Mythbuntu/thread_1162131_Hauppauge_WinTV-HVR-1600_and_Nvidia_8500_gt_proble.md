---
title: "Hauppauge WinTV-HVR-1600 and Nvidia 8500 gt problem"
date: 2009-05-17
forum: Mythbuntu
---

### Post by mark467 on 2009-05-17
I had a working 9.04 install with a nvidia 8500 gt and an old ati tuner. I took out the ati and put in the WinTV-HVR-1600 and on boot I get failed to initialize nvidia. I did a fresh install with the new tuner and I get all the way through configuring and on reboot get the same thing. Any help would be appreciated.

---

### Post by 67GTA on 2009-05-17
[http://ubuntuforums.org/showthread.php?t=1004660](http://ubuntuforums.org/showthread.php?t=1004660)

---

### Post by mark467 on 2009-05-17
Cool that worked. had to set vmalloc to 512 though

---

### Post by 67GTA on 2009-05-17
Yeah, it really depends on your virtual memory allocation. It could be 192, 256, 512, etc... Glad that worked. I filed a bug last year for this, but since the cx18 module comes from Hauppauge, the Ubuntu devs won't fix. Your card should be initialized at boot. Open a terminal and run ```
dmesg | grep cx18
``` to see messages about your card.

---

