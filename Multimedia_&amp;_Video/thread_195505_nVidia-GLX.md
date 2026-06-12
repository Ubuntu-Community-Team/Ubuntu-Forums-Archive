---
title: "nVidia-GLX"
date: 2006-06-12
forum: Multimedia &amp; Video
---

### Post by MrSam on 2006-06-12
I've been told I need the nVidia-GLX drivers to get my dual monitor setup going. Not sure where that is. I DL'd this one - NVIDIA-Linux-x86-1.0-8762-pkg1.run - from the nVidia site but I'm not sure if it's the GLX or not.

---

### Post by Perfect Storm on 2006-06-12
Open the terminal and grab the driver from the repo:

```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable

```

reboot.

---

### Post by tseliot on 2006-06-13
Artificial Intelligence's suggestion is right.

Nonetheless "sudo nvidia-glx-config" enable is kind of broken in Dapper.

I suggest you to use the following command instead:
```
sudo nvidia-xconfig
```

---

