---
title: "How to partition disk?"
date: 2012-03-18
forum: Networking &amp; Wireless
---

### Post by jeshrel on 2012-03-18
Hi,I have a 320 GB hard on which i have installed ubuntu 11.10, Kindly help on how to partition my hard disk into several partitions. NOTE: Ubuntu 11.10 is already installed on the hard diskThank you

---

### Post by kazztan0325 on 2012-03-18
You would be able to partition your disk with **'G Parted'**.

1. Boot your PC with _Ubuntu Live CD_.
2. Run **'G Parted**'

As for usage of **'G Parted'**, please refer following site:
**"GParted partitioning software - Full tutorial"**
[http://www.dedoimedo.com/computers/gparted.html]("http://www.dedoimedo.com/computers/gparted.html")

Hope this helps.

---

### Post by ajgreeny on 2012-03-18
Are you asking how the job of partitioning is done, or how to best set up partitions for your Ubuntu installation?

If the former then kazztan0325 has given enough information for the moment.

If you want to know how best to set up partitions for an installation, it is a bit late as you have already installed the OS.  However, it is still possible for you to make a separate /home partition with very little trouble or work on your part.  If you want to know more ask again, and I or many others will try to help you out.

---

### Post by jeshrel on 2012-03-18
> **ajgreeny said:**
> Are you asking how the job of partitioning is done, or how to best set up partitions for your Ubuntu installation?

If the former then kazztan0325 has given enough information for the moment.

If you want to know how best to set up partitions for an installation, it is a bit late as you have already installed the OS.  However, it is still possible for you to make a separate /home partition with very little trouble or work on your part.  If you want to know more ask again, and I or many others will try to help you out.
Eg : After we install windows OS we would partition our hard disk into many drives..i would like to do the same wiht ubuntu..I have already installed ubunut 11.10 and now i would like to partition my hard disk into one or two more drives
How do i do that?

thanks for your response

---

### Post by ajgreeny on 2012-03-18
You will need to boot to a live CD or USB, run gparted and then setup the partitions you want, of the sizes you want, and finally edit /etc/fstb to mount the partitions at boot time.

Tell us more about how you wish to use the partitions; do you want one for music, another for videos, etc, or did you really want a separate /home partition?  Almost anything is possible, we just need to know more about your needs.  We also need to know if this is a dual boot with windows or a dedicated Ubuntu machine.

---

### Post by jeshrel on 2012-03-18
Is ther any other way other than partitioning through live cs or usb?

---

### Post by ajgreeny on 2012-03-18
> **jeshrel said:**
> Is there any other way other than partitioning through live cs or usb?
I don't know of any, as you can not edit a mounted partition and when running your ubuntu OS, the partition is. of course, mounted.  You can not even use a Windows system with any partitioning application for that, as it will probably not even be able to see the current ubuntu partition.

What is the problem with running gparted from a live CD or USB? It is very easy to use.  If you don't already have a live system to run you can download and use gparted live CD/USB which is much smaller to download that a full ubuntu live CD.
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by critin on 2012-04-04
> Is ther any other way other than partitioning through live cs or usb?

It is very easy.  And while there take the time to study and learn about disks and partitions.

---

