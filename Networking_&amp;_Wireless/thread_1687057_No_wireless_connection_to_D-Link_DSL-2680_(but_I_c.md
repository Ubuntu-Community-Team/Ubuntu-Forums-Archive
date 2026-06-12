---
title: "No wireless connection to D-Link DSL-2680 (but I could connect once!)"
date: 2011-02-13
forum: Networking &amp; Wireless
---

### Post by Jooles on 2011-02-13
Hi there,

I've just received a new router from TalkTalk - a  D-Link DSL-2680 - and was very pleased to find that after I plugged it  in I could wirelessly connect straight away with my laptop.  However  since I first disconnected I have been unable to connect again since and  have had to resort to a wired connection.

I have been using  Ubuntu for several years now and am very pleased with it, especially  given my relatively low knowledge of computers.

Can anyone help?

My system is as follows:

[LIST]
[*]IBM T42 laptop
[*]Ubuntu 10.10 - I was running V9, but upgraded as some discussions suggested this might be an issue
[*]The wireless adapter is built in to the laptop, and I'm not even sure how to find out what it is
[/LIST]
It  may be a problem with the DHCP server on the router rather than a  problem with the laptop, however I would appreciate any troubleshooting  help.

Thanks

---

### Post by chili555 on 2011-02-13
> The wireless adapter is built in to the laptop, and I'm not even sure how to find out what it isLet's start there. Please open Applications > Accessories > Terminal and run and post:```
lspci -nn
```One line will reference wireless or 802.11 or ABG. Post all of that line and we'll proceed.

---

### Post by Jooles on 2011-02-13
Hi there,

thanks for the reply.  this gives

02:02.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)


Jooles

---

### Post by Jooles on 2011-02-13
Bit more info....

I can still see the wireless network, but when I try to attach the icon just spins round and after a while it asks for the password again.  I have typed the password in correctly and tried it without any encryption, so i'm pretty sure it's not that; and anyway, like i said at the start, I managed to connect once!

Thanks for all the help
Jooles

---

### Post by chili555 on 2011-02-13
Let's see if there are any informative messages about this; please post:```
dmesg | grep -e ipw -e eth
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

---

### Post by Jooles on 2011-02-13
OK here it is - sorry I took so long to get back the first time round. Parents in law arrived!!

[    1.514299] e1000 0000:02:01.0: eth0: (PCI:33MHz:32-bit) 00:15:58:09:04:69
[    1.514308] e1000 0000:02:01.0: eth0: Intel(R) PRO/1000 Network Connection
[   37.628827] libipw: 802.11 data/management/control stack, git-1.1.13
[   37.628832] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   37.706264] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   37.706271] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   38.084705] ipw2200 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[   38.109014] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   38.601408] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
[   38.707520] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   38.708445] e1000: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   38.708819] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   49.032029] eth1: no IPv6 routers present
[   49.096025] eth0: no IPv6 routers present

---

### Post by chili555 on 2011-02-13
> eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TXThis suggests that the ethernet cable is attached and you have an internet connection. Network Manager is designed to *disallow* a wireless connection if you have wired ethernet. Please reboot with the ethernet detached and let me know the result when you click the Network Manager icon.

---

### Post by Jooles on 2011-02-13
Thanks again - here's the output after rebooting with the cable unplugged though (obviously) it's now back in again.

[    1.502282] e1000 0000:02:01.0: eth0: (PCI:33MHz:32-bit) 00:15:58:09:04:69
[    1.502291] e1000 0000:02:01.0: eth0: Intel(R) PRO/1000 Network Connection
[   30.760577] libipw: 802.11 data/management/control stack, git-1.1.13
[   30.760582] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   30.832734] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   30.832739] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   31.126339] ipw2200 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[   31.130309] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   31.546219] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
[   31.731712] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   42.704030] eth1: no IPv6 routers present

---

### Post by Jooles on 2011-02-13
OK - thanks for all your help anyway.  I've just been onto the talktalk guys and they seemed to have fixed it.  though I had to lie and pretend I was using a windows laptop...!

---

### Post by doubi on 2011-09-19
Hi Jooles,

I appear to be experiencing problems with the DSL-2680 too. They're annoyingly intermittent - as in, when I call Talktalk, the problem can fix itself by simply entering the wireless key again :s

I'd be very interested to hear how exactly you were helped to solve your issue. Was it with your laptop hardware? Ubuntu? The DSL-2680? The broadband service itself?

Thanks!

---

