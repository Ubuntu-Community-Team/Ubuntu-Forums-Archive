---
title: "Broadcom BCM4312/Ubuntu 8.10/Dell Inspiron 1525 wifi not working if SSID hidden"
date: 2008-12-12
forum: Networking &amp; Wireless
---

### Post by retiefdv on 2008-12-12
I have just moved to a new laptop. My previous laptop, with Ubuntu 8.10, worked perfectly on whatever wifi network I used to connect - at home, the office, the guest house where I regularly stay and at a client site where I work. These networks have different security settings, some with visible SSID's and other with hidden SSID's and in all cases the connections worked.

My new laptop is a Dell Inspiron 1525 with a Broadcom BCM4312 wifi card, which is fully supported in Ubuntu 8.10.

After many tests I have now come to the conclusion that my new laptop's wifi card does not work when trying to connect to a wifi network with a hidden SSID. I have now confirmed this fact in tests here at home. I reset my wifi router and set it up with a hidden SSID. After numerous attempts I could not connect with my Dell to the network. I then reconfigured my wifi router with an open SSID and immediately it was possible to connect to the router.

When attempting to connect to a network with a hidden SSID, the following happens: a connection is attempted (icon in panel "spins") and after a while the login screen appears, but the password that was initially entered, appears in a completely changed manner, almost as though it was encrypted. Attempts at retyping the password and retrying the connection does not work. In all these cases the security protocol was "WPA and WPA2 personal".

How can I solve this problem? It really seems to be specific to the Broadcom card and it's driver, since my previous laptop, with the same version of Ubuntu, worked perfectly. I would prefer to keep my SSID hidden and there are networks at client sites with hidden SSID's that I need to use.

---

### Post by Ayuthia on 2008-12-12
I want to say that it is a known bug, but I don't recall if has been reported in launcpad.net.  You might want to report it so that it can be looked at.

You might need to use ndiswrapper if you need to connect to a hidden site with WPA.  Here is a link that might help:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

You might also try wicd to see if it is an issue with network manager.

---

### Post by retiefdv on 2008-12-13
This has now been reported on launchpad as follows:

[https://bugs.launchpad.net/ubuntu/+bug/307637](https://bugs.launchpad.net/ubuntu/+bug/307637)

---

### Post by Fijitotev on 2009-06-18
Maybe this can help:

[https://bugs.launchpad.net/ubuntu/+source/wireless-crda/+bug/336915](https://bugs.launchpad.net/ubuntu/+source/wireless-crda/+bug/336915)

It Fixed the problem on 9.04 for me

---

### Post by arch0njw on 2009-06-19
Holy sweet mercy.  I spent a couple hours wondering WTF was going wrong and the whole time the problem was simply that my SSID is hidden.  That sucks.  I try not to pitch fits over bugs, but this one is pretty annoying.  I don't want a solution which effectively amounts to sharing my SSID with my neighbors so they can have a target to shoot at if they want to get bored and hack.

I'll probably get clobbered for this, but I just "me too"'d the bug.

Kubuntu 9.04, 32bit, Broadcom Corporation BCM4306 802.11b/g (rev 02).


I'll admit I'm using a dated laptop, but that's no excuse since it doesn't appear that the problem is the cruddy bcm driver anyway, but failure to test hidden SSIDs.  DOH!  ... and GRR!!!

---

### Post by chenxiaolong on 2009-12-22
Use AES encryption instead of TKIP. Also, select only WPA or WPA2, not a combination of both (if your router supports it). WEP always works.

---

