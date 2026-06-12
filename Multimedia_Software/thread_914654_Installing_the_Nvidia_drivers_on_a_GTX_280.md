---
title: "Installing the Nvidia drivers on a GTX 280"
date: 2008-09-09
forum: Multimedia Software
---

### Post by jrharvey on 2008-09-09
Ok so I spent hours of research on this trying to figure out what I was doing wrong. Just so everyone knows before trying this, YOU WILL THROW SOMETHING IF YOU DONT FOLLOW INSTRUCTIONS. First simply download the drivers from the nvidia website and follow instructions ( i wont go over this since there are multiple threads on this already. After deleting the old drivers and installing your new ones, ubuntu WILL boot up and display a GDM at 600x400 and its very anoying. You can try to change the resolution all you want and even edit your Xconf but it wont work. The fix is to simply run this comand in the terminal  ```
sudo nano /etc/default/linux-restricted-modules-common
```
and make sure the bottom most line looks like this ```
DISABLED_MODULES="nv nvidia_new"
```
Then simply hit ctrl O to save the file and reboot. Your system should just automatically post at your native resolution and if not then you should be able to manually change it to the res you want.

---

