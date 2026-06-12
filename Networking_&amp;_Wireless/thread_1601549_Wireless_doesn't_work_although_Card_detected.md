---
title: "Wireless doesn't work although Card detected"
date: 2010-10-20
forum: Networking &amp; Wireless
---

### Post by dtkr on 2010-10-20
Hi,

I have an issue with wireless connectivity on my laptop. Its a HP dm3 and the intel network adapter is supported as I can scan and detect wireless access points.

However, when I attempt to connect to my home network, it fails and this is probably a result of two things: The BSSID is missing and/or the DHCP client ID is missing.

I am running Kubuntu 10.10 32 bit

Can anyone explain how I can obtain them?

Thanks.

---

### Post by dtkr on 2010-10-20
And the funniest thing is that when I use Ubuntu on the same machine, there's not a single query over the network connection and everything works. 

Anyway, here's lspci:

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Device 0a69 (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)


On Kubuntu, the configuration is more difficult and confusing. Can anyone help out? Thanks.

---

### Post by dtkr on 2010-10-20
Update: I've also realized that when running Ubuntu, although no MAC/BSSID and DHCP Client ID Information is being set, the connection still works smoothly using the "automatic" options while on Kubuntu, Knetworkmanager keeps popping out with a dialog box regarding my network connection (WEP settings, password, DHCP ID Field, BSSID Field) without any information whatsoever of what is wrong.

---

