---
title: "Wireless not working on Dell Inspiron Mini... :("
date: 2012-07-27
forum: Networking &amp; Wireless
---

### Post by seymar on 2012-07-27
Hi,
   I'm a rather new Ubuntu user (actually I have always had somebody fixing my Linux issues for me). After spending all the afternoon reading post about Wireless not working in Ubuntu 10.04 on Dell Mini1018, I'm pretty close to give up.

I guess you all know the issue: whenever I update, my wireless doesn't work anymore. I fixed it once with:

                                  sudo apt-get update
 sudo apt-get --reinstall install bcmwl-kernel-source
 cd Realtek/r8101-1.021.00  
  sudo -E make clean modules
 sudo make install
 sudo depmod -a
 blacklist r8169
                                     sudo update-initramfs -u
  lspci -vvnn
 sudo apt-get install b43-fwcutter firmware-b43-installer
 sudo apt-get update


I updated yesterday and this method doesn't work anymore. In particular when I type


blacklist r8169


i get an error message:
blacklist command not found


....and I couldn't help to fix it.


I tried also as described in 

[http://ubuntuforums.org/showthread.php?t=1721705](http://ubuntuforums.org/showthread.php?t=1721705)
but still it doesn't work.


I tried to reboot several times, being plugged or unplugged, but nothing worked.


This is the output of: lspci -nnk | grep -iA2 net

05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Kernel driver in use: r8101
    Kernel modules: r8101, r8169
07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8176] (rev 01)
    Kernel modules: r8192ce_pci


and when I look at Hardware Drivers, it shows 

"Linux driver for Realtek RT819x WiFi Card"
The driver is activated but not in use


If I well understood I do have the wrong driver, but I don't know how to convince my laptop to get the right one


Sorry if this issue has already been solved, I feel very dummy, but....


Thank you for your help
Paola

---

### Post by seymar on 2012-07-27
Hi,
   I think I solved the problem just going to synaptic and reinstalling rtl8. I rebooted (unplugged! and with eth0 disconnected) and the wireless worked.
I don't know how/why....but it works!
Thanks
Paola

---

