---
title: "Ubuntu Studio 8.10 wireless linksys problem"
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by Petecoi on 2008-12-20
Hello,

I am brand new to linux and have installed Ubuntu studio on a pc in my garage to act as a music studio. I am trying this as I am a Headteacher/Principle and would love to use this programme throughout my school.

However, the install does not recognise my Linksys G USB device. WUSB54GR. I have looked on the forum and downloaded the following on my main machine using XP. 

2008_0506_RT73_Linux_STA_Drv1.1.0.1.tar.bz2

However, I just don't understand how to use this. I have copied it to a USB stick and can get it onto the Ubuntu machine. I try to open it but all that comes up is text.

I hope to get it working as I love the principle of Linux and Ubuntu Studio looks great but with upgrades only available online I need to get this working. Obviously, unless I can get the whole thing running it will be difficult to persuade the school to give over windows machines to linux.

Lots of very simple step by step help needed.

Thanks.

Pete

---

### Post by Ayuthia on 2008-12-20
> **Petecoi said:**
> Hello,

I am brand new to linux and have installed Ubuntu studio on a pc in my garage to act as a music studio. I am trying this as I am a Headteacher/Principle and would love to use this programme throughout my school.

However, the install does not recognise my Linksys G USB device. WUSB54GR. I have looked on the forum and downloaded the following on my main machine using XP. 

2008_0506_RT73_Linux_STA_Drv1.1.0.1.tar.bz2

However, I just don't understand how to use this. I have copied it to a USB stick and can get it onto the Ubuntu machine. I try to open it but all that comes up is text.

I hope to get it working as I love the principle of Linux and Ubuntu Studio looks great but with upgrades only available online I need to get this working. Obviously, unless I can get the whole thing running it will be difficult to persuade the school to give over windows machines to linux.

Lots of very simple step by step help needed.

Thanks.

Pete

You can try the following:
```
sudo modprobe rt73usb
sudo /etc/init.d/networking restart
```
If it does not work, please post the results of:
```
lsusb
```
If it does work, please add the following:
```
echo rt73usb|sudo tee -a /etc/modules
```and that will add it to the list of modules to load at boot.

---

### Post by Petecoi on 2008-12-22
Thank you for this.

I openned up a terminal and carried out the above. The wireless device is still not seen.
1susb gives the reply command not found.

I think I am less capable than you think with linux.

I tried to unpack (?) the tar information above and follow the instructions. However, the system just tells me I don't have permission to carry out any of the operations described in the readme.

---

### Post by Brigham on 2008-12-30
Glad to see that you're experimenting with linux.  For a school, no less!

I don't know how to solve this problem, but you mistyped the command "lsusb".  This command is comprised of all letters (lowercase L-S-U-S-B).  It does get a bit confusing with the number "1" and the lowercase letter "l" on a computer screen.  

Welcome to the Linux community, by the way.  Wireless always seems to be a bit tricky, especially USB wireless devices.  I can install the same OS and get different results regarding wireless connectivity.  I wish I could explain it.

---

