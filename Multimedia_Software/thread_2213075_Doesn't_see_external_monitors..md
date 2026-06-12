---
title: "Doesn't see external monitors."
date: 2014-03-24
forum: Multimedia Software
---

### Post by guice on 2014-03-24
I'm running a Lenovo T530 Laptop with an NVidia 5400 NVS video card. My laptop is connected to a Lenovo docking station with two external monitors connected on the DVI ports. Ubuntu isn't seeing either of them. What can I do to get this working? Here's a couple things I found in discussions people asking for, but nothing seems to work for my case:

```

root@hades:/etc# uname -a
Linux hades 3.11.0-18-generic #32-Ubuntu SMP Tue Feb 18 21:11:14 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
root@hades:/etc# lspci
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:16.3 Serial controller: Intel Corporation 7 Series/C210 Series Chipset Family KT Controller (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation QM77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108M [NVS 5400M] (rev ff)
02:00.0 System peripheral: Ricoh Co Ltd MMC/SD Host Controller (rev 08)
02:00.3 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 PCIe IEEE 1394 Controller (rev 04)
03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] (rev 34)
root@hades:/etc# 

```

I found I _cannot_ use any NVidia drivers due to the Optimus support problems. So, can't go that direction. I've installed the Bumblee software ([from this thread]("http://askubuntu.com/questions/36930/how-well-do-laptops-with-nvidia-optimus-work")) but still doesn't work.

Any other route I can try?

*Edit: After realizing this is a docking station issue, not laptop driver issue, I changed up my search terms and ran across [this thread]("http://ubuntuforums.org/showthread.php?t=1913401"). The general gist is: set to "Discrete Graphics"; install drivers from nVidia.com; restart. All-in-all, it worked. However, it only works on _two_ displays. Any attempt to add a third (laptop itself), fails. It's not a 100% solution, but it's a strong enough resolution that would allow me to work.

*Edit 2: I should add, it's apparently pretty unstable: any attempt to _open_ the laptop results in a complete system stall-out, forcing me to reboot. Ouch.

---

