---
title: "Intel Link 5100AGN problem"
date: 2009-11-29
forum: Networking &amp; Wireless
---

### Post by ancientrustic on 2009-11-29
I have just bought a new Toshiba Satellite P500. I cannot connect to my router either wired or wireless. I have searched the forums but have found nothing that will work. iwlwifi-5000-ucode-2 seems to be in the right folder but no connection is found. The temporary solution has been to use an old Belkin adapter, which works fine, but I would rather have the internal devices working. Can anyone help?
:confused:

---

### Post by ancientrustic on 2009-12-01
A bit more information. I am using Karmic 64 bit, but using a live cd no network was found with Jaunty, Fedora 12 and Open Suse. Is this a new chip for which there is no open source driver yet? I really am getting desperate. Is there noone out there who can help?
Toshiba Satellite P500D.

Please Help.

---

### Post by teward on 2009-12-01
/i'mAnIdiotForIDidn'tReadTheTitle:P

Anyways, you shouldn't be having any problems with the Intel wifi card.  I know that Intel wifi cards (which the Intel Link 5100AGN is) haven't had problems with Ubuntu.

On another note, can you go into your terminal, and run the command ```
lspci
``` and post the output here?  I want to see what ethernet card you have.

---

### Post by ancientrustic on 2009-12-02
Thanks for your response. Here is the output from lspci;

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Device 0a28 (rev a2)
01:00.1 Audio device: nVidia Corporation Device 0be2 (rev a1)
06:00.0 FireWire (IEEE 1394): O2 Micro, Inc. Device 10f7 (rev 01)
06:00.1 SD Host controller: O2 Micro, Inc. Device 8120 (rev 01)
06:00.2 Mass storage controller: O2 Micro, Inc. Device 8130 (rev 01)
07:00.0 Ethernet controller: Attansic Technology Corp. Device 1063 (rev c0)
08:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)

---

### Post by ancientrustic on 2009-12-03
Here is what I get with ifconfig.

ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:43 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4320 (4.3 KB)  TX bytes:4320 (4.3 KB)

---

### Post by coffeecat on 2009-12-03
Why did you think your laptop has an Intel 5100 wireless chipset, when you seem to have a Realtek one?

> **ancientrustic said:**
> 08:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)

Perhaps if you edited your thread title to include Realtek, someone with Realtek experience would notice and be able to help.

I can't offer much except posts #26 and #27 from this thread:

[http://ubuntuforums.org/showthread.php?t=1182457&page=3](http://ubuntuforums.org/showthread.php?t=1182457&page=3)

Although the thread started as a 9.04 one, that poster seems to have got the Realtek 8172 working in Karmic with information in the thread.

---

### Post by ancientrustic on 2009-12-04
Thanks for that. I must be blind. I downloaded the spec sheet from the Toshiba website and believed it. I've tried the solution in your link. I can now see my network but cannot connect to it. I will keep trying. Many thanks fot your help;

---

