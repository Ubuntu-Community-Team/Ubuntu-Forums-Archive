---
title: "Netgear N600 USB Adapter Drivers"
date: 2012-12-15
forum: Networking &amp; Wireless
---

### Post by Joon Lee on 2012-12-15
Broadcom chipset bcm4323
Personally, I use Lubuntu 12.10, but I have installed Zorin on my father's computer (from XP to Ubuntu to Zorin). Since the Zorin comp is in the basement, there is no internet connection for now. I transferred the correct .inf file to the Zorin comp after downloading them from the Lubuntu comp, from which I am typing this post now. Zorin has this thing for installing Windows Drivers, but it won't install the .inf file because "ndiswrapper module is not found." Solutions?

---

### Post by Joon Lee on 2012-12-15
SOLVED! I found all the dependencies (.deb) from pkgs.org and transferred them over via flashdrive to the Zorin computer and installed the debs. I was then able to install ndiswrapper-dkms (deb, also from pkgs.org) and, thus, the .inf for the usb adapter. The only problem now is that, although the adapter finds available networks, the authentication process seems to be problematic.

In the end, to any other people with this issue, the first giant step to getting your Netgear N600 USB Adapter working is installing the drivers. Ask me to link you to the drivers if you want them. The dependencies can be downloaded from pkgs.org.

---

### Post by Joon Lee on 2012-12-17
Download from Post #24:
[http://ubuntuforums.org/showthread.php?t=1695036&highlight=bcmwlhigh5&page=3](http://ubuntuforums.org/showthread.php?t=1695036&highlight=bcmwlhigh5&page=3)

If you can't install the .inf files because you need ndiswrapper, do the following:
1) Go to pkgs.org
2) Search and download the following: binutils, dkms, fakeroot, gcc, gcc-4.6, libc-dev-bin, libc6-dev, libgomp1, libquadmath0, linux-libc-dev, make, manpages-dev
3) Some of these packages are dependent on another on the list above, so simply install them in the correct order by using a package manager such as Synaptic Package Manager
(Note: If you are using Zorin 6.1 remember it is based on Ubuntu 12.04. When downloading the packages, it will give you a list of files for their respective operating systems. Choose the correct files for YOUR OS. Ensure you are downloading the latest version of the package.)

Now, you may not have needed such a thorough explanation, but I guess it's ok to be too careful here.

---

