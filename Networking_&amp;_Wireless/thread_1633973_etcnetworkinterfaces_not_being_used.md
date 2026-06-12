---
title: "/etc/network/interfaces not being used"
date: 2010-11-29
forum: Networking &amp; Wireless
---

### Post by TennTux on 2010-11-29
I have paired down my /etc/network/interfaces to the following.

```
auto lo eth0 eth1



iface lo inet loopback



iface eth0 inet static

    address 192.168.1.10

    netmask 255.255.255.0

    network 192.168.1


iface eth1 inet static

    addrss 192.168.0.17

    netmask 255.255.255.0

    network 192.168.0

```

The network 192.168.0 has a DHCP server, however, I do not want this machine to use it. Instead I want it to have the static address I provide.  After booting running ifconfig from the command line reveals that it used the DHCP server for eth1 and didn't provide an IPv4 address for eth0. I have iterated through several generations of /etc/network/interfaces simplifying to figure out why I am having a problem. I will eventually be adding pre-up clauses and may even use a mapping clause. I had everything working in 10.4 before eventually installing 10.10 from scratch.

I have considered adding a hwaddress ether AA:BB:CC:DD:EE:FF to each interface but I suspect that should be a latter addition once I have my interfaces basically working. For a while eth0 was working correctly but now it too is having problems.

Looking at /var/log/syslog reveals many questions but I am not seeing many answers. The results of ```
fgrep -i eth < /var/log/syslog
``` reveals no errors, however, it shows NetworkManager has it's hands all over the interfaces. ```
avahi-daemon[799]: New relevant interface eth0.IPv4 for mDNS.
``` does this mean I have to use the interface name eth0.IPv4 in the /etc/network/interfaces file? NetworkManager[789]: has a couple of lines that talk about new Ethernet device(s) and the drivers that include 'tulip' and 'e1000'. Should both interfaces use the same driver or is this relevant to the particular hardware for each interface? Eventually dhclient appears to be trying DHCP to get an address for each interface. I am assuming that by this point since the interfaces have not been configured this is a fall back position?

I have re-reviewed 'man interfaces' and a number of other sources of information to no avail.

The bottom line is: How do I get the system to use my /etc/network/interfaces file to configure the two interfaces?

---

### Post by uncaspi on 2010-11-29
Items listed in this file are not handled by the network-manager, so you have to bring them up manually, but first you must stop the network-manager.

---

### Post by chili555 on 2010-11-29
> but first you must stop the network-manager.Or, ideally, completely remove it.

---

### Post by iponeverything on 2010-11-29
nm will ignore interfaces that are properly defined the interfaces file.

```

iface eth0 inet static
    address 192.168.1.10
    netmask 255.255.255.0

iface eth1 inet static
    address 192.168.0.17
    netmask 255.255.255.0

auto eth0 eth1 lo

```

No need for the "network" as its inferred from the netmask and if you decide to use it provide 4 octets.

---

### Post by TennTux on 2010-11-29
> **uncaspi said:**
> Items listed in this file are not handled by the network-manager, so you have to bring them up manually, but first you must stop the network-manager.

Before I reinstalled my interfaces would come up automatically and I thought NetworkManager was in Ubuntu 10.4? Perhaps I was wrong. From what I gather it is not possible to tell NetworkManager to keep its hands off of these interfaces. Short of uninstalling NetworkManager is it possible to tell it to not start on boot?

I have considered completely removing NetworkManager but I did not know if I might need it for something else, also I have been trying to install or remove as few packages as possible to minimize my efforts the next time I have to reinstall. But I will remove it if I must.

> **uncaspi said:**
> nm will ignore interfaces that are properly defined the interfaces file.
As for the network statement I only added it when not having it failed. But sure I can remove it.

---

### Post by iponeverything on 2010-11-29
> From what I gather it is not possible to tell NetworkManager to keep its hands off of these interfaces. Short of uninstalling NetworkManager is it possible to tell it to not start on boot?

nm will not manage interface properly defined in the interfaces file. No need to stop or uninstall it. It interfaces will not need to be brought up manually if it is on the "auto" line.

---

### Post by TennTux on 2010-11-29
> **iponeverything said:**
> nm will not manage interface properly defined in the interfaces file. No need to stop or uninstall it. It interfaces will not need to be brought up manually if it is on the "auto" line.

Then I guess I'm a little confused. I thought I properly defined the three interfaces (Including loopback) and added all of them to the "auto" line...

> **iponeverything said:**
> auto lo eth0 eth1

iface lo inet loopback

iface eth0 inet static
    address 192.168.1.10
    netmask 255.255.255.0
    network 192.168.1

iface eth1 inet static
    addrss 192.168.0.17
    netmask 255.255.255.0
    network 192.168.0

PS: I will be removing the network clause since it does not contribute anything.

---

### Post by iponeverything on 2010-11-30
> **TennTux said:**
> Then I guess I'm a little confused. I thought I properly defined the three interfaces (Including loopback) and added all of them to the "auto" line...



PS: I will be removing the network clause since it does not contribute anything.

The above:

it's "address" not "addrss"

and using "192.168.1" instead of "192.168.1.0" is wrong.

also just a one other small thing, the ubuntu version is 10.04 not 10.4.

---

### Post by uncaspi on 2010-11-30
There are different opinions on the forum if to remove nm or not.Chili555 said  remove. If you do so  then you had to write a shell script to bring them up, or put the commands in /etc/rc.local if you want them executed at boot up.

---

### Post by iponeverything on 2010-11-30
> **uncaspi said:**
> There are different opinions on the forum if to remove nm or not.Chili555 said  remove. If you do so  then you had to write a shell script to bring them up, or put the commands in /etc/rc.local if you want them executed at boot up.

it's not an opinion, it is a fact. This has been the behavior of nm for as long is it been used in ubuntu. 

no need to bring up the interfaces via rc.local if is on the "auto" line, as it will brought up by the default init scripts at boot.

---

### Post by TennTux on 2010-11-30
> **iponeverything said:**
> The above:

it's "address" not "addrss"

and using "192.168.1" instead of "192.168.1.0" is wrong.

also just a one other small thing, the ubuntu version is 10.04 not 10.4.

Ok. I fixed the 'addrss' -> 'address', removed both 'network' clauses and broke up the auto statement into three parts ('auto lo', 'auto eth0' and 'auto eth1') then rebooted and it still didn't work. I have not yet done anything with nm. I'm guessing removing nm is my next step unless there are other suggestions.

---

### Post by TennTux on 2010-11-30
Current /etc/network/interfaces
```
auto lo
auto eth0
auto eth1

iface lo inet loopback

iface eth0 inet static
  address 192.168.1.10
  netmask 255.255.255.0

iface eth1 inet static
  address 192.168.0.17
  netmask 255.255.255.0
```

---

### Post by iponeverything on 2010-11-30
maybe the evil invisible ^M

Try this --

The attached file is your valid interfaces file - Download it. Don't look at or edit it on a MS windows machine -- linux only. 

copy it to /etc/network/ on your box rename it from interfaces.txt to interfaces and reboot. (attachments here require extensions) 

if you need a default gateway, add the line to the appropriate stanza in the interfaces file.

---

### Post by TennTux on 2010-11-30
Your version of '/etc/network/interfaces' does not do it either. When I boot 'eth1' gets a DHCP (IPv4) address while 'eth0' gets no IPv4 address. Both get a IPv6 addresses.

I guess I am down to it and must de-install network-manager, network-manager-gnome, network-manager-pptp and network-manager-pptp-gnome.

---

### Post by chili555 on 2010-11-30
> I guess I am down to it and must de-install network-manager, network-manager-gnome, network-manager-pptp and network-manager-pptp-gnome.I believe so.

I think your interfaces file should also direct each interface to the correct gateway:> auto lo
auto eth0
auto eth1

iface lo inet loopback

iface eth0 inet static
  address 192.168.1.10
  netmask 255.255.255.0
  [COLOR="Red"]gateway 192.168.1.1[/COLOR]

iface eth1 inet static
  address 192.168.0.17
  netmask 255.255.255.0
  [COLOR="Red"]gateway 192.168.0.1[/COLOR]May I assume they are physically connected to two different routers/switches/whatever?

---

### Post by TennTux on 2010-11-30
Well, that did it. I had to de-install the 4 network-manager* packages. I guess nm does not play nice with others. :(

Thanks for everybodys help particularly chili555.

---

### Post by chili555 on 2010-11-30
Glad it's working.> I guess nm does not play nice with others.It's fine for what it is designed to do; allow a laptop to go to the library or the cyber cafe and connect. For more complicated tasks, it's just not designed to do what you are trying to do.

---

