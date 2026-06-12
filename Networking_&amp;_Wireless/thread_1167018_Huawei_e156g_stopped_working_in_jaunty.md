---
title: "Huawei e156g stopped working in jaunty"
date: 2009-05-22
forum: Networking &amp; Wireless
---

### Post by Shootfast on 2009-05-22
Hi folks,

I've been using a Huawei E156G with a "three" UK simcard for a few weeks with no problems at all, until yesterday where for no reason at all, I can't make a connection.

I'm using the default settings from Network Manager (which all worked fine) and I have another modem (an e160g which still works) that I've tested the SIM on and it works fine.

dmesg shows nothing perculiar and lsusb shows the dongle fine.
I can't seem to find any logs for Network Manager to help me diagnose any further.

What seems more troubling is that the modem no longer works on any of my other ubuntu boxes either. Perhaps something has been flipped?

(The whole device still works fine in windows)

Any help would be awesome.

Thanks.

---

### Post by Shootfast on 2009-05-22
Gah, seems after whinging about it here, it's decided to start working again.
Still, If anyone knows how to view Network Managers logs, i'd be glad to know where they are.

Cheers,

---

### Post by BUGabundo on 2009-07-31
in the future, if you have trouble with 3G modem please see this:
[https://wiki.ubuntu.com/DebuggingNetworkManager](https://wiki.ubuntu.com/DebuggingNetworkManager)

specially:
[https://wiki.ubuntu.com/DebuggingNetworkManager#Serial%20Log%20%28Mobile%20Broadband%29](https://wiki.ubuntu.com/DebuggingNetworkManager#Serial%20Log%20%28Mobile%20Broadband%29)
and
[https://wiki.ubuntu.com/DebuggingNetworkManager#Debugging%203G%20modems](https://wiki.ubuntu.com/DebuggingNetworkManager#Debugging%203G%20modems)

---

