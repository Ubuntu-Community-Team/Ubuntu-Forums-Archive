---
title: "iwconfig can't configure wireless connection"
date: 2011-02-20
forum: Networking &amp; Wireless
---

### Post by bprins on 2011-02-20
Hi,

I'm trying to configure my wireless via terminal instead of via the GUI. Via GUI (network-manager) works fine. When I delete my connection and try to set it up via terminal I get nothing. Here is what I did.

```

sudo iwconfig eth1 essid "linksys"
sudo iwconfig eth1 channel 11
sudo iwconfig eth1 key 107c72940e
sudo iwconfig eth1 mode Managed
sudo ifconfig eth1 up

```

Resulted in nothing, not even an error message. So I looked up what I created in /etc/network/interfaces, but it's pretty much empty.
```

bas@bas-Aspire-5741G:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

```

If I then connect via the network-manager again, it connects right away.

The essid, wep key, channel are correct, I am sure of that.

What am I doing wrong.

For those who ask themselves, why bother if it works: I screwed up my 11.04 installation and try to get it back up, just to learn from it.

Thanks a lot in advance.

PS: I read pretty much everything from "man iwconfig"

---

### Post by thefasterblueone on 2011-02-20
Maybe you need to restart the network before issuing the commands.

```
sudo /etc/init.d/networking restart
```

---

### Post by chili555 on 2011-02-20
As long as Network Manager is installed and running, manual methods including iwconfig are very difficult and usually impossible to implement. In fact, it's very difficult to temporarily stop NM in order to do so. Your system wants one or the other but not both.

---

