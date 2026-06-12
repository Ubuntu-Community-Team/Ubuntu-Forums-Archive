---
title: "installing the commercial nvidia driver (IA-32)"
date: 2006-06-18
forum: Multimedia &amp; Video
---

### Post by fakie_flip on 2006-06-18
I was following the wiki guide to install the NVIDIA driver from nvidia's website. I am getting this message:

WARNING: The NVIDIA Vanta/Vanta LT GPU installed in this system is
supported through the NVIDIA legacy Linux graphics drivers.
Please visit [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) for more
information. The 1.0-8762 NVIDIA Linux graphics driver will
ignore this GPU.

I don't have a gpu. Why would I get this message? Next I get this message:

WARNING: You do not appear to have an NVIDIA GPU supported by the 1.0-8762
NVIDIA Linux graphics driver installed in this system. For
further details, please see the appendix SUPPORTED NVIDIA GRAPHICS
CHIPS in the README available on the Linux driver download page at
[www.nvidia.com](www.nvidia.com).

Where is the readme for video cards supported by the nvidia linux driver (IA-32)? I have searched the website and cannot find it. Next I get this message:

No precompiled kernel interface was found to match your kernel; would you
like the installer to attempt to download a kernel interface for your
kernel from the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?)

Yes No

What is a precompiled kernel interface and why do I need it? Is it the same as the source code for the kernel?

---

### Post by meng on 2006-06-18
I think a GPU is a graphics processing unit.
Have you tried installing nvidia-glx from repositories? This should install/configure nvidia drivers for you.

---

### Post by tseliot on 2006-06-18
Read my guide, please:
[http://ubuntuforums.org/showthread.php?t=139264]("http://ubuntuforums.org/showthread.php?t=139264")

---

### Post by fakie_flip on 2006-08-11
> **meng said:**
> I think a GPU is a graphics processing unit.
Have you tried installing nvidia-glx from repositories? This should install/configure nvidia drivers for you.

Is a GPU the same thing as a graphics adapter aka graphics card?

---

### Post by tseliot on 2006-08-12
> **fakie_flip said:**
> Is a GPU the same thing as a graphics adapter aka graphics card?

It's part of a card. Read this for further information:
[http://en.wikipedia.org/wiki/Graphics_processing_unit](http://en.wikipedia.org/wiki/Graphics_processing_unit)

BTW post the output of this command:
```
lspci | grep VGA
```

---

