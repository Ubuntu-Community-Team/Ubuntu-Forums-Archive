---
title: "Road warrior cannot connect to encrypted wireless networks with BCM43 and Ubuntu10.04"
date: 2010-11-10
forum: Networking &amp; Wireless
---

### Post by WhatEver90 on 2010-11-10
I have a frustrating wireless networking problem trying to connect to cafe wireless networks using a BCM4318 under Ubuntu 10.04 (Lucid.)  I don't have a wireless connection/router of my own to test with, which makes this problem difficult to troubleshoot.

I'm using Ubuntu 10.04 and it's fairly new/default.  I think that means I'm using Network Manager for networking because I think that's what comes out of the box, right?

I click the little wireless icon in Gnome's top bar and I see a list of networks, some of which have locks next to them.  When I click on a name without a lock, I usually connect just fine (unencrypted network.)  But since installing 10.04, I have not been able to connect to any networks that are encrypted.  When I click on those, a dialog box pops up that says "Wireless Security" and points to a dropdown with only one option: "WPA & WPA2 Personal," followed by a field for the password.  Is it defaulting to WPA & WPA Personal because of Network Manager settings or is it detecting WPA & WPA2 Personal in the network?

So sometimes I try to set the connection up manually in Network Manager, using a different securit method (ie - WEP, etc.), hoping that that will help.  So far I have not found the right combination on any of the networks I've used.  (And I tried dozens today.)

Unfortunately, this upgrade corresponded to a geographic move so I cannot confirm whether I can connect to networks that I used to be able to connect to, now that I've upgraded to 10.04.  So I can't say whether the problem is that I upgraded or whether it has to do with these new networks using WPA (whereas maybe the old ones in my old town were using WEP?) or whether it's something else.

Here is what I do know:

Wireless Card: Broadcom Corporation BCM4318 [AirForce One 54g]
Driver: Not sure.  FWCutter is involved, as is a Windows driver.
Results of iwlist auth:
wlan0     Authentication capabilities :
        WPA
        WPA2
        CIPHER-TKIP
        CIPHER-CCMP

I will be happy to provide any other information that you think you might be able to use to help me debug this.  I'm hoping this is a known problem either with my wireless card or with 10.04 or with Network Manager and that it has a known solution. :)  Thank you in advance for your time and help.

---

### Post by chili555 on 2010-11-10
> Is it defaulting to WPA & WPA Personal because of Network Manager settings or is it detecting WPA & WPA2 Personal in the network?It is detecting either a WPA Personal network; or a WPA2 Personal network; or a mixed WPA and WPA2 Personal network for which a password is required to connect. If you know the password and supply it in the little box, it will connect. You don't need to figure out or specify what particular version of WPA the network is; Network Manager is supposed to work out all of that for you.

Incidently, many drivers or perhaps wpa_supplicant, have trouble with mixed WPA and WPA2 networks. I recommend you set up your router with WPA2 and skip the mixed mode.> I think that means I'm using Network Manager for networking because I think that's what comes out of the box, right?Right.> Driver: Not sure. FWCutter is involved, as is a Windows driver.The name of the driver that wraps the Windows driver is ndiswrapper. It requires the .inf and .sys files from Windows, usually XP. If NM is able to see networks and you can connect, that part is working as expected.> I have not been able to connect to any networks that are encrypted.And for which you know the double-checked case-sensitive password?

---

### Post by chili555 on 2010-11-11
Oops! You caught old Mr. Chili late at night and hurrying to close for the night. 

ndiswrapper wraps the Windows drivers; that is, the .inf and .sys files. On the other hand, b43-fwcutter downloads the proprietary firmware, extracts it and puts it in the correct spot so the native Linux driver will correctly find it. You have one or the other, not both.

If you used b43-fwcutter, you are using the native driver b43. You can query the computer to find out for sure by asking it what driver modules are loaded and if any of them have b43 or ndis in their names. Open Applications > Accessories > Terminal and do:```
lsmod | grep -e b43 -e ndis
```

It probably doesn't matter much until you are certain that the password is correct. When you know that, then we can look into difficulty connecting with b43, Network Manager and WPA2.

I'm sorry I mis-spoke in the post above.

---

