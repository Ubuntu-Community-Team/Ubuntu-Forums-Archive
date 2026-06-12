---
title: "connecting to internet"
date: 2006-01-23
forum: Networking &amp; Wireless
---

### Post by rodl on 2006-01-23
Ubuntu box connected to network, but unable to see the internet(adsl router plugged into network)
Network settings static ip192.168.1.6, subnet255.255.255.0, gateway router address.
when i try firefox error cannot connect, all i can see is the local network.
where to go from here?
Rod
Ps very new to ubunto

---

### Post by stream303 on 2006-01-23
Under the DNS tab in your network settings, do you have any search domains, ie

yourisp.net

or perhaps your isp's nameservers entered?

---

### Post by cayamara on 2006-01-23
[QUOTE=rodl]Ubuntu box connected to network, but unable to see the internet(adsl router plugged into network)
Network settings static ip192.168.1.6, subnet255.255.255.0, gateway router address.
when i try firefox error cannot connect, all i can see is the local network.
where to go from here?
Rod
Ps very new to ubunto[/QUOTE]
Run ```
$ gksudo network-admin
``` and then double-click on the network card. In the new window, under "Configuration" choose "Static IP-Adress" and fill out the information below.
You can look at the screenshot I attached. Its in German though, but it should look the same in any other language. ;)

---

### Post by rodl on 2006-01-24
i looked in network tools > network device > config
found what Cayamara screen shot.
 i have
config man
ip 192.168.1.6
subnet 255.255.255.0
geteway 203.12.22.10

Stream303,

when i typed gksudo network-admin
under dns
192.168.1.1

does this help? thanks

---

