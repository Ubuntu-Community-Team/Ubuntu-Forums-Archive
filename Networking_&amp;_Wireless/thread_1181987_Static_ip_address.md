---
title: "Static ip address"
date: 2009-06-08
forum: Networking &amp; Wireless
---

### Post by crabhunter on 2009-06-08
Hi,
I'm trying to set up my 9.04 lamp server to have a static address on my network.
I need to alter the following example of /etc/network/interfaces

auto eth0
iface eth0 inet static
address 172.19.0.10
netmask 255.255.255.0
network 172.19.0.0
broadcast 172.19.0.255
gateway 172.19.0.1


Now I know the address of my router
I know the broadcast 
I know the netmask
I know the address I want for my server

I need to know what to put for "network"

Mike

---

### Post by chili555 on 2009-06-08
Several of my Ubuntu machines, including a server run perfectly with static addresses set up like this:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 172.19.0.10
netmask 255.255.255.0
gateway 172.19.0.1
```That should work, but if not, please post back.

---

### Post by brabo on 2009-06-08
network is correct as it is.
when your ip is 172.19.0.10 then the network you're in is 172.19.0.0

you can also put a line:
dns-nameservers x.x.x.x y.y.y.y

at the end.

grtz,
brabo.

---

### Post by crabhunter on 2009-06-08
Thanks for the replies,I will try it out tomorrow as the server is at my works.
Mike

---

### Post by Iowan on 2009-06-08
Some claim (and **chili555**'s example demonstrates) that network and broadcast addresses are unnecessary if address and netmask are given.

---

### Post by brabo on 2009-06-08
Hey!

thanks for the extra info there Iowan. I see that it is idd unneccessary info, but i was not aware it was not required!

grtz,
brabo.

---

### Post by crabhunter on 2009-06-11
Ok, I seem to have a problem here.
In the examples of /etc/network/interfaces I've seen posted they have all started,

auto eth0
iface eth0 inet dhcp


Mine however is

auto lo
iface lo inet loopback


I have tried adding

auto eth0
iface eth0 inet static
address 192.168.1.22
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

But when I sudo /etc/init.d/networking restart
I get SIOCDELRT:No such process
If I restart the pc the network icon has a x in it and I have no network.
Any help would be appreciated.
Mike

---

### Post by alphacrucis2 on 2009-06-11
> **crabhunter said:**
> Ok, I seem to have a problem here.
In the examples of /etc/network/interfaces I've seen posted they have all started,

auto eth0
iface eth0 inet dhcp


Mine however is

auto lo
iface lo inet loopback


I have tried adding

auto eth0
iface eth0 inet static
address 192.168.1.22
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

But when I sudo /etc/init.d/networking restart
I get SIOCDELRT:No such process
If I restart the pc the network icon has a x in it and I have no network.
Any help would be appreciated.
Mike

Looks like your ethernet card isn't being picked up. Which version of ubuntu are you running (and server or desktop version). Also what does this give:

```
sudo lshw -C network
```

---

### Post by crabhunter on 2009-06-11
I'm running Ubuntu 9.04 desktop. 
sudo lshw -C network gives me, 


 *-network               
       description: Ethernet interface
       product: nForce2 Ethernet Controller
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: a1
       serial: 00:01:29:27:05:f6
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.1.21 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 66:f6:d4:91:90:e9
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by zika on 2009-06-11
> **crabhunter said:**
> But when I sudo /etc/init.d/networking restart
I get SIOCDELRT:No such process
If I restart the pc the network icon has a x in it and I have no network.
Any help would be appreciated.
Mike
***First:***You had **iauto eth0** and You should have **auto eth0** (see below). If tha doesn't solve the problem, follow down ...
***More:***Do You have **Network manager** running? If You do, that might be the cause of the problem.
Uncheck it in **StartUpApplications** in **Preferences**.
Modify **/etc/NetworkManager/nm-system-settings.conf** so that instead```
[ifupdown]
managed=false
```You have```
[ifupdown]
#managed=false
```
Also, check if Your network card is enabled in BIOS.
Also, once You've got rid of **NetworkManager** edit **/etc/resolv.conf **to look like```
search www.google.com
nameserver xxx.xxx.xxx.xxx
nameserver yyy.yyy.yyy.yyy
nameserver 208.67.220.220
nameserver 208.67.222.222
```and **/etc/network/interfaces**```
# The loopback network interface
auto lo
iface lo inet loopback

[COLOR=Red]auto eth0[/COLOR]
# The primary network interface DHCP
#iface eth0 inet dhcp

# The primary network interface static
iface eth0 inet static
address 192.168.1.22
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
#mtu 1444
```Try that. If it works than with **sysv-rc-conf** we can stop **NetworkManager**  from being loaded at all.

---

### Post by crabhunter on 2009-06-11
Thanks,I will need a bit of time to try all that.
I'll post back in a few days.
Mike

---

### Post by Iowan on 2009-06-11
Did you install a desktop on your LAMP server (or install the LAMP stack on a desktop) - or is it a standard CLI-only install?

---

### Post by crabhunter on 2009-06-12
I managed to get some help with this,luckily one of my customers happens to be a linux guru and he had a look at it for me.
He sorted it by deleting the network entry and creating a new one with a fixed ip.Despite being a command line sort of bloke he did it all graphically.
I am running Apache on a desktop 9.04 install so the gui was available.
Mike

---

