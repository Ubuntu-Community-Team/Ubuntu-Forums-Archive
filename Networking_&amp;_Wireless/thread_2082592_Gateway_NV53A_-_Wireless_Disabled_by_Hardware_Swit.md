---
title: "Gateway NV53A - Wireless Disabled by Hardware Switch"
date: 2012-11-09
forum: Networking &amp; Wireless
---

### Post by h0nd0 on 2012-11-09
During installation of Ubuntu 12.10, my wireless worked.  Post-installation Network Manager showed *"Wireless Disabled by Hardware Switch"*.

Long story short I had to black-listed the **acer_wmi** module. 

```
sudo nano /etc/modprobe.d/blacklist.conf
```

Add the following at the end of the file:

```
# Acer Wireless Module
acer_wmi
```

Reboot and if all goes well, the wireless should work.

This solution should apply to Gateway laptops [manufactured by Acer] and Acer laptops.

**Note:**  I've noticed in other post people not able to find the *-wmi module, try an underscore instead, *_wmi.

---

### Post by h0nd0 on 2012-11-17
> **h0nd0 said:**
> During installation of Ubuntu 12.10, my wireless worked.  Post-installation Network Manager showed *"Wireless Disabled by Hardware Switch"*.

Long story short I had to black-listed the **acer_wmi** module. 

```
sudo nano /etc/modprobe.d/blacklist.conf
```

Add the following at the end of the file:

```
# Acer Wireless Module
acer_wmi
```

Reboot and if all goes well, the wireless should work.

This solution should apply to Gateway laptops [manufactured by Acer] and Acer laptops.

**Note:**  I've noticed in other post people not able to find the *-wmi module, try an underscore instead, *_wmi.

*****UPDATE*****
The code for blacklisting the module should read
```
# Acer Wireless Module
blacklist acer_wmi
```

My apologies for missing that.

---

### Post by renopete on 2013-06-01
It's now June 1st 2013 and I have run into a similar problem trying to get networking going on a Gateway NV53A, that has a Realtek rtl8192SE chip.

It's a friends laptop that I've just installed Ubuntu 12.10 onto and it's running right next to my laptop which is also running Ubuntu 12.10 and connecting just fine to the same wireless routers.

It sees the available wireless routers, but fails to connect to any of them.

I've blacklisted acer_wmi as you suggested, but it still doesn't work.

However ifconfig wlan0  
shows
RX packetes:2649 errors: 0

So it's getting something back from the router just not connecting.

Any suggestions?

-Pete

---

