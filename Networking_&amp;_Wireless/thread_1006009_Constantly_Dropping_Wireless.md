---
title: "Constantly Dropping Wireless"
date: 2008-12-08
forum: Networking &amp; Wireless
---

### Post by zksmith on 2008-12-08
So after busting my balls just to figure out how to get my wireless working, ubuntu seems to think dropping my wireless every < 2 minutes is a good way of keeping me using this os.

I have an atheros ar938x driver for my Acer Aspire 4730z. I used the ath9k from madwifi to get my wireless working.

Im fairly new to linux but can find my way around, but now im completely stumped. I dont want to go back to windows(so slow, but at least everything worksish...) but will be forced to if the wireless keeps crapping out on me.

All the lspci lshw readouts dont show anything not working...

---

### Post by vivekias on 2008-12-08
> **zksmith said:**
> So after busting my balls just to figure out how to get my wireless working, ubuntu seems to think dropping my wireless every < 2 minutes is a good way of keeping me using this os.

I have an atheros ar938x driver for my Acer Aspire 4730z. I used the ath9k from madwifi to get my wireless working.

Im fairly new to linux but can find my way around, but now im completely stumped. I dont want to go back to windows(so slow, but at least everything worksish...) but will be forced to if the wireless keeps crapping out on me.

All the lspci lshw readouts dont show anything not working...

similar problem i am facing. with me the problem is that if wireless adaptor is put on after the ubuntu is loaded, the system does not recognize it. machine has to be restarted. how does one ensure that ubuntu constantly poll the wireless device

---

### Post by pytheas22 on 2008-12-08
zksmith: did you compile ath9k manually from source?  It's possible that you'd have better luck using madwifi (ath_pci) as opposed to ath9k.  ndiswrapper is a third option.

In any case, if you could please run these commands the next time the connection drops and post the output here, I'll try to help figure out the problem:
```

dmesg | tail -50
lspci -nn
uname -m
ifconfig
iwconfig
lshw -C Network
```

vivekias: your problem is probably actually different from that of the original poster, but if you could please post the output of the following commands while your wireless card is up and running, I'll try to help you make sure it works automatically:
```

lshw -C Network
iwconfig
lsusb
lspci -nn
```

---

