---
title: "Pavilion dv6 Wireless Issue"
date: 2011-06-11
forum: Networking &amp; Wireless
---

### Post by TromC on 2011-06-11
Hi all, I recently installed Ubuntu 11.04 32bit on my new hp pavilion dv6-6033cl.
For some reason, ubuntu cannot find local wireless networks. In fact, the [s]Broadcom wireless card[/s] **Ralink RT5390 802.11b/g/n** seems to be incompatible with ubuntu. I've tried numerous 'solutions' on the Internet, but none of them seem to work on my computer. [s]Tutorials I've visited have recommended downloading the b43 drivers from the Synaptic package manager and also the bcmwl-kernal-source package. Nevertheless, the wireless never turns on and Additional Drivers never shows anything at all.[/s]
After several exasperating hours of trying to get my wireless running I've decided to turn to the forum for help. I'm sure there's probably more information I should supply, but I'm honestly not sure what that would be. Thanks in advance to anyone who can help!

---

### Post by superduperlinuxperson on 2011-06-11
heres how i got the broadcom driver working (Got this from this website:[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx))

If you do not have any other means of Internet access on your computer, you will have to install b43-fwcutter and patch  packages from the install media. After that you will need to setup  firmware manually (without the firmware automatically downloading and  being set up). 
**Step 1.** 
b43-fwcutter is located on the Ubuntu install media under **../pool/main/b/b43-fwcutter/** and patch is located under **../pool/main/p/patch/** **or** both in the official repositories online.  
Double click on the package to install **or** in a **terminal** (under the desktop menu **Applications > Accessories > Terminal**) navigate to the folder containing the package and issue the following command:  

:/b43-fwcutter/$ sudo dpkg -i b43-fwcutter*
**Step 2.** 
On a computer with Internet access, download the required firmware files from [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o) and [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2) 
**Step 3.**  
Copy  the downloaded files to your home folder and execute the following  commands consecutively in a terminal to extract and install the  firmware: 

~$ tar xfvj broadcom-wl-4.150.10.5.tar.bz2 
~$ sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o 
~$ sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o

still not gone? reboot. still not gone, then your wireless card may not be supported. heres the list website link:
[http://wireless.kernel.org/en/users/Drivers/b43?highlight=%28b43%29#Known_PCI_devices]("http://wireless.kernel.org/en/users/Drivers/b43?highlight=%28b43%29#Known_PCI_devices")

you mit

---

### Post by TromC on 2011-06-13
Well, I tried that and it installed properly. However, I still have no Internet connection. I was trying to set this up with my friend and he told me I had a Broadcom wireless card, but I actually have a Ralink RT5390 802.11b/g/n WiFi Adapter installed. I'm pretty sure that's my wireless card, but I'm not really into this hardware stuff yet so I can't be sure.
[B]
First post updated with this information.


EDIT: 
For any searchers, the following thread fixed my problem.
[http://ubuntuforums.org/showthread.php?t=1743525](http://ubuntuforums.org/showthread.php?t=1743525)[/B]

---

