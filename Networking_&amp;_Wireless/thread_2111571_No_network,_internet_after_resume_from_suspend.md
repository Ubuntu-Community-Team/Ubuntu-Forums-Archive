---
title: "No network, internet after resume from suspend"
date: 2013-02-02
forum: Networking &amp; Wireless
---

### Post by firekage on 2013-02-02
Hi guys!.

I've been testing recently all "ubuntu" based distros like Mint, Lubuntu, Xbuntu. I've come across one big problem that is present on all this distros.

There is no internet, network after resume from suspend. I put to resume, than wake up it and there is no internet, no network. Typing sudo ifconfig -a shows that the ip addres is not present, not obitained, or not configured.

My distros are created to run as a live distribution on usb stick but with "partition" to enable changes and stored them permamently.

I would like to use suspend, put to sleep, than wake it up and having internet.

Could you help me?


BTW - restarting network by sudo services networking restart doesen't help. One thing more: if this command is typed in Ubuntu then this command crashes unity, freezes desktop and crashes system, we can only hit ctrl+alt+del, can't even switch to terminal. On xubuntu and lubuntu there is no such behaviour but like i wrote, no network/internet.

```

firekage@lubuntu:~$ sudo ifconfig -a
[sudo] password for firekage: 
eth0      Link encap:Ethernet  HWaddr 00:13:xxx  
          inet addr:192.xxx  Bcast:192.xxx  Mask:255.xxx
          inet6 addr: fe80::213:xxx Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:174582 errors:0 dropped:0 overruns:0 frame:0
          TX packets:122547 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:207497547 (207.4 MB)  TX bytes:47211634 (47.2 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2302 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2302 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:296123 (296.1 KB)  TX bytes:296123 (296.1 KB)

```

and :

```

firekage@lubuntu:~$ ethtool eth0
Settings for eth0:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: No
    Speed: 100Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: Unknown
Cannot get wake-on-lan settings: Operation not permitted
    Current message level: 0x000000ff (255)
                   drv probe link timer ifdown ifup rx_err tx_err
Cannot get link status: Operation not permitted
firekage@lubuntu:~$ 

```

Regarding XXX in ip.addres: i did it. There is an full ip addres but after wake up from resume i see that it is not present.

---

### Post by firekage on 2013-02-02
I think i found a solution. It was mentioned over the internet.

Removing driver by rmmod command and than starting again driver by modprobe did the trick!

I would like now to know what to do in order to have it done automatically when suspend to ram and waking it up.

---

### Post by Toz on 2013-02-02
Create (if it doesn't already exist) the file /etc/pm/config.d/modules and add the following to the file:
```
SUSPEND_MODULES="<driver>"
```
...replace <driver> with the actually driver name that you rmmod'd.

This will manually unload the driver during the suspend cycle and re-load it during thaw.

---

### Post by firekage on 2013-02-04
> **Toz said:**
> Create (if it doesn't already exist) the file /etc/pm/config.d/modules and add the following to the file:
```
SUSPEND_MODULES="<driver>"
```...replace <driver> with the actually driver name that you rmmod'd.

This will manually unload the driver during the suspend cycle and re-load it during thaw.

Thanks. I tried to do it eariler because i found this kind of solution over the internet. No luck. Doesen't work.

I have to use rmmod and modprobe manually.

```
 sudo rmmod sky2 && sudo modprobe sky2 
```

and this works.

Anyway, big thanks.

---

### Post by sandyd on 2013-02-04
Moved to networking and wireless

---

### Post by Toz on 2013-02-04
Interesting. Try this instead:

1. Create the file /etc/pm/sleep.d/99sky

2. With the following content:
```

#!/bin/bash

case $1 in
     suspend|suspend_hybrid|hibernate)
	rmmod sky2
        ;;
     resume|thaw)
	modprobe sky2
        ;;
esac

```

3. Make the file executable.

4. Try suspending again. If it doesn't work, post back the contents of /var/log/pm-suspend.log and the results of:
```
cat /var/log/syslog | grep PM:
```

---

### Post by firekage on 2013-02-06
Thanks for Your time and help. Much appreciated. I will try your solution as fast as i could to get my hands on laptop that i used when i tried to face this problem with internet, suspend and no connection at all.

---

