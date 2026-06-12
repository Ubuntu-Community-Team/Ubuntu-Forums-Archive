---
title: "motherboard gigabyte ga-f2a55m-ds2 linux drivers"
date: 2014-01-07
forum: Multimedia Software
---

### Post by soulcat on 2014-01-07
hi

installed the below motherboard couple weeks ago, getting very poor performance from on board graphics, are there any drivers that can be installed to improve this USING UBUNTU


motherboard gigabyte GA-f2a55m-ds2 

regards

---

### Post by Bucky Ball on 2014-01-07
*Thread moved to **Multimedia & Video**.*

Hard without any details. Please post the output of:

```
sudo lshw -C video
```

Have you looked in Additional Drivers?

---

### Post by Willyweasel on 2014-01-08
You need to install the amd graphics drivers, but that is a fm2 socket motherboard so your graphics are on the apu (cpu+gpu). If you tell me what processor you installed I could point you in the right direction for the video drivers. If you don't know what processor you have install please post the output of:
```
sudo lshw -C cpu
```

---

### Post by soulcat on 2014-01-11
sorted downloaded and installed AMD catalyst software for linux from AMD website, now ok

cheers

---

