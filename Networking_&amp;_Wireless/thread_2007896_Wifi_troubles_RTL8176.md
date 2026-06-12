---
title: "Wifi troubles RTL8176"
date: 2012-06-21
forum: Networking &amp; Wireless
---

### Post by danielbrackett on 2012-06-21
Hi, 

I would like some help. I got my wireless working for kernel 2.6.32-37 with the RTL8192CE driver but it will not work for the kernel >= 2.6.32-38. I am currently running on kernel 2.6.32-41. 

I put this on the terminal; [I]lspci -nnk | grep -iA2 net

[/I]and got this back;
using sysinfo I got the subsystems

[I]03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8176] (rev 01)
    Kernel modules: rtl8192ce
[/I]Subsystem: Hewlett-Parkard Comany Device 1629
[I]07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Kernel driver in use: r8169
    Kernel modules: r8169
[/I]Subsystem: Hewlett-Parkard Company Device 165e

I am thinking that I should try to install the rtl8176 driver or the rtl8101e driver ??? Which one ???

---

### Post by rukiaEnix on 2012-06-21
rtl8101e

---

### Post by chili555 on 2012-06-21
As much as I respect my colleague, 8101E is for ethernet. It's won't help your wireless at all.

---

### Post by rukiaEnix on 2012-06-21
Sorry I didn't put enough attention to your output, I didn't read the model of your wireless just of the ethernet, sorry.

---

### Post by chili555 on 2012-06-21
So, daniel, you know what you need to do. Do you need additional guidance? Please post back if we can help.

---

### Post by danielbrackett on 2012-06-21
OK so I want to download and install the rtl8176? yes? 
I am on the Realtek site but I am not sure where to go from the downloads section.
[http://152.104.125.41/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=21&Level=4&Conn=3](http://152.104.125.41/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=21&Level=4&Conn=3)

How am I supposed to tell the difference?

---

### Post by chili555 on 2012-06-21
> 03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8176] (rev 01)
Kernel modules: [COLOR="Red"]rtl8192ce[/COLOR]Please check here:  [http://152.104.125.41/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://152.104.125.41/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

You need the RTL8188CE version for kernel versions 2.6.24 and later. Also make sure you have kernel headers and build-essential installed before you proceed.

---

