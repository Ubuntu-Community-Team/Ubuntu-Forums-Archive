---
title: "Wireless does not connect after suspend/resume"
date: 2011-10-14
forum: Networking &amp; Wireless
---

### Post by prarobo on 2011-10-14
Hey,

I upgraded yesterday to Ubuntu 11.10 . From then on, when I suspend and resume my laptop, wireless manager does not connect to any network. It asks me for the network password again. Even when I enter the password, it doesn't connect till I reboot my system.

If you need me to run something on terminal to get more information about the issue, kindly say so.
 
Kindly help.:(

---

### Post by peepingtom on 2011-10-15
Please post the output of lscpi, we need to know what kind of wireless adapter you have. Does wireless function after resuming when using an Ubuntu 11.10 LiveCD?

---

### Post by prarobo on 2011-10-19
The lspci output

[HTML]00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc NI Seymour [AMD Radeon HD 6470M]
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
0d:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
13:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)
19:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
[/HTML]

I am not using a live CD. Its a full install of 11.10

I found similiar issues in links:

[HTML]http://askubuntu.com/questions/35592/no-wireless-after-resuming-from-suspend
http://askubuntu.com/questions/61795/wireless-does-not-connect-after-suspend-on-thinkpad-t61[/HTML]

I tried the fixes there but none of them worked.

---

