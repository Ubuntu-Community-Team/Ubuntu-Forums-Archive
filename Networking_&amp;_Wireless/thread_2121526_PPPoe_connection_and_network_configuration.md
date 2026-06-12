---
title: "PPPoe connection and network configuration"
date: 2013-03-02
forum: Networking &amp; Wireless
---

### Post by fernando98 on 2013-03-02
Hello everybody,

I'm currently using a PPPoe connection over Ethernet to connect to the Internet. I have configured it using the "pppoeconf" command. The process is quite straight fordward and I got Internet access easily (I set default options). It seemed to be working fine until I rebooted and got the "Waiting for network configuration" screen. I headed to /etc/network/interfaces and realised I set the ppp0 interface to "auto" which was a mistake so I deleted that line.

Rebooted once again, the boot was working fine but could not connect to the Internet due to the DNS addresses were missing. To solve that I tried changing the eth0 interface from manual to dhcp. It solved the DNS issue but I got once again the "Waiting for network configuration" screen so I kept manual mode and added the DNS addresses manually. Eventually I reached this /etc/network/interfaces file:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual
  up ifconfig $IFACE 0.0.0.0 up
  dns-nameservers (DNS IP provided by ISP)
  dns-nameservers (another one)

iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up
provider dsl-provider

```

This configuration works fine to connect to the Internet in every case I tested but it only boots regularly under a certain condition. Said condition is that I have my Ethernet to USB adapter plugged in (not the Ethernet cable itself but the adapter). If the adapter is plugged in Ubuntu will boot as expected but if not it will hang up for a while no matter wether the Ethernet cable is connected to the adapter or not. I really have no clue about this since it is just an adapter...

Here is also the /etc/ppp/peers/dsl-provider file configurated with pppoeconf:

```

noipdefault
defaultroute
hide-password
#lcp-echo-interval 30
#lcp-echo-failure 4
noauth
persist
#mtu 1492
#persist
#maxfail 0
#holdoff 20
plugin rp-pppoe.so eth0
user "ppp_username_provided"
usepeerdns

```

I'm running Ubuntu 12.10 in a Dell XPS 12. The adapter is a Logilink UA0144 which worked pretty bad under the same Ubuntu and other Ethernet networks (without PPPoe) but with this particular network gives a steady and fast connection.

Any help would be appreciatted.

Thanks in advance & have a nice day.

---

### Post by praseodym on 2013-03-02
Change false to true in the file /etc/NetworkManager/NetworkManager.conf
```

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=[COLOR="#FF0000"]false[/COLOR]
```
Otherwise the Networkmanager tries to connect and can not handle the manual configuration

---

### Post by fernando98 on 2013-03-02
I did it but there is no change. Still the same issue.

EDIT: Well, I did a little scripting so whenever I shutdown Ubuntu the ppp interface is disabled and whenever I boot it is re-established. So far seems to be working fine. If someone is interested I can explain it in further detail.

---

