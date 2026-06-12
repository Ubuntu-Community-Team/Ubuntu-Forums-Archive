---
title: "Atheros atk9k - Slow Performance?"
date: 2013-06-07
forum: Networking &amp; Wireless
---

### Post by mykrob on 2013-06-07
Just got a new laptop, an Acer Aspire V5-571P. Everything works pretty good. A lot of people complained about the wifi not working at all, but mine worked out of the box. It does seem rather sluggish, although I have no empirical evidence. Just that my other laptop, which had Intel wifi of some sort, pulls up pages instantly on the same network. My, whereas this laptop takes several extra seconds before beginning to display a page. first thought was to install Compat-Wifi drivers, but apparently they do not compile well with 13.04 (64-bit, if that matters)

That said, here's is a little info about the wireless adapter:

```

*-network
       description: Wireless interface
       product: AR9462 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: DELETED
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.8.0-23-generic firmware=N/A ip=192.168.1.101 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:19 memory:f0500000-f057ffff memory:dfa00000-dfa0ffff

```

And I ran a ping test while typing this up, here are the results
```

--- 8.8.8.8 ping statistics ---
304 packets transmitted, 276 received, 9% packet loss, time 303570ms
rtt min/avg/max/mdev = 30.996/53.574/1715.894/149.411 ms, pipe 2

```

As you can see, I have a 9% packet loss, which I guess would be the only hard evidence that I have to support the sluggishness.. So what can I do to further troubleshoot and attempt to fix it? The only thing I have tried so far is to add an ath9k.conf file to /etc/modprobe.d to add the nohwcrypt=1 option.

Thanks

---

### Post by mykrob on 2013-06-07
Tried rmmod acer-wmi    and it made no difference. Just wanted to put that out there too.

---

### Post by mykrob on 2013-06-07
I think I may have solved the issue. I will mark it as such after running a ping with 0% packet loss for at least 1000 packets...
But I disabled power management on the wireless adapter, and got 0% for 200 pings. Will report back after this next test.

---

### Post by mykrob on 2013-06-07
I think I may have solved the issue. I will mark it as such after running a ping with 0% packet loss for at least 1000 packets...
But I disabled power management on the wireless adapter, and got 0% for 200 pings. Will report back after this next test.

---

### Post by mykrob on 2013-06-07
1000 packets, with 0% packet loss. Gonna go ahead an make this change permanent.

[http://itechscotland.wordpress.com/2011/09/25/how-to-permanently-turn-off-wi-fi-power-management-in-ubuntu/](http://itechscotland.wordpress.com/2011/09/25/how-to-permanently-turn-off-wi-fi-power-management-in-ubuntu/)

Will post back if I notice any negative side effects, but as of right now, the internet works as it should, and I like this laptop :)

---

### Post by mykrob on 2013-06-07
NOTE: One thing the article fails to mention, be sure to do this:

```
sudo chmod 777 /etc/pm/power.d/wireless
```

otherwise, the script will not execute on reboot. So if you have already done this, check your power management by typing  iwconfig and seeing what's reported. If it didn't survive a reboot, apply the code above, and it should survive after a reboot.

---

