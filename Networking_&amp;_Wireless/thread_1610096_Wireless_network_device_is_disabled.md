---
title: "Wireless network device is disabled"
date: 2010-10-31
forum: Networking &amp; Wireless
---

### Post by OoAmAyAoO on 2010-10-31
Hi
I'm having a wireless poroblem.When I typed the lsow command I got the following output:

```
*-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:21:00:bd:80:da
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
```My lap is hp6730s
I'm using ubuntu10.04
What should I do?

---

### Post by xircon on 2010-10-31
Try:

```
sudo gedit /var/lib/NetworkManager/NetworkManager.state
```

Change false to true, then reboot.
```

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


```

---

### Post by OoAmAyAoO on 2010-10-31
I'm new at this. Are these both codes that I should write in the terminal and what does reboot mean?

---

### Post by OoAmAyAoO on 2010-10-31
It is already true..
what should I do now?

---

### Post by Iowan on 2010-10-31
[Here]("http://ubuntuforums.org/showthread.php?t=1564615") is one that *might* help. You can also right-click Network Manager icon and verify Neworking and Wireless are both enabled there.

---

### Post by OoAmAyAoO on 2010-11-01
Thanks but that didn't work either ><

---

### Post by xircon on 2010-11-01
From a terminal:

```
lspci
```

Look through the output, what card does it report? e.g.

```
12:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)

```

Which is mine :)

Also run the hardware drivers program just in case (alt-f2 jockey-gtk).

Steve

---

### Post by OoAmAyAoO on 2010-11-01
```
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
```
And the hardware drivers program gave this first:
Downloading package indexes failed, please check your network status. Most drivers will not be available.

after searching it gave:
no proprietary drivers are in use on this system

---

### Post by xircon on 2010-11-01
Try searching the forum for BCM4312 e.g.

[http://ubuntuforums.org/showthread.php?t=1604868&highlight=BCM4312](http://ubuntuforums.org/showthread.php?t=1604868&highlight=BCM4312)

---

### Post by OoAmAyAoO on 2010-11-01
I hope this work
But I could not find in the firmware-b43-lpphy-installer in my sunaptic package manager
where can I get it from?

Thanks ^^

---

### Post by xircon on 2010-11-01
Think you need to enable restricted repository in synaptic.

settings>repositories Ubuntu software tab.

---

