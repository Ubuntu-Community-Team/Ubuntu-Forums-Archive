---
title: "Loosing static IP settings after reboot"
date: 2010-12-01
forum: Networking &amp; Wireless
---

### Post by Baphomet on 2010-12-01
Hello Everyone.

I'm Using the latest Kubuntu 10.10 with the default network manager -- which I think it's called Knetwork manager.

I have set up a static IP by adding a new connection using this manager and then clicking it so that it is used to connect. But as soon as there is a computer reboot the connection falls back to the original autoeth0 which has dynamic IP on and which I cannot change or delete.

Thank you for your time in advance.

---

### Post by Iowan on 2010-12-01
I'm not really familiar with Kubuntu (or Knetwork Manager), but my Ubuntu Network Manager gives the option to Connect Automatically (even for Auto eth0). Does Knetwork Manager have that option? If so, what happens if you uncheck the box?

---

### Post by Baphomet on 2010-12-02
I can't really change anything for autoeth0 which I think is the main problem at the end.

---

### Post by pricetech on 2010-12-02
Alternative;  Does your router let you reserve IP address according to MAC ??  I've taken to using that exclusively to "fix" my IPs.

---

### Post by Baphomet on 2010-12-02
The IP was reserved by a faculty technician who took some info (like machine name, mac adress and such) but it is not forced by the router -- if I understood your question correctly. This then results on:

- the machine asking for a the static IP (the connection which I configured for static IP but have to go and click each time the computer is rebooted) or 
- the computer asks for any IP that the DHCP is attributing to it (the autoeth0 connection which is the default on the manager and I can't edit).

---

### Post by Baphomet on 2010-12-10
Should I install another manager and remove knetwork manager?

---

### Post by gmargo on 2010-12-10
Give this a try; I don't know for sure that it will work.
1. Remove entry you created in knetwork manager (gets this tool out of the picture)
2. Edit /etc/network/interfaces (make a backup first!)

/etc/network/interfaces should have lines like:
```

# The primary network interface
auto eth0
iface eth0 inet dhcp

```Replace that with the static ip info (here's my hardy static ip setup):
```

auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
address 192.168.1.6
netmask 255.255.255.0
gateway 192.168.1.1

```Reboot and see if it takes.

Similar info here:
[http://ubuntuguide.org/wiki/Ubuntu:Maverick#Set_a_static_IP_address](http://ubuntuguide.org/wiki/Ubuntu:Maverick#Set_a_static_IP_address)

---

### Post by Baphomet on 2010-12-11
Thanks! I'll give it a try!

---

