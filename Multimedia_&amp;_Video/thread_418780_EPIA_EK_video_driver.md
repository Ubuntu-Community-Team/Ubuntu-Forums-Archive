---
title: "EPIA EK video driver"
date: 2007-04-22
forum: Multimedia &amp; Video
---

### Post by steve on linux on 2007-04-22
I have installed xubuntu 6.10 on a VIA EPIA EK8000EG mini-itx board with 256MB RAM.  The video performance seems incredibly slow - with glxgears I get about 1 frame per second.  I have searched for video drivers but can't find any for the Luke chipset.  I am new to Linux so have struggled to find out what is wrong.  Can anyone help?

Thanks

---

### Post by mshives on 2007-05-15
Hello Steve,

I am using the EK100000G as my main system. It has 512mb ram (tried 1GB but it just would not remain stable no matter the distribution or manufacturer RAM).

I have recently upgraded from 6.10 to 7.04. With both version I have used the OpenChrome drivers with great success. Just follow the instructions here:

[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

There is even a build for xine that takes advantage of via driver. Used to be that before installing the OpenChrome driver, GL-Gears was very slow and ate up the CPU resources. After installing the driver, GL-Gears ran much faster and smoother and cpu never went above 15 percent utilization. 

Hope this helps

-mshives
---
Open Source Software: Opening doors to more software solutions in a world full of Windows.

---

### Post by steve on linux on 2007-05-16
Thanks - I'll give that a try

---

