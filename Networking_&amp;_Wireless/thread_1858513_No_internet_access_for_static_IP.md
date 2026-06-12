---
title: "No internet access for static IP"
date: 2011-10-12
forum: Networking &amp; Wireless
---

### Post by daktau on 2011-10-12
Hi all,
I am in need of a static ip for my ubuntu laptop which is acting as a webserver on my network. I recently changed my router and of course all the host files on the other machines on the network are no longer doing their job.

After having set up a static ip using the 'edit connections' link in the connection status icon I can no longer reach the internet from the ubuntu laptop. I can still see the router and log in to it while using a static IP though, just no internet. Whlst using DHCP the internet works fine but I am after using a static IP. 

I have set up the same IP address for the wired network and for the wireless network so the IP address will remain the same which ever method the laptop is using.

Other posts have on the internet seem to solve this problem but I am having difficulty.
I am running Lucid Lynx 10.04.

cheers,
George

---

### Post by Elysius on 2011-10-12
Unfortunatly at the moment I don't have a ubuntu computer around, I can't recall when editting the network adapter like you did if you have to fill in a nameserver.

Is the router's ip address located as your nameserver in /etc/resolve.conf?

---

### Post by CharlesA on 2011-10-12
I just edited the interfaces file - but I don't use network manager.

```
charles@Thor:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.2
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.1.1
        dns-search lcl

```

And resolv.conf
```
charles@Thor:~$ cat /etc/resolv.conf
search lcl
nameserver 192.168.1.1

```

---

### Post by matt_symes on 2011-10-12
Hi

You are based in Bristol, UK ? So i am (south Bristol)!

Sounds like you might have a route problem. Can you ping 8.8.8.8 ?

Using your static IP address, open a terminal and type

```
route
```Post the results back here using copy and paste. Please post between code tags like this...

[noparse]```
results
```[/noparse]

It will look like this...

```
results
```EDIT: Beaten to it. ;) You have speedy fingers Charles :)

Kind regards

---

### Post by praseodym on 2011-10-12
Hi,

your router should give your MAC address (and therefore your computer) a static IP. This IP should be _outside_ the DHCP range of the router.

---

### Post by CharlesA on 2011-10-12
> **matt_symes said:**
> 
```
results
```EDIT: Beaten to it. ;) You have speedy fingers Charles :)

Kind regards

Heheh. I actually had to SSH into my *nix box to grab that info. ;)

> **praseodym said:**
> Hi,

your router should give your MAC address (and therefore your computer) a static IP. This IP should be _outside_ the DHCP range of the router.

On my router (running dd-wrt) I had to set a reservation inside the dhcp scope. Otherwise set the IP as static outside the DHCP scope (or set it as an exemption).

---

