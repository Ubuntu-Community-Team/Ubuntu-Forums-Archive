---
title: "VM Webcam Problem"
date: 2010-02-01
forum: Multimedia Software
---

### Post by Guerillatactix418 on 2010-02-01
I've been searching this pretty much all day and still have not found anything to resolve my issue.

I am running ubuntu 9.10 and using a SiGma Micro USB Webcam (1c4f:3000) I understand that it is supported with ubuntu. Using Camorama it cannot find the camera, but with cheese I had no problem so I know my cam is working properly and ubuntu sees it there.

I have added the camera to the devices on my (xp) virtual machine and it recognizes that it's there, but it's greyed out so that I cannot click it. anybody have any advice for this issue?

---

### Post by sports.car.guy on 2010-02-01
> **Guerillatactix418 said:**
> I've been searching this pretty much all day and still have not found anything to resolve my issue.

I am running ubuntu 9.10 and using a SiGma Micro USB Webcam (1c4f:3000) I understand that it is supported with ubuntu. Using Camorama it cannot find the camera, but with cheese I had no problem so I know my cam is working properly and ubuntu sees it there.

I have added the camera to the devices on my (xp) virtual machine and it recognizes that it's there, but it's greyed out so that I cannot click it. anybody have any advice for this issue?

It will not work because of how video is rendered in Windows through DirectX and the lack of support for it in the VM's available.

---

