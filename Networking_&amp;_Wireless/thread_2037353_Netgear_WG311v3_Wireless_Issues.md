---
title: "Netgear WG311v3 Wireless Issues"
date: 2012-08-04
forum: Networking &amp; Wireless
---

### Post by Worfthing on 2012-08-04
Hi all,

I recently downloaded Lubuntu and have been trying to get it to recognize my wireless card. I have used [https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3) and everything seems to be working well until I get to the "sudo modprobe ndiswrapper" command. Like the article suggested, I have rebooted, but to no avail. I will receive the error message "FATAL: Module ndiswrapper not found."

However, immediately after telling me that ndiswrapper wasn't found, I can run "ndiswrapper -h" and get all of the options, and even go so far as to run the complete "ndiswrapper -a" command and am informed that "Driver 'wg311v3' is already used for '11AB:1FAA'".

I am at a complete loss. The computer I am using Lubuntu on has no wired connection, but I can download files onto this computer and transfer.

Any help would be appreciated, thanks.

---

### Post by praseodym on 2012-08-04
You also need the packages "ndiswrapper-dkms", "dkms", "build-essential", and the kernel headers. Check the CD for them first

---

### Post by ajgreeny on 2012-08-04
There is a problem with the repository versions of ndiswrapper in Lubuntu 12.04 which means you will need to install **ndiswrapper-source** package and **ndiswrapper-dkms** plus **build-essentials** and compile and install it properly.  Annoying but well documented.

 > If you install the ndiswrapper-common and ndiswrapper-utils-1.9  packages they should install the ndiswrapper module on your system for  all kernels.  But apparently that is not happening in some cases.
So build the module manually from source using Ubuntu's  version of the source code, which should compile without issue.  To do  that, first use a cable connection or boot into a kernel where you have Internet access and  install the packages you will need:```
sudo apt-get install ndiswrapper-source ndiswrapper-dkms build-essential
```Then boot into the 3.2 kernel and try compiling ndiswrapper there using the dkms service:```
sudo dkms build -m ndiswrapper -v 1.57
sudo dkms install -m ndiswrapper -v 1.57 
```If you run into errors from any of these commands, please post all  output.  Otherwise, when they are done, try loading the ndiswrapper  module with:
     ```
sudo modprobe ndiswrapper 
```See also
[https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/986064](https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/986064)
[http://ubuntuforums.org/showthread.php?t=1967383](http://ubuntuforums.org/showthread.php?t=1967383)
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Good luck!  It does work; I know because I had to do it as well.

---

### Post by gordintoronto on 2012-08-04
I could be wrong, but I think that wireless adapter is supported "out of the box" in the current Linux kernel.

Do you understand how to set up a wireless connection in Lubuntu, with supported hardware?

---

