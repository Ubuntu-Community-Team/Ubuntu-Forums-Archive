---
title: "Set up pppoe bridge on 10.04 server"
date: 2011-06-27
forum: Networking &amp; Wireless
---

### Post by chrisbay90 on 2011-06-27
How would I configure my box to connect to a modem in bridge mode?

I have a server at home that im migrating over to be the default-gateway/router. I have everything else setup (dns,dhcp etc) now just need the ppoe part, or so i beleive?

I have two interfaces. eth0 (lan) and eth1 ready to connect to the modem.
The modem is in bridge mode ready to go.
What is my next step? Are there any good guides, I didn't find any.

---

### Post by Dangertux on 2011-06-27
An application like pppoeconf might be what you're looking for. Sets up a bridged connection through modem bypassing NAT etc

[http://packages.ubuntu.com/lucid/pppoeconf](http://packages.ubuntu.com/lucid/pppoeconf)

---

### Post by chrisbay90 on 2011-06-28
Thank you dangertux. pppoeconf worked, very easy I might add. To anyone reading this, your modem must be plugged into the phoneline and have a sync before you can configure pppoeconf.

The bridge is setup.
I have internet access from the server
dhcp and lan access works
the dns server works and hosts can resolve domain names
However hosts cannot access the internet. (however if configured to use the squid server on the lan they can browse the www)

In other setups with an ethernet network on both interfaces I have run
      echo 1 > /proc/sys/net/ipv4/ip_forward
      iptables -A FORWARD -i <LAN interface> -j ACCEPT
in order for traffic to be routed. This did not work in my case today.

Could anyone help me out please?

---

### Post by Dangertux on 2011-06-28
> **chrisbay90 said:**
> Thank you dangertux. pppoeconf worked, very easy I might add. To anyone reading this, your modem must be plugged into the phoneline and have a sync before you can configure pppoeconf.

The bridge is setup.
I have internet access from the server
dhcp and lan access works
the dns server works and hosts can resolve domain names
However hosts cannot access the internet. (however if configured to use the squid server on the lan they can browse the www)

In other setups with an ethernet network on both interfaces I have run
      echo 1 > /proc/sys/net/ipv4/ip_forward
      iptables -A FORWARD -i <LAN interface> -j ACCEPT
in order for traffic to be routed. This did not work in my case today.

Could anyone help me out please?

in your iptables chain are you specifying the bridged interface or the eth interface? Because it needs to be the bridged interface.

---

### Post by chrisbay90 on 2011-06-28
The only iptables rule set is the one above
      iptables -A FORWARD -i eth0 -j ACCEPT
eth0 being the lan interface. As this has worked for me in the past for Ethernet-Ethernet network routes.

You are suggesting that
      iptables -A FORWARD -i pppoe -j ACCEPT
is the correct rule i need? Are there any other things i should set? I can't make any changes to the network at the moment, i will try this tonight. Thank you again Dangertux.

---

### Post by chrisbay90 on 2011-06-29
I've tried the chain with eth0, ppp0 and both, none work.

Running iftop on the server while pinging google shows the packet arriving on eth0.
there appears to be an entry for google in iftop on the server while pinging, but nothing reaching the client.

---

