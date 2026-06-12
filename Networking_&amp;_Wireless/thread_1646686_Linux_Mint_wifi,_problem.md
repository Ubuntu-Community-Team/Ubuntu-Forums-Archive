---
title: "Linux Mint wifi, problem"
date: 2010-12-16
forum: Networking &amp; Wireless
---

### Post by xZeKeX on 2010-12-16
HI, i dont speak very well english (sorry). I have a problem with my  notebook Asus and wireless. When i turn on pc without wirelles ON , pc  is normal, when i turn pc with wireless on, my pc freeze and i can not  do anything on my notebook i must restart pc... sometimes when is wifi  off, the pc also freeze without special cause.. 
i have [B]Linux Mint 10 Julia 
- Linux Mint 2.6.35-22-generic-pae #35-Ubuntu SMP Sat Oct 16 22:16:51 UTC 2010 i686 GNU/Linux[/B]

I work on my pc now when i not connected on wirelles the pc freeze too  (sometimes) , always when i turn wifi the pc freeze and i must restart  machine.. Someone helps me? its a problem with driver or some hw or  software? The notebook is new, i installed mint a few days later. 
here is the terminal output - **lspci**:

00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b3)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0b.0 SATA controller: nVidia Corporation MCP79 AHCI Controller (rev b1)
00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
02:00.0 VGA compatible controller: nVidia Corporation GT216 [GeForce GT 320M] (rev a2)
02:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
04:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)


please help

---

### Post by dandnsmith on 2010-12-16
I believe that Mint 10 is based on Ubuntu 10.10, which isn't so far renowned for being very good with this sort of hardware (just have a look at all the threads).

I found that older versions of Mint worked well with my Acer netbook out-of-the-box - so this could be the way to go.

---

### Post by grahammechanical on 2010-12-16
If you go to system>Administration>System Monitor and select the Resources tab you can see how much CPU activity is taking place, and how much memory is being used.

Something is using up your CPU and memory for your system to freeze.

Regards.

---

