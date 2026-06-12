---
title: "cannot connect to wired internet with static IP"
date: 2010-10-15
forum: Networking &amp; Wireless
---

### Post by Haagimus on 2010-10-15
currently running ubuntu 9.10, the internet connection im hooking up to is a router from a friends personal dish internet (were all deployed to Afghanistan). Here is all the static information that i need to input. 

Static IP - 10.142.12.30
Subnet Mask - 255.255.255.240
Default Gateway - 10.142.12.17
Preferred DNS 1 - 212.31.224.2
Preferred DNS 2 - 217.10.160.8

now i have all this information input in windows 7 and it works fine since its all broken out exactly how it was given to me in the ipv4 settings page. wicd in ubuntu however wont use these settings. when i open the preferences in the wired connection settings i get:

Static IP
Subnet Mask
Default Gateway
Host DNS
Search DNS
DNS 1
DNS 2
DNS 3

there is no confusion with the information up top since its still the same but the DNS stuff, i suppose, i am doing wrong. i have tried just inputting into DNS 1 and 2 but i get an error about the host dns. i put the first dns into the host and second into 1 and i no longer get an error but i also cannot connect. 

im at my wits end here guys/girls is appreciated i would love to finish my upgrade to ubuntu 10.04 since a half upgrade pretty much obliterated my 9.10 when it uninstalled all my drivers for the upgrade.

also i read on another forum that i should adjust my /etc/network/interfaces file to reflect something like this

auto eth0
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

i did that but still nothing.

---

### Post by neomod on 2010-10-15
I'm not really expert, neither I have ever managed a dish connection settings but maybe this might help you: when trying to set up my wired connection with DNS i put the specific dns inside router admin page and then pointed system dns to router address. 
In your case you might try to set up DNS = GATEWAY (10.142.12.17) : in this way DNS requests are passed straight to router which, hopefully, should have inside it's settings proper DNS.

Anyway, it's just a try: i'm not an expert.

---

### Post by Haagimus on 2010-10-23
so i tried putting the gateway as the default DNS but no luck there. i noticed something interesting in my ifconfig output

eth0      Link encap:Ethernet  HWaddr e0:cb:4e:50:44:46  
          inet addr:10.142.12.24  Bcast:10.142.12.31  Mask:255.255.255.240
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:37 

the inet addr and mask are both what they should be however the Bcast address is something foreign, not sure if it has anything to do with my problem but i cannot find any way to change this. its also worth noting that i have Conky setup to monitor my internet connection be it wired or wireless and when i click connect the address pops up in conky and stays there but WICD will basically set the static ip then disconnect immediately. im fresh out of ideas and im about to lose the internet in a couple days, probably for a month or so while im moving around this godforsaken country of afghanistan so any help on the quick is greatly appreciated.

---

