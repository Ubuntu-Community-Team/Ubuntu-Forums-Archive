---
title: "losing connection after changing network settings"
date: 2006-07-04
forum: Networking &amp; Wireless
---

### Post by one_ro on 2006-07-04
Hi all,

I have a somewhat annoying problem which should have a quick fix. It's about a Toshiba laptop; when I change my network, I usually do it by copying different versions of:
[COLOR=Red] /[/COLOR][COLOR=Red]etc/network/interfaces
/etc/networks
/etc/resolv.conf[/COLOR]

then[COLOR=Navy]
[COLOR=Red] sudo ifdown eth0
sudo ifup eth0[/COLOR][/COLOR]

Everything works smooth, until I reboot. None of the network settings doesn't work anymore; I tried 
[COLOR=Red]/etc/init.d/networking restart[/COLOR]
with no avail

The only hack I found is to check "Activate when computer starts" in the System Settings / Network Settings / eth0 Configure Interface...

Is there a way to force this check every time I boot? Even more, is there a reason why it was introduced?

Cheers in advance.

---

### Post by tonyr on 2006-07-04
Explain, please, a little more about what "when I change my network" means.

---

### Post by one_ro on 2006-07-04
[quote=tonyr]Explain, please, a little more about what "when I change my network" means.[/quote] 
Hi tonyr,

Since it's about a laptop, I move from place to place with different network settings. I have created different files (interfaces, network, resolv.conf) for every network I want to be connected and I copy those files over those in /etc.
Basically, my routine is this (for example for "roda" network):[INDENT][COLOR=Black]sudo cp interfaces_roda /etc/network/interfaces
sudo cp networks_roda /etc/networks
sudo cp resolvconf_roda /etc/resolv.conf
sudo ifdown eth0
sudo ifup eth0[/COLOR]
[/INDENT]I hope I have answered your question,
Adrian

---

### Post by tonyr on 2006-07-04
Is your network connection wired  or wireless?

Can you post a couple of examples of your files (two different sites)?

---

### Post by one_ro on 2006-07-04
[quote=tonyr]Is your network connection wired  or wireless?

Can you post a couple of examples of your files (two different sites)?[/quote] 
Sorry for the delay, I had to leave for a while.
The connections are all wired, although I do have a built-in wireless card in my laptop (which btw gets also enabled after changing connections although I don't specify that).

A couple of examples for interfaces:

```
# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
    script grep
    map eth0

# The primary network interface
iface eth0 inet static
    address 193.231.1.234
    netmask 255.255.255.0
    network 193.231.1.0
    broadcast 193.231.1.255
    gateway 193.231.1.2
``` 
and 

```
# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
    script grep
    map eth0

# The primary network interface
iface eth0 inet static
    address 192.168.1.200
    netmask 255.255.255.0
    network 192.168.1.0
    broadcast 192.168.1.255
    gateway 192.168.1.1
``` 
The other files (network and resolv.conf) just specify the localnet and nameserver IPs.
All the best,
Adrian

---

### Post by tonyr on 2006-07-04
Add the line
```

auto eth0

```
above the **iface eth0** line in each version of **/etc/network/interfaces**
that you have.  This does the same thing as checking the "Activate when computer
starts" box in the configuration control.

Sorry for being late,  too.  The first US Space Shuttle launch in a long time (since
last disaster)  happened today; televised and webcast.  Had to watch.  All successful.

---

### Post by one_ro on 2006-07-05
Great :D
It works like a charm, thanks a lot.
And congratulations for the succesful launch, I imagine all Americans were keeping their fingers crossed.
Cheers,
Adrian

---

