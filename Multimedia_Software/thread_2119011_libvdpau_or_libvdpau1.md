---
title: "libvdpau or libvdpau1 ?"
date: 2013-02-22
forum: Multimedia Software
---

### Post by JayIyer on 2013-02-22
I want to use the nvidia on my laptop. It has the GeForce GT 540 M. 
I am Using ubuntu 12.04.
I see in nvidia site that libvdpau it is supported for the device. I have done the following:
1. an apt get install nvidia-current 
2. also got libvdpau1
Problem is when I try "vdpauinfo" it complains of device not found: 1
I googled. and did a few relinkings of files. Still the same.
One thing is I dont see any file named: "libvdpau" by itself.
So, basically I am trying to figure out if I have done the main steps of installation right.
 
Any help greatly appreciated.
<my goal is to use mythtv 0.25 with it>

---

### Post by Yellow Pasque on 2013-02-22
Is this an Optimus laptop? If so, is bumblebee installed?

---

### Post by JayIyer on 2013-02-22
This is a "MSI GE 620 Core i7" laptop. Does that help ? 
Thanks for your time.
Jay

---

### Post by Yellow Pasque on 2013-02-22
What does this return?
```
lspci | grep -i VGA
```
If it returns an intel and nvidia GPU, then you have Optimus.

---

### Post by JayIyer on 2013-02-23
lspci | grep -i VGA

output:

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 540M] (rev a1)

Could you kindly tell me how I should proceed ?

Thanks a bunch for your help.

---

### Post by Yellow Pasque on 2013-02-23
You need to uninstall nvidia(-current), reboot and make sure graphics are working. If so, you can proceed with Bumblebee install:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by JayIyer on 2013-02-23
thanks. Have one more question since it is better to be cautious in doing these:
should I do a
apt-get remove
or
apt-get purge

many thanks

---

### Post by Yellow Pasque on 2013-02-23
Do apt-get purge to remove old configuration files.

---

