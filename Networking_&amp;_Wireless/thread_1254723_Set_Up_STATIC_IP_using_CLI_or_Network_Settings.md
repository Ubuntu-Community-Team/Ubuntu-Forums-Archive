---
title: "Set Up **STATIC** IP using CLI or Network Settings"
date: 2009-08-31
forum: Networking &amp; Wireless
---

### Post by snorkytheweasel on 2009-08-31
Jaunty 9.04

For one of my machines I have to use a static IP: 10.21.1.16 /24 That address is not negotiable.

I cannot set a static IP AND have the machine visible to the rest of the network (and *vice versa*)
[LIST]
[*]Using System --> Preferences --> Network Connections, I can set an IPv4
IP 10.21.1.16
netmask 255.255.255.0
gateway 10.21.1.1

However, that static IP is not persistent, i.e, when I reboot, the system reverts to DHCP & dynamic IP: 10.1.1.136
The good news is that when the IP is dynamic (assigned via dhcp), the computer can see the rest of the network and the rest of the network can see it.

OR

[*]from the CLI I can set
[LIST=1]
[*]/etc/resolv.conf
nameserver 10.1.1.10
[*]/etc/network/interfaces
address 10.21.1.16
netmask 255.255.255.0
network 10.21.1.0 /24
broadcast 10.21.1.255
gateway 10.21.1.1

[/LIST]
That setting is persistent
But ... 
the computer cannot 'see' the rest of the network, and the rest of the network cannot 'see' it
[/LIST]
I have the worst of both worlds, and have to choose between seeing the network or having the static IP that I have to use.

What I need is a machine 
[LIST=1]
[*]with a static IP 10.21.1.16 /24
[*]that can interoperate in the network
[/LIST]

Ideas? Keep in mind 
[LIST]
[*]DHCP is not an option for the computer in question.
[*]Other subnets include 10.1.xxx.xxx, 10.10.xxx.xxx, 10.20.xxx.xxx, 10.30.xxx.xxx, 10.40.xxx.xxx
[*]There are 2400+ devices in the system,and they all get along fine: they see and talk to each other.
[*]There are 15 or so other devices with fixed IPs. They all work fine. Those are  Windows machines.
[/LIST]

---

### Post by Iowan on 2009-08-31
If the router at 10.21.1.1 has a path to the 10.1.1.0/24 subnet, you may be able to reach it.  Network Manager (on 9.04) *should* let you configure a static address - otherwise, you can configure it in */etc/network/interfaces* (but you may need to manually edit */etc/resolv.conf as well*).

---

### Post by uylug on 2009-08-31
What is the output of

```
cat /etc/network/interfaces
```

NetworkManager often replaces the contents of this file. You may be having problems with that.

---

### Post by Iowan on 2009-08-31
> **uylug said:**
> NetworkManager often replaces the contents of this file. Network Manager *should* ignore interfaces configured in */etc/network/interfaces,* and *should* leave the file alone, but...

---

### Post by snorkytheweasel on 2009-09-01
> **Iowan said:**
> If the router at 10.21.1.1 has a path to the 10.1.1.0/24 subnet, you may be able to reach it.  Network Manager (on 9.04) *should* let you configure a static address - otherwise, you can configure it in */etc/network/interfaces* (but you may need to manually edit */etc/resolv.conf as well*).


from the CLI I can set

   1. /etc/resolv.conf
      nameserver 10.1.1.10

   2. /etc/network/interfaces
      address 10.21.1.16
      netmask 255.255.255.0
      network 10.21.1.0 /24
      broadcast 10.21.1.255
      gateway 10.21.1.1

That setting is persistent
But ...
the computer cannot 'see' the rest of the network, and the rest of the network cannot 'see' it

---

### Post by snorkytheweasel on 2009-09-01
> **uylug said:**
> What is the output of

```
cat /etc/network/interfaces
```

NetworkManager often replaces the contents of this file. You may be having problems with that.

cat /etc/network/interfaces
address 10.21.1.16
netmask 255.255.255.0
network 10.21.1.0 /24
broadcast 10.21.1.255
gateway 10.21.1.1

That setting is persistent
But ...
the computer cannot 'see' the rest of the network, and the rest of the network cannot 'see' it

---

### Post by Bachstelze on 2009-09-01
> **snorkytheweasel said:**
> cat /etc/network/interfaces
address 10.21.1.16
netmask 255.255.255.0
network 10.21.1.0 /24
broadcast 10.21.1.255
gateway 10.21.1.1

That setting is persistent
But ...
the computer cannot 'see' the rest of the network, and the rest of the network cannot 'see' it

Is that really all you have in your /etc/network/interfaces?

---

### Post by dbalascak on 2009-09-01
You have only one interface, correct?
Post the output of
```


cat /etc/NetworkManager/nm-system-settings.conf


```

---

### Post by snorkytheweasel on 2009-09-01
> **Iowan said:**
> Network Manager *should* ignore interfaces configured in */etc/network/interfaces,* and *should* leave the file alone, but...

I can switch between dhcp & static by editing /etc/network/interfaces and /etc/resolv.conf

FWIW I use 6 files:
/etc/network/interfaces
/etc/network/interfaces.dhcp
/etc/network/interfaces.static
and 
/etc/resolv.conf
/etc/resolv.conf.dhcp
/etc/resolv.conf.static

To switch between dhcp & static I copy the .dhcp or .static file to the unadorned filename. Then I run sudo /etc/init.d/networking restart - or I reboot - or both, as needed.

I even tried removing NetworkManager and installing wicd. About each from Synaptic:
[LIST]
[*]WICD is a replacement for gnome network manager. It is an open source wired and wireless network manager for Linux which aims to provide a simple interface to connect to networks with a wide variety of settings.

[*]NetworkManager attempts to keep an active network connection available at all times. ***It is intended only for the desktop use-case, and is not intended for usage on servers***. That raises the question "why is NetworkManager the default tool in server installations - if one adds a gui?" Please no flame wars about gui on a server. In this situation, my boss - a self-described 'gui cripple' - requires a gui.
[/LIST]

Using wicd to manage the network, I get exactly the same results:
[LIST]
[*]using dhcp, the server & the rest of the network see each other & talk
[*]using static IP, neither sees the other
[/LIST]

---

### Post by snorkytheweasel on 2009-09-01
> **HymnToLife said:**
> Is that really all you have in your /etc/network/interfaces?

yes

---

### Post by dbalascak on 2009-09-01
So if DHCP works compare the output of *ifconfig -a* when using a DHCP address. Post it. Might be your subnet mask, but DHCP has the correct attributes.

---

### Post by snorkytheweasel on 2009-09-02
What's the smiley for relieved?

I tracked down the Cisco guy and asked him why I couldn't set up the IP on a subnet different from the one where I was working. After all, I do this all the time when setting up other servers, desktops, printers, etc. - remembering that the servers all had static IPs in 10. 0 - and everything else used DHCP in 10.10 or 10.30 or 10.40.

His response: 'you can and you did.'

'Huh?' said I.

'You have to plug the server into the switch for that subnet," he replied.
 
'But set up IPs all the time - from anywhere in the network,' I said.

'Not for 10.20,' he answered.

'Huh?' (that was I who "HUHed")

'10.20 is not trunked out of the "dungeon". The entire subnet is in the dungeon only,' he said. *[ Note: the "dungeon" is our main MDF for the WAN. It's located in the basement of a building a mile or so from my shop. ]*

Armed with that knowledge, I took the server to the Dungeon and connected it to the switch for 10.20. 

*Voilà!* It works!

So I told my boss - the one who told me to use 10.21.1.16 - how I got it working, i.e., connect to a switch in the dungeon.

'Huh?' said he. He didn't know that 10.20 wasn't trunked out with the rest of the WAN.

You've just seen community ignorance in action.

---

