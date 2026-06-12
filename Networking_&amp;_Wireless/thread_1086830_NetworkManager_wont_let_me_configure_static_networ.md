---
title: "NetworkManager wont let me configure static network"
date: 2009-03-04
forum: Networking &amp; Wireless
---

### Post by DeepSeaNautilus on 2009-03-04
Hello, I wanted to connect to a network with a static ip address, gateway and netmask. I found that in linux it is required to modify two network configuration files to do this.
The first one is /etc/network/interfaces, in which I wrote the following:
```
iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1 
```

The second is /etc/resolv.config in which I wrote the following:
```
nameserver 80.58.0.33
nameserver 80.58.32.97 
```

The addresses are just examples.

Finally I typed this:
```

killall NetworkManager
sudo /etc/init.d/networking restart
ifconfig eth0 up
NetworkManager

```

The problem is that NetworkManager was still trying to get an address from dhcp service, which should not be, since I already assinged it on the network files I mentioned above. When I introduced the data directly into Edit connections window it did connect, so I know everything else was ok. But I don´t want to use NetowrkManager`s GUI to configure the network, I want to use bash scripts to configure my networks easily and be able to use them in other linux distros, how can I do this?
Thanks in advance.

---

### Post by ddrichardson on 2009-03-05
Network Manager overrides these files.

You can disable NM [https://help.ubuntu.com/community/NetworkManager#Disabling%20NetworkManager](https://help.ubuntu.com/community/NetworkManager#Disabling%20NetworkManager)

---

