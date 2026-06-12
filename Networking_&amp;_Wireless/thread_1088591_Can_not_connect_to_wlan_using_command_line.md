---
title: "Can not connect to wlan using command line"
date: 2009-03-06
forum: Networking &amp; Wireless
---

### Post by xuanhua on 2009-03-06
hey everybody, i installed ubuntu 8.10 on my thinkpad r61i and the wireless hardware can't work with the default driver. After installing madwifi-hal-0.10.5.6-current driver, it can connect to wireless lan using NetworkingManager( a little tools provided).

but i hope to connect to wireless lan from command line (i am trying to make some trials about wireless lan, most of the work would be done by shell scripts)

i enabled the wireless device by the following commands:
(Supposing the wireless interface is called "ath0", and the driver called "ath_pci")

sudo modprobe ath_pci
sudo ifconfig ath0 up # After this the wireless 
                      # network card seemed work...


wlanconfig ath0 essid testm  # "testm" is available 
                             # ap 192.168.1.1

ifconfig ath0 192.168.1.6    # the fixed ip is available


After the above commands, i ping 192.168.1.1, but the destination
host is unreachable.

And then, if i use NetworkManager to connect "testm", there is response from 192.168.1.1 , it seems the NetworkManager has some kind of priority over the low level command.

so, to be simple, how can i configure my wireless connection only using command line?

---

### Post by xuanhua on 2009-03-06
I found it at last...

The reason is that NetworkManager is some kind of a daemon process, some command line configuration is restricted by it.

Just kill it and all can work well.

---

