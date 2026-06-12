---
title: "no wireless on Sony Vaio"
date: 2009-04-27
forum: Networking &amp; Wireless
---

### Post by skatebiker on 2009-04-27
After an upgrade to 9.04 it cannot connect to wifi.
I first enabled the networkmanager widget and then saw a list of routers including mine. The I clicked on connect and filled in my key but 'connection failed'.

I restarted the computer, but it didn't help.

I tried tips using wicd and knetworkmanager but it didn't help either.

So I restored my 8.10 backup and everything worked flawlessly.

Then I made a boot CD of 9.04 and booted from that CD to check a clean install.
Same problem, no wifi connection and also not with knetworkmanager (which I installed in the clean version).

In both cases it seems that the driver does work (it shows wifi hotspots) but does not connect.

Any workaround ?

---

### Post by coffeecat on 2009-04-27
Which Sony Vaio model are you using? And before any one can help, you need to post details of the wireless chipset it has. Open a terminal and post the output of:

```
lspci
```

---

### Post by skatebiker on 2009-04-27
> **coffeecat said:**
> Which Sony Vaio model are you using? And before any one can help, you need to post details of the wireless chipset it has. Open a terminal and post the output of:

```
lspci
```

The model is VGN-FZ21M and I did this command yesterday (right now I am not in the opportunity to do this terminal command) and it is an Intel PRO/Wireless 4965 AG(N)
(iwl4965) which is listed in the supported devices list:
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel)

It does work under 8.10 and under 9.04 it lists all wifi hotspots but it cannot connect.

---

