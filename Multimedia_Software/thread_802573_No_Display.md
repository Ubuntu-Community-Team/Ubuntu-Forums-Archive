---
title: "No Display"
date: 2008-05-21
forum: Multimedia Software
---

### Post by TR13 on 2008-05-21
Hello,

I just installed Ubuntu, after it restarted for the first time it asked me to choose the O/S i wanted. So i choose Ubuntu and then my monitor displayed an error ( H frequency and V frequency out of range) and then everything went blank.. Please help.. Thanks,

---

### Post by overdrank on 2008-05-21
> **TR13 said:**
> Hello,

I just installed Ubuntu, after it restarted for the first time it asked me to choose the O/S i wanted. So i choose Ubuntu and then my monitor displayed an error ( H frequency and V frequency out of range) and then everything went blank.. Please help.. Thanks,

Hi and you can try the keys, ctrl, alt,F1 and this will bring you to the command prompt then reconfigure your xorg
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then sudo reboot
If you can not reach the command line then you can try from recovery mode.

---

