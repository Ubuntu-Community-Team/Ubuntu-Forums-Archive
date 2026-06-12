---
title: "Bluetooth/Wireless combo: Wireless working, bluetooth does not"
date: 2012-03-01
forum: Networking &amp; Wireless
---

### Post by veroslav on 2012-03-01
Hi,

I bought a new Dell Laptop (Inspiron N7110) and it comes with some weird wireless/bluetooth combo. The wireless card is working and I
am able to connect to the Internet. Bluetooth, however, is not. I am running Ubuntu 11.10 (64-bit). The wireless card is the following:

```
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Dell Device [1028:0205]
    Kernel driver in use: ath9k
```
	
What is weird is that when I checked out the state of the Bluetooth connection (by clicking on the bluetooth-applet in the panel), it said
that it was disabled, but even though, I could still select "Disable bluetooth" option from the same applet!

I selected this option just because I was curious, and instantly, my wirelss was disabled instead! I tried to enable it again from the
network manager, but the option was greyed out saying that "The wireless is disabled by a hardware switch" or something similar.

I tried disabling/enabling the networking but nothing helped. All of the bluetooth enabling/disabling options were gone too, so I could do
nothing. I restarted the computer and the problem still persisted.

Then I booted into the Windows 7 partition and the wireless was disabled there as well, however, Windows offered me an option to enable it
again, so I did, and the connection was up and running again. Rebooting back into Ubuntu afterwards, resulted in the wireless being
active and up again there as well. Bluetooth is still disabled though.

My questions are:

1. How can I enable bluetooth without affecting the wireless?
2. Is there a way I can re-enable wireless from Ubuntu after it has been disabled by a hardware switch, in case Windows is unavailable for
some reason?

Thank you!

---

### Post by veroslav on 2012-03-02
bump

---

### Post by veroslav on 2012-03-02
Managed to solve it by installing [ar3011-dkms_1.1ryu2.3_all.deb]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/714862/+attachment/1913129/+files/ar3011-dkms_1.1ryu2.3_all.deb") that I found from this bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/714862](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/714862)

---

