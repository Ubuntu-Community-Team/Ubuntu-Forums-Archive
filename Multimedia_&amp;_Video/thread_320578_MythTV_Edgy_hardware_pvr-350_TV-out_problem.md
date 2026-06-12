---
title: "MythTV Edgy hardware pvr-350 TV-out problem"
date: 2006-12-17
forum: Multimedia &amp; Video
---

### Post by pheno on 2006-12-17
I have a system running an AMD 1.6GHz Duron with 1GB RAM. I added a Hauppauge WinTV-PVR-350 and am trying to get MythTV running...

I installed edgy, then did a Combined Backend, Frontend, & Regular Desktop install 
([https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop)](https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop)).

At “Setup Additional Hardware”, I detoured to “MythTV Edgy hardware”. I did the “Install IVTV Edgy”, then detoured to “To get  X running on PVR-350 out click here”.

I entered the command “depmod -a” and got 

“FATAL: Could not open /lib/modules/2.6.17-10-generic/modules.dep.temp for writing:
 Permission denied”

any help appreciated!

---

### Post by superm1 on 2006-12-17
Try running 
```
sudo depmod -a
```

To run this as root

---

### Post by pheno on 2006-12-18
thanks!

---

