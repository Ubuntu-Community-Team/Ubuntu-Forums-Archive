---
title: "No sund on Netbook"
date: 2010-08-06
forum: Multimedia Software
---

### Post by s0xt3r on 2010-08-06
Hi all, I have just got an ASUS 1005P netbook and want to put Ubuntu on it. The problem is when I load up the Live version I get no sound. I was wondering if this is just an issue with running it live from the USB and will be resolved if I actually install it.

The reason I ask is that I have only just got the netbook and it came with Windows 7, the sound worked in Win7 for about an hour and then just stopped working. I don't want to install Ubuntu if it is an actual fault with the netbook and I have to return it.

The version of Ubuntu I'm trying to use is 10.04, I am running it off of a USB stick that I created with the "USB Startup Disk Creator" tool in Ubuntu 9.04.

Any help would really be appreciated as at the minute I am unable to get any sound out of it either in Windows or Ubuntu and I really don't want to have to return it to Amazon.

Thanks.

---

### Post by lidex on 2010-08-06
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---

