---
title: "Problems after updating to 8.10"
date: 2008-12-05
forum: Networking &amp; Wireless
---

### Post by Jompa on 2008-12-05
I can't connect to the internet after updating to Ubuntu 8.10 on an old HP laptop. It worked fine with 8.04, but now it finds the connection, but won't connect. Hope someone has an idea of what can be wrong

---

### Post by zika on 2008-12-05
> **Jompa said:**
> I can't connect to the internet after updating to Ubuntu 8.10 on an old HP laptop. It worked fine with 8.04, but now it finds the connection, but won't connect. Hope someone has an idea of what can be wrong

There are two ways:

1.
```

sudo nano /etc/network/interfaces
```it should look like this:

> 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp(assuming that You use dhcp)

If You use static address it should look like:

> 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
    address xxx.xxx.xxx.xxx
    netmask 255.255.255.0
    gateway xxx.xxx.xxx.xxx
    broadcast 255.255.255.255

Do:
```

sudo ifdown eth0
sudo ifup eth0

```

2.
Open VPN connections after clicking on Network in Your panel. Click on eth0 and edit its settings. Enter Your IP address, netmask, gateway and DNS and choose Manul for DNS. It might not work from the first time but be patient. Once Your numebrs are remebered (netmask migt go to 24 instead of 255.255.255.0 but that is OK) You are on the rignt way. Be sure to check System settings and Connect automagically. If You do not get connected right away, restart machine, and, hopefully, You will be OK.

If You choose 1. You won't have Network Manager to bug You. I prefer 1. but have done 2. several time successfully. Just be patient and persistent.

---

### Post by gib2800 on 2008-12-06
If it finds the connection but won't connect then you may need to open (k)networkmanager and adjust your connection settings. Mine was not connecting to my wireless router after updating to Ubuntu 8.10 but it would connect to other unsecured wireless networks. Comparing the settings for the one that worked and the one I wanted to work I noticed that the wireless security was net set to WPA.

---

