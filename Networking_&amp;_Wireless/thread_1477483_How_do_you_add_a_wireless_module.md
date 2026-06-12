---
title: "How do you add a wireless module"
date: 2010-05-08
forum: Networking &amp; Wireless
---

### Post by rdingraham on 2010-05-08
I have a Toshiba Satellite 505D, and because of ACPI issues I had to compile a custom kernel. (see thread [http://ubuntuforums.org/showthread.php?t=1301101&highlight=l505d](http://ubuntuforums.org/showthread.php?t=1301101&highlight=l505d)) 

Everything works except the wireless is broken.  My network card is a RTL8101E/RTL8102E. The driver is r8169.  The new kernel does not load the wireless driver at boot up.

At the terminal, I typed sudo modprobe r8169 to load the driver.  
Then I typed dmesg | grep -i r8169, and I got back the response 

bob@bob-desktop:~$ lsmod | grep -i r8169
r8169                  39454  0 
mii                     5237  1 r8169

This, I think, tells me the driver is there.

However, when I type iwconfig, I get the response "no wireless connection"

Anyone know how to fix this?

Bob Ingraham

---

### Post by chili555 on 2010-05-08
> However, when I type iwconfig, I get the response "no wireless connection"The RTL8101E/RTL8102E is an ethernet device, not a wireless device.

---

### Post by rdingraham on 2010-05-08
Sorry.  When I type the command lspci -nn at the terminal prompt, at the end of a long list of things, it has two lines which say:

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8172] (rev 10)

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)

Is that the information I need, and if it is, does anyone know how to proceed?

I know this laptop has a wireless device. I used it on Windows 7 before I installed Ubuntu Lucid.

Bob

---

### Post by chili555 on 2010-05-08
This is your wireless device:> Realtek Semiconductor Co., Ltd. Device [10ec:8172] (rev 10)It works with the module r8192se_pci which is built in to the Lucid - 10.04 kernel. I don't know what custom kernel you built, but Lucid runs 2.6.32-xx. Can you bring it to life with:```
sudo modprobe r8192se_pci
```

---

### Post by rdingraham on 2010-05-08
This is what I get:

bob@bob-desktop:~$ sudo modprobe r8192se_pci
[sudo] password for bob: 
FATAL: Module r8192se_pci not found.

I believe if I add the r8192se_pci module, the wireless will work. Do you know how I would go about adding the module?  

The name of the custom kernel is 2.6.32.4-l505d.  Creating the kernel was necessary because many of the new Toshiba laptops, particularly the model L505D, will not boot into Ubuntu unless the kernel is patched to correct the dsdt aspect of the acpi configuration. This is not a problem with Ubuntu; it is a problem in the Toshiba BIOS, and Toshiba does not seem interested in correcting it.

However, the patch that corrected the dsdt problem seems to have removed the wireless module.  If I re-add it, it should work.

Bob

---

### Post by rdingraham on 2010-05-09
A progress report:

I followed the instructions on this page: [URL="http://www.linwik.com/wiki/using+the+realtek+8172+and+8192se+wireless+controller+with+ubuntu+9.10"] to download and install the 8192_se driver, and rebooted.

Still no wireless at boot-up, but now when I type the command sudo modprobe r8192se_pci, I get the following:

bob@bob-desktop:~$ sudo modprobe r8192se-pci
[sudo] password for bob:
bob@bob-desktop:~$ 

After which the wireless is indeed up and running!

How to I make it permanent?

Bob

---

### Post by chili555 on 2010-05-09
> After which the wireless is indeed up and running!Great work!!

In order to get it to load on boot, let's add it to /etc/modules:```
sudo su
echo r8192se_pci >> /etc/modules
exit
```Proofread carefully; all the symbols, case, spelling, etc. are crucial. You should be up and running thereafter.

---

### Post by rdingraham on 2010-05-09
It worked.   A big thanks for your help.

Bob I.

---

