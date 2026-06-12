---
title: "Disk Utility on Live CDs (SMART question)"
date: 2010-09-29
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Martey on 2010-09-29
I am not sure if I should be posting here, or in the Development CD Image forum. In both Maverick and Lucid, I have noticed a bug that only seems to affect the LiveCD. Basically, on every computer that I own that has a spinning hard drive, Gnome Disk Utility and other libatasmart based programs do not probably detect the SMART data when running off of the LiveCD. If you download and install smartmontools, it works fine.

The Launchpad bug is [https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/580112](https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/580112) , but it has not received very much attention. Is there something simple that would cause this not to work?

---

### Post by cariboo on 2010-09-29
I don't have a Maverick Live usb handy, but smart works with a Lucid Live USB.

---

### Post by Martey on 2010-09-30
Unfortunately, it only seems to affect certain computers. The original bug report is for a ThinkPad T60. I have seen it on my ThinkPad T500. I hesitate to say that it is a "ThinkPad only issue", because I believe that the original bug reporters has seen it on other models.

It's super-weird, because it only happens on the LiveCD, and only with Ubuntu (I tried with Fedora, and could not replicate it). I was hoping that someone might know if something about the LiveCD's architecture changed or something.

---

