---
title: "nvidia help please"
date: 2009-03-27
forum: Multimedia Software
---

### Post by ssj3g0ku on 2009-03-27
hello
first of all i installed today ubuntu 8.04 x86
i have a video card 7300 GT 256 ddr3 pci
and i dont want to install the driver that ubuntu has recomended me..
i saw on nvidia.com that the latest driver is  180.29 and the recomended one is 170 i think..
there are diferences
please i need help i dont know how to install the new nvidia drivers it needs some kernel things...
uname -r output "2.6.24-19-generic"
thank you

---

### Post by wolfen69 on 2009-03-27
download [this]("http://us.download.nvidia.com/XFree86/Linux-x86/180.29/NVIDIA-Linux-x86-180.29-pkg1.run") file and put it in your home folder. then open a terminal and do
```
sh NVIDIA-Linux-x86-180.29-pkg1.run
```
follow the prompts.

---

### Post by ssj3g0ku on 2009-03-27
> **wolfen69 said:**
> download [this]("http://us.download.nvidia.com/XFree86/Linux-x86/180.29/NVIDIA-Linux-x86-180.29-pkg1.run") file and put it in your home folder. then open a terminal and do
```
sh NVIDIA-Linux-x86-180.29-pkg1.run
```
follow the prompts.

ehh i tried that but you have to kill gdm... 
and i did that 
the display driver is trying to download a kernel patch or something
and he cants so it quits setup

---

### Post by norwoods on 2009-03-27
download the README file from nvidia where you downloaded the driver and follow the install directions in the README file.

---

### Post by sandy8925 on 2009-03-28
Try the following:

sudo apt-get install nvidia-glx-180

It installs the 180.11 version driver.
I did it on Ubuntu 8.10 and it worked.Dunno about 8.04 though.......

---

### Post by sandy8925 on 2009-03-28
I also tried installing the nvidia 180.29 drivers but my xserver broke and had to uninstall the driver. I guess you'll have to do some configuration first......

---

### Post by Insane_Homer on 2009-03-28
ignore me, my reply was jaunty related.

---

### Post by xc3RnbFO8P on 2009-03-28
> ignore me, my reply was jaunty related.
I have the same problem :)
Latest update in Jaunty Beta :
>   * Add 102_geforce_7300_gt.patch:  Adds pci id for GeForce 7300 GT
    (LP: #320671)

---

### Post by ssj3g0ku on 2009-03-28
thank you guys..
ill try
but one more question.
if i installed other drivers 
how do i completley remove them ?

---

