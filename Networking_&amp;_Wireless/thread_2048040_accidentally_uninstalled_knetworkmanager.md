---
title: "accidentally uninstalled knetworkmanager"
date: 2012-08-26
forum: Networking &amp; Wireless
---

### Post by rockprincess on 2012-08-26
Hello friends,

I've accidentally uninstalled the knetworkmanager (i wanted to install the gnome-network-manager package) and somehow it only uninstalled the knetmanager and its dependencies.

So what to do now?

I've tried to download knetworkmanager and put it on a usb pen drive and then install it, but unfortunately it has too many dependencies, so that's an impossible task.

please help, i have no idea other than a fresh install (which i would like to avoid by all costs)

thanks

---

### Post by steeldriver on 2012-08-26
If you're lucky (and haven't done any housekeeping with apt-get clean recently) you may find that the deb file is still cached - in which case you should be able to reinstall using dpkg

Otherwise I think your simplest option would be to set up a temporary network connection manually using /etc/network/interfaces so that you can then pull the missing packages from the repository as normal

---

### Post by rockprincess on 2012-08-26
> **steeldriver said:**
> If you're lucky (and haven't done any housekeeping with apt-get clean recently) you may find that the deb file is still cached - in which case you should be able to reinstall using dpkg

Otherwise I think your simplest option would be to set up a temporary network connection manually using /etc/network/interfaces so that you can then pull the missing packages from the repository as normal

thanks for your quick reply, steeldriver.
no, i haven't run apt-get clean yet, so I'll give it a go. do i need to point it to a specific directory? or can i just run dpkg -i knetworkmanager ?

if i set up a connection manually, can i just do this if I'm connected with an Ethernet cable or can i also do this if i have only a wifi connection? 

thanks for the advice ;)

---

### Post by steeldriver on 2012-08-26
Let's see if we can find the package first:

```
find /var/cache -iname '*.deb' | grep 'network'
```And also exactly which bits are missing:

```
dpkg -l | grep 'network-manager'
```Setting up the temporary /etc/network/ interface is easier if you can grab a wired connection - but not impossible with wireless.

---

### Post by rockprincess on 2012-08-26
> **steeldriver said:**
> Let's see if we can find the package first:

```
find /var/cache -iname '*.deb' | grep 'network'
```And also exactly which bits are missing:

```
dpkg -l | grep 'network-manager'
```Setting up the temporary /etc/network/ interface is easier if you can grab a wired connection - but not impossible with wireless.

unfortunately I can't find it in the cache anymore :(
If i remove the grep network bit, a lot of packages come up but unfortunately not any network package.


dkpg -l | grep 'network-manager' finds the following:

network-manager
network-manager-gnome:i386
network-manager-kde
network-manager-pptp

i am now connected to a wired connection

ifconfig -a showed eth0 without an ip, that's why I defined it manually:

```
ifconfig eth0 192.168.1.103 broadcast 192.168.1.255 netmask 255.255.255.0 up
```

but it still wouldn't work :(

did i forget something?

EDIT: /etc/network/interfaces says the following:

auto lo
iface lo inet loopback

---

### Post by steeldriver on 2012-08-26
Hmm... I don't have any experience of bringing the interface up manually that way - I would guess you're missing at least the DNS service and probably a default gateway

Try 

```
ping 74.125.226.34
```(this is a google ip) and if it says 'Network is unreachable' then try adding a gateway using

```
sudo route add default gw 192.168.1.xxx eth0
```where xxx is the trailing IP of your router. If that works (i.e. you can ping external hosts by IP) we will have to figure out how to add a DNS server - which has become tricky now that resolvconf / dnsmasq have entered the picture

EDIT: actually it's probably OK to do

```
echo "nameserver 8.8.8.8" | sudo tee -a /etc/resolv.conf"
```just for now because resolvconf will simply overwrite it when you fix everything and restart network-manager - I hope I'm not out of line there

FWIW I just stopped network-manager on one of my boxes here and then did exactly these steps and was able to do a 'sudo apt-get update' afterwards. I then took eth0 down and restarted network-manager and everything seemed to go back to normal - including reverting my changes to /etc/resolv.conf - hope this helps

---

### Post by rockprincess on 2012-08-26
You sir, are my new hero!
With your help I'm back online.

Looks like my problem were an empty resolv.conf (inserted the router as my nameserver now)
and i had no standard gateway define

route (or netstat -rn) couldn't resolve...

now updates work again, knetworkmanager is now working again, both for wired/ethernet connection as well as wifi.

thank you so much steeldriver, you saved my *** :)

---

### Post by steeldriver on 2012-08-26
Happy to help - we've all had those 'Oh $#&@!' moments - kind of like realizing you just sawed through the branch you were sitting on ;)

For the record, you should probably define your router as DNS server via the network manager applet (if you didn't already do so) - in the new scheme of things the resolvconf service takes over /etc/resolv.conf and overwrites it

---

