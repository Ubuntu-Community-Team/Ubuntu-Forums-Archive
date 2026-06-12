---
title: "Can't connect to hidden WEP wireless network"
date: 2010-08-23
forum: Networking &amp; Wireless
---

### Post by ubungler on 2010-08-23
Hi there,
I've just been given an old PC and I've installed the latest Ubuntu on it.
I know the wireless network card on it works with Windows, but I can't seem to get it working with.
I clicked on the Network Management icon and followed the "Connect to Hidden Wireless Network" screens, entering my SSID and WEP key, and it thought about that for a while and didn't connect.

I've tried to follow the steps of advice given in other threads but I don't understand the output or what's going on and I'm not making progress.

Anybody able to point me in the right direction?

p.s. Also when it is scanning it doesn't pick up any networks. In Windows it would see my neighbours secured networks.

---

### Post by ubungler on 2010-08-24
As far as I can work out it's using the rt2500pci driver and I believe that this is being loaded correctly.

Any suggestions for what I can try next?

---

### Post by ubungler on 2010-08-24
I tried disabling the WEP on the router and it still can't connect. Is there some sort of test I can run to check that the driver is working properly?

---

### Post by pling on 2010-08-24
I'm pretty sure that your wifi card is not working. You'll probably need to use ndiswrapper to run its windows drivers under linux to get it working. Google this.

Also: it would probably help you get responses if you gave details like what card you were using..

---

