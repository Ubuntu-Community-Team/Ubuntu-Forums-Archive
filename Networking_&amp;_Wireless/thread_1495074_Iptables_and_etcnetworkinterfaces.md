---
title: "Iptables and /etc/network/interfaces"
date: 2010-05-27
forum: Networking &amp; Wireless
---

### Post by Athunye on 2010-05-27
I was reading this: [https://help.ubuntu.com/community/IptablesHowTo#Solution #1 - /etc/network/interfaces]("https://help.ubuntu.com/community/IptablesHowTo#Solution #1 - /etc/network/interfaces")
> 
**Solution #1 - /etc/network/interfaces**

Modify the /etc/network/interfaces configuration file to apply the rules automatically. **You will need to know the interface that you are using in order to apply the rules ** - if you do not know, you are probably using the interface eth0, although you should check with the following command first to see if there are any wireless cards:



Why do I need to know what interface I am using?

Actually, I have eth0 and wlan0. How should I really proceed?

If I have:[i]
pre-up iptables-restore < /etc/iptables.rules
[/i] **after** the eth0 entry, **will** my iptables rules **apply to wlan0 as well?**

Here's my /etc/network/interfaces file:
```


auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
	address 192.168.1.10
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.1
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 208.67.222.222 200.176.2.10


auto wlan0
#iface wlan0 inet dhcp
iface wlan0 inet static
    address 192.168.1.10
    network 192.168.1.0
    netmask 255.255.255.0
    broadcast 192.168.1.255
    gateway 192.168.1.1
    #pre-up wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
    #post-down killall -q wpa_supplicant
    wpa-driver wext
    wpa-conf /etc/wpa_supplicant.conf

```

I regularly use both interfaces. After which one should I really add 
```
pre-up iptables-restore < /etc/iptables 
``` ?

Any help and ideas are welcome. Thanks in advance.

---

