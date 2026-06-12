---
title: "Poor wireless connection to my Belkin routerI'm not really certain whether this is ha"
date: 2012-11-11
forum: Networking &amp; Wireless
---

### Post by ChunkyDrew on 2012-11-11
I'm not really certain whether this is hardware-related or a software  change I need to make. When I use my Belkin 802.11N router in Windows,  along with my provider, I have a VERY FAST connection, which almost  never drops.  When I use the same router on my desktop PC with Ubuntu  12.04 & a direct ethernet connection, same thing. 

However, when I connect wirelessly from my Dell laptop in Ubuntu 12.04  to the same router, my connection is very spotty. The connection drops  frequently from 54Mbps to 1Mbps, and often drops entirely.
Any suggestions on what's causing my problem?  [IMG]https://lqo-thequestionsnetw.netdna-ssl.com/questions/images/smilies/confused.gif[/IMG]

---

### Post by gordintoronto on 2012-11-11
It's probably an issue with the wireless adapter in your laptop, or (more likely) its driver.

What wireless adaper? If you open Terminal, and enter the command lspci, you should get about a dozen lines of output. One of them should contain "802.11", and that's your wireless adapter. If you could post the entire line here it might help. If the line contains a "version," that's extremely important, because most of the big manufacturers have a "component du jour" policy. In other words, someone who bought the same laptop a month earlier, might have a completely different wireless adapter.

There's a remote possibility that your problem would be solved by setting the router to a different channel, but that's a 1 in 50 solution.

If you connect the laptop to your router by Ethernet cable and run "Additional Drivers," it might offer you a better driver.

---

### Post by ChunkyDrew on 2012-11-12
Thanks for your suggestions. I could not find any reference to 802.11 in my *lspci *output, unless I overlooked it. How else might it be listed? As for your 2nd suggestion about looking for additional drivers, I will do that as soon as I get home & am near my router. Right now, I am using my Verizon MiFi hotspot, which has no issues.


[INDENT]> 00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09T
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1c.7 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 8 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
09:00.0 Network controller: Intel Corporation Centrino Wireless-N 1030 (rev 34)
0b:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)[/INDENT]

---

### Post by ChunkyDrew on 2012-11-12
After further reflection, I figured out that the 802.11 info is missing from ***lspci*** now because I'm not currently connected to my router. I'll try again when I get home.

---

### Post by gordintoronto on 2012-11-12
It's this one:
09:00.0 Network controller: Intel Corporation Centrino Wireless-N 1030 (rev 34)

I've never seen that, where the "802.11" was not included in lspci output.

You might have a look at:
[http://ubuntuforums.org/showthread.php?t=1892428](http://ubuntuforums.org/showthread.php?t=1892428)

It mentions that, apparently, you can only turn the wireless on and off in Windows. Also suggests a driver to blacklist. Ten to one, that will solve your problem.

---

### Post by ChunkyDrew on 2012-11-13
I no clue why, but that seemed to work. My connection speed tripled immediately, and I have not dropped my connection since performing the suggested edit. I really have a lot to learn about linux, after years of being a Windows expert. Thanks much.
:)

---

