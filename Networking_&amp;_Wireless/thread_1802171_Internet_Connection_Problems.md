---
title: "Internet Connection Problems"
date: 2011-07-11
forum: Networking &amp; Wireless
---

### Post by Alex090391 on 2011-07-11
I am running Ubuntu 10.10 on my Dell Inspiron 1545, and have been running Ubuntu on it for a couple years now. Last night we had some storms come through the area and our power went out, and after the power came back on I reconnected to the internet. I am using Firefox, but also have chromium, it says it cannot find the server. I can connect to wifi and a wired connection, I just cannot access the internet with the connections. I dual boot windows 7 as well, so I started that up and the wifi works on that, so it is something with Ubuntu and I was wondering if anyone out there could help me figure out what the problem is. If you need more information feel free to ask. Thanks in advance!

---

### Post by nm_geo on 2011-07-11
> **Alex090391 said:**
> I am running Ubuntu 10.10 on my Dell Inspiron 1545, and have been running Ubuntu on it for a couple years now. Last night we had some storms come through the area and our power went out, and after the power came back on I reconnected to the internet. I am using Firefox, but also have chromium, it says it cannot find the server. I can connect to wifi and a wired connection, I just cannot access the internet with the connections. I dual boot windows 7 as well, so I started that up and the wifi works on that, so it is something with Ubuntu and I was wondering if anyone out there could help me figure out what the problem is. If you need more information feel free to ask. Thanks in advance!

You can't get to the internet from wired or wireless when using Ubuntu but windows will connect wired and wireless?

Let's start with a few commands in terminal. just copy and paste and then paste results.

```

lspci -nn
```

```
rfkill list all
```

```
sudo lshw -C network
```

---

### Post by Iowan on 2011-07-11
A couple more to check:
From the aforementioned terminal (Applications>Accessories>Terminal), check **ifconfig -a** to see if the interface(s) get(s) an IP address. If so, can you ping the router? If that works, try to ping the internet (one place is 74.125.225.48). If not, check results of **route -n**

---

### Post by jmoorse on 2011-07-12
Reboot your router and modem.  Power outages cause this all the time.

If there is still no access after reboot make sure your router has learned an IP.  traceroute / mtr 4.4.4.4 will check for upsteam problems.

---

