---
title: "API mismatch between driver and kernel"
date: 2008-06-01
forum: Multimedia Software
---

### Post by superuzr001 on 2008-06-01
As the title say I am getting an error:

API mismatch; the nvidia kernel module has version 169.12 but the nvidia driver component has version 173.14.05.

and I am unable to load X because of that. Something of note, under the hardware drivers menu i have the nvidia accelerated graphic driver but it's not enabled.  Most likely when I did the install through there that i installed 169.12 but when i found out there is newer from nvidia i went grabbed that.  even though it says no preconfigured kernel interface for my system it goes ahead and does the install for it anyway but for some reason it's still giving me an error.  Is there a safe way to remove all of nvidia manually instead of just doing the installer or did i miss something along the way?  I never had this problem ever so i don't want to start janking stuff unless there is no easy fix.

2.8G
7800GS
1GB Ram
ubuntu v8.04

thakns

---

### Post by superuzr001 on 2008-06-01
*bump*

---

### Post by prshah on 2008-06-01
> **superuzr001 said:**
> 
API mismatch; the nvidia kernel module has version 169.12 but the nvidia driver component has version 173.14.05.


Install the latest driver with```

sudo apt-get update
sudo apt-get nvidia-glx-new

```

It will automatically remove traces of the "old" driver.

Actually, both drivers (old and new) _may_ be the same. The issue is that to prevent proprietary drivers being replaced by open-source drivers when you upgrade the kernel, the proprietary installer put a fake, "higher" version number, which will change from kernel upgrade to kernel upgrade. I forgot the technical term for it...

---

### Post by superuzr001 on 2008-06-01
I get a "E: Invalid operation nvidia-glx-new"

when I run "sudo apt-get nvidia-glx-new"

thx for the tip tho

---

### Post by superuzr001 on 2008-06-02
any other ideas?  By default, does ubuntu installs the nvidia drivers?  I am thinking.. if it's not the case I can just run the install again since it's fresh anyway and I will just DL the latest from Nvidia's site.  The kernel I installed was older version from the one on Nvidia's site, so by default it should complile a later version of the kernel drivers but it wasn't so I would think we need to remove the one already on there.

---

### Post by prshah on 2008-06-02
> **superuzr001 said:**
> I get a "E: Invalid operation nvidia-glx-new"

when I run "sudo apt-get nvidia-glx-new"

thx for the tip tho

Oopps... my mistake: try```
sudo apt-get install nvidia-glx-new
```

---

### Post by superuzr001 on 2008-06-02
fair enough hehe.  I'll try that when I get home.  Ty.

---

### Post by Domie on 2008-07-13
No solution. It is nvidia-glx-new that caused the problem in the first place.

The drivers from nvidia.com do work, but when you reboot, everything is back to black.

---

### Post by snugglenutz on 2008-12-02
I don't know if this has been solved yet but I was having the same problemo after upgrading to 8.10.  I used Envy and the Restricted Drivers and nothing worked.  I finally got it to work last night by killing X and installing NVIDIA-Linux-x86-177.82-pkg1.run from Nvidia.com.  Now everything works perfectly and I am play Unreal again. Hopefully it'll work for you...

---

### Post by dvo on 2009-01-02
Thanks a lot!

For me, using Ubuntu hardy 2.6.24-22-generic amd64, envy did not work either, but NVIDIA-Linux-x86_64-177.82-pkg2.run 
from [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

---

