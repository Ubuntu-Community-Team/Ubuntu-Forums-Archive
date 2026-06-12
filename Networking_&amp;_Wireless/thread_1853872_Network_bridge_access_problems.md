---
title: "Network bridge access problems"
date: 2011-10-03
forum: Networking &amp; Wireless
---

### Post by Niksko on 2011-10-03
I'm having some trouble with a network bridge and I was hoping the very knowledgeable people here could help.

I have a machine that is running ubuntu server 11.04. This machine has two network cards. One network card is connected to my router, and thus, the rest of my network. This works fine. I would like the other network card to be connected a media centre pc which I can't connect directly to my router because I don't have enough ports. I'm trying to avoid buying a switch.

I'm confident that I have successfully configured a bridge between the two network cards as outlined [here]("http://manpages.ubuntu.com/manpages/natty/en/man5/bridge-utils-interfaces.5.html"), specifically the first example where the bridge is configured with a static ip, and leaving ip assignation to the router.

Despite this, the media center refuses to connect to the server, and hence, the network. The media center is running Mythbuntu 11.04. I've been configuring the media center to take a static ip by editing the /etc/network/interfaces file, but to no avail.

My configurations are:
Server /etc/network/interfaces:
```
auto lo
iface lo inet loopback

auto br0
iface br0 inet static
        address 10.0.0.1
        netmask 255.255.255.0
        network 10.0.0.0
        broadcast 10.0.0.255
        gateway 10.0.0.200
        bridge_ports all

```

and my media center's /etc/network/interfaces is:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 10.0.0.5
        netmask 255.255.255.0
        network 10.0.0.0
        broadcast 10.0.0.255
        gateway 10.0.0.200

```

I'm confident that it's not a cabling issue or some deficiency in the installation of the hardware, as the hardware and cables work in different configurations.

Can anybody see an error in the configuration, or suggest avenues for further troubleshooting? I suspect I'm missing something crucial, but I can't figure out what.

Regards

-Nik

EDIT: I'm not sure if this is relevant, but I've also tried putting a second network card in a windows 7 machine and bridging there, and that doesn't work either. Same network settings for the bridge as above.

---

