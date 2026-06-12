---
title: "Network Manager not connecting to Wireless Network after upgrade from 9.04 to 9.10"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by rvbhute on 2009-11-01
Hi all,

I upgraded my Ubuntu from 9.04 to 9.10 and am having trouble connecting to my Wi-Fi network. *This used to work perfectly in 9.04*, so there is no doubt that the hardware is supported, encryption is supported, passwords are correct, etc.

My wi-fi card (it is using restricted drivers):
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

The router is Linksys WRH54G using stock firmware.

**Issue number 1** (which I noticed first): Network manager is not 'remembering' WPA2 passwords. 

In 9.04, I used to do the following:
1. Click on the NM applet, select 'Connect to hidden wireless network'.
2. From the drop-down, select the pre-configured network. Click 'Connect' and it got done.

But now, the password is empty and the connect button is grayed out. I can see that the password is stored correctly using Sea Horse application.

Issue number 2: NM cannot connect to even un-secure networks. I turned off the encryption and tried connecting. The applet changed to the rotating throbber to indicate that it is trying to connect but nothing further happens. Left-clicking on the applet reveals the network name to be in bold, as if it is connected to, but is not actually.

WICD has the same issue - cannot connect to wireless network. I did not spend much time with WICD as NM is more convenient - for now, it is at least connecting to my wired LAN and USB CDMA internet modem.

Please let me know how I go about debugging this.

Thanks.

---

### Post by Keeper of the Keys on 2009-11-03
I don't know about issue 2 but issue 1 is a known issue mentioned in several bug reports.

Honestly I don't understand how 9.10 was shipped with said bug, it's a bug that faces regular users and would be called Release Critical by most people...

[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/446394](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/446394)

A potential fix is offered here:
[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/449287](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/449287)

---

