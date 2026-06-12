---
title: "Wired network unclaimed after upgrade to 9.04"
date: 2009-10-25
forum: Networking &amp; Wireless
---

### Post by Myth123 on 2009-10-25
Hi,
    I have upgraded my ubuntu server from 8.10 to 9.04.
My network was working fine previously. But now its not working at all.
Following is the output of **lshw -C network **

  *-network UNCLAIMED
       description: Ethernet controller
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list
       configuration: latency=0

---

### Post by Myth123 on 2009-10-25
I have solved the problem.
I have downloaded the drivers for RTL8101e pci express and installed it.
Also I have updated the linux-headers which were of previous version.

---

### Post by RainKing44 on 2009-10-25
I'm having a similar [problem]("http://ubuntuforums.org/showthread.php?p=8160587#post8160587"), where my network now says unclaimed. 

I am trying to install linux headers using

sudo apt-get install linux-headers-$(uname -r).


The problem is that I don't know which version I need. How do I figure this out?

---

### Post by Myth123 on 2009-10-25
> **RainKing44 said:**
> 
sudo apt-get install linux-headers-$(uname -r).


This command takes care of the version. Your linux headers version should be same as your kernel version. 
uname -r finds the version of the kernel.

---

