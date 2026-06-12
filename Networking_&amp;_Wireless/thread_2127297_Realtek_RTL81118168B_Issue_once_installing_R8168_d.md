---
title: "Realtek RTL8111/8168B Issue once installing R8168 driver 12.04 64Bit"
date: 2013-03-19
forum: Networking &amp; Wireless
---

### Post by gatorcc on 2013-03-19
I have installed the R8168 driver to replace the R8169 driver but I still am not able to access my wired network.  

lsmod | grep r81
r8168                 248628  0 

 lspci | grep RTL
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)


Any suggestions.

I installed the driver from Realtek and ran the 
sudo ./autorun.sh

script then I blacklisted the R8169 driver.

Any suggestions on what could be wrong other than a bad NIC?

Phil

---

