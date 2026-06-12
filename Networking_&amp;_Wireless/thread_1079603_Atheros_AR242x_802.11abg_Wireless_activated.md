---
title: "Atheros AR242x 802.11abg Wireless activated?"
date: 2009-02-24
forum: Networking &amp; Wireless
---

### Post by Colo2 on 2009-02-24
Hey,
I booted Ubuntu 8.10 from LiveCD. This is a laptop and I have Atheros AR242x 802.11abg Wireless adapter on it

The network image at the top right of the ubuntu desktop (two black monitors one infront of the other) had a orange sign with an exclamation sign on it. I clicked it and It said the following:

__________________________
Wired Network (Greyed out)
() Auto eth0
__________________________
VPN Connections  >
__________________________

So the wireless isn't being detected?? Upon going into the hardware driver managment, I discover:
__________________________________________________
__________________________________________________
"Support for Atheros 802.11 wireless LAN cards.
__________________________________________________
__________________________________________________
Support for Atheros 802.11 wireless LAN cards.
Tested by the Ubuntu developers
Licence: free
This driver is activated and currently in use.
__________________________________________________
__________________________________________________

Please help me fix this so I can go online :) thanks
Tom

---

### Post by binbash on 2009-02-24
[http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/)

---

### Post by Reiger on 2009-02-24
> Install linux-backports-modules-intrepid. This works but you would have to reload the driver every time you log on.
Pay particular notice: all this means is that he didn't (know to) add the line aht5k to /etc/modules. You can do this as follows:
```

echo "ath5k" | sudo tee -a /etc/modules

```
From now on, every time you reboot the kernel should automatically load the ath5k driver, which means that the card should upon reboot "just work". (May I add, that this particular model, AR5007EG is a very good "just works" card (long range, healthy signals).)

---

### Post by Colo2 on 2009-02-24
Thank you all for the help :) I will check this out! :)

---

