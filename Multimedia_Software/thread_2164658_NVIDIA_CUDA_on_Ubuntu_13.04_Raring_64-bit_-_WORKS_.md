---
title: "NVIDIA CUDA on Ubuntu 13.04 Raring 64-bit - WORKS on Laptop, DOES NOT WORK on Desktop"
date: 2013-08-01
forum: Multimedia Software
---

### Post by Vivek_Saxena on 2013-08-01
Hi,

I have the following packages installed on my laptop, with a successful CUDA installation:

```

[B]nvidia-current
nvidia-settings-304
[/B]nvdia-visual-profiler
nvidia-cuda-gdb
nvidia-cuda-toolkit
nvidia-cuda-dev
nvidia-insight
libnvtoolsext3.0
nvidia-cuda-doc
nvidia-profiler
nvidia-opencl-dev
libcublas5.0
libcudart5.0
libcufft5.0
libcusparse5.0
libcurand5.0
libnpp5.0
**nvidia304**
libcupti-doc
python-pycuda
python-pycuda-doc
libcupti5.0
python-pycuda-headers[B]
ubuntu-drivers-common
[/B]
```

My laptop has an NVIDIA GT555M which seems to be recognized automatically (and I see an Additional Drivers pane too, which is populated with drivers).

But my desktop (Core i7 920, 24 GB RAM, NVIDIA GTX 780) is posing problems when I try to install any kind of NVIDIA driver (except the .sh file from NVIDIA -- I haven't tried that yet) from the repositories, including any of the abovementioned packages. I have tried nvidia-current and nvidia-304.

On one occasion, when I finally installed nvidia-current and rebooted my system, there was a blank screen from Unity after I entered my login credentials.

My research work for my Master's thesis strongly depends on the use of CUDA on this desktop. I'd really appreciate any guided advice about how I could install CUDA-capable drivers on my desktop. I'll be happy to provide more information.

Thanks in advance!

---

### Post by dino99 on 2013-08-01
Looks like you are not alone with that issue : [http://askubuntu.com/questions/323293/nvidia-drivers-dont-work-with-gtx-780](http://askubuntu.com/questions/323293/nvidia-drivers-dont-work-with-gtx-780) [http://ubuntuforums.org/showthread.php?t=2161464](http://ubuntuforums.org/showthread.php?t=2161464)
Are you using the latest nvidia driver from the edgers ppa ? [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)  Either the 325 or the "persistence" one might fit your needs.

---

### Post by Vivek_Saxena on 2013-08-01
No I am not using that ppa....is it known to work?

EDIT: For reference of other people who might stumble upon this...

[http://www.phoronix.com/scan.php?page=news_item&px=MTM3Nzg](http://www.phoronix.com/scan.php?page=news_item&px=MTM3Nzg)

[http://askubuntu.com/questions/323293/nvidia-drivers-dont-work-with-gtx-780](http://askubuntu.com/questions/323293/nvidia-drivers-dont-work-with-gtx-780)

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

[http://foldingforum.org/viewtopic.php?f=88&t=24623&start=15](http://foldingforum.org/viewtopic.php?f=88&t=24623&start=15) (this link details installation steps for this ppa)

---

### Post by dino99 on 2013-08-01
im using it all the time to get the fixes/updates (319 on my end)

note : be sure to purge the previous nvidia installation (sudo apt-get purge ...) before installing a new one (this avoid unexpected disturbing old settings left behind)

---

### Post by Vivek_Saxena on 2013-08-01
Okay so I have a fresh install of Ubuntu 13.04 with updates and upgrades (sudo apt-get update & sudo-apt-get upgrade)

Will using the above PPA with intructions as given on [http://foldingforum.org/viewtopic.php?f=88&t=24623&start=15#p246377](http://foldingforum.org/viewtopic.php?f=88&t=24623&start=15#p246377) suffice or do I have to install anything before this?

Also if it doesn't work, is there some way I can come back to the fresh install + updates stage? I'm behind a slow internet connection, and I can't afford to re-install Ubuntu every time....

---

