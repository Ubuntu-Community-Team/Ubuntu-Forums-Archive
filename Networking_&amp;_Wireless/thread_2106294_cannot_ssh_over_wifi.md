---
title: "cannot ssh over wifi"
date: 2013-01-18
forum: Networking &amp; Wireless
---

### Post by davidgutu on 2013-01-18
I have a machine I cannot ssh to over wifi from my computer. Ssh works over ehternet. I can also connect to it from another machine (even on another unconnected network in a different geographical location). I have flushed out all my iptables by running:
```
iptables -F
iptables -X
iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT
```

I have also stopped ufw (```
sudo service stop ufw
```) but none of it has worked. Any ideas?

I have tried pinging to the machine but it fails from my laptop. It works form other locations.

If I switch to windows, it all works. Thanks

---

### Post by ahallubuntu on 2013-01-18
Are you connected by WiFi to the same router that you are connected to via Ethernet?

Sure the settings are "automatic" with each one of them?

---

### Post by dpurgert on 2013-01-18
check that you're not blocking port 22 over the wireless (who knows...) or that the wireless isn't on a "blocked" network segment (e.g. the ssh server allows from 192.168.1.50-99, and wireless starts at 192.168.1.100)

---

### Post by lisanels47 on 2013-01-18
Some routers have a setting in there about wifi isolation or something like that.  It prevents two wifi devices from connecting to each other.  Turn that off.

Look in the wifi settings on the router.  Maybe in the advanced settings.

---

### Post by ahallubuntu on 2013-01-18
> **lisanels47 said:**
> Some routers have a setting in there about wifi isolation or something like that.  It prevents two wifi devices from connecting to each other.  Turn that off.

Look in the wifi settings on the router.  Maybe in the advanced settings.

Oh, I'll bet you that's the problem!

---

### Post by Aergan on 2013-01-19
Have had the same problem, wireless isolation enabled on the router/access point. If there is no option to turn it off then assume it's set to enabled.

---

### Post by davidgutu on 2013-01-22
I'm actually at a college so I can't reset wifi access points. It also works on another operating system, say windows. I think the problem is somewhere within my settings.

---

