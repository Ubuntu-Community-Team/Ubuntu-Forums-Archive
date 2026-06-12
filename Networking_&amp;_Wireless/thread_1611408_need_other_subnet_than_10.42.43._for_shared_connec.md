---
title: "need other subnet than 10.42.43. for shared connection"
date: 2010-11-01
forum: Networking &amp; Wireless
---

### Post by DexterF on 2010-11-01
10.04 machine shares internet connection, used the network manager. 
Now the dhcpd NM uses here runs like this:

/usr/sbin/dnsmasq --no-hosts --keep-in-foreground --bind-interfaces --except-interface=lo --clear-on-reload --strict-order --listen-address=10.42.43.1 --dhcp-range=10.42.43.10,10.42.43.100,60m --dhcp-option=option:router,10.42.43.1 --dhcp-lease-max=50 --pid-file=/var/run/nm-dnsmasq-eth0.pid

So I have all clients on 10.42.43.

But I need them on 192.168.0.0/24 and even more, I need addresses assigned to IPs for 2 machines.

Where is the configuration for that dhcp server? There is no /etc/dnsmasq.conf

Who calls dnsmasq?

---

### Post by DexterF on 2010-11-01
Addendum: according to ps auxf Network-Manager calls dnsmasq directly, still I can't find where to configure it when called like this. Maybe it parses /etc/dnsmasq.conf if present. Will test that.

---

### Post by e79 on 2010-11-01
You might find me silly but why don't you just buy a cheap router that will share your Internet connexion ? Would be a hell lot easier.

As far as I understand you are trying to make your Ubuntu box act as a 'router' (sharing Internet connexion + providing DHCP service); and as far as my knowledge goes you would need 2 Network Interfaces to do that.

More about routing and dhcp servers under Ubuntu can be found here :

[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

[https://help.ubuntu.com/10.04/serverguide/C/dhcp.html](https://help.ubuntu.com/10.04/serverguide/C/dhcp.html)

Hope this helps

---

### Post by DexterF on 2010-11-01
I have only a laptop with a pcmcia umts modem right now that can connect to the internet until broadband is available, I just moved. This is a temporary solution.

The links are for building a server by the book, I need to configure the ICS feature in ubuntu's network manager.

---

### Post by e79 on 2010-11-01
> **DexterF said:**
> ...I need to configure the ICS feature in ubuntu's network manager.

Inthat case this should provide you with the necessary info :

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

There is a way to set up a DHCP3 server in conjunction with FireStarter (Firewall application), the latter use a GUI but in any cases, you will probably have to add some command lines :

[https://help.ubuntu.com/community/Internet/ConnectionSharing#Alternate%20gateway%20software%20%28GUI%29](https://help.ubuntu.com/community/Internet/ConnectionSharing#Alternate%20gateway%20software%20%28GUI%29)

---

### Post by DexterF on 2010-11-01
This is not helping. I am at 99% with the NM-ICS solution.
Going back to 0 and start all over with a different approach is viable after the first has proven impossible or impractical - which it hasn't by now.


All I need is: how does NM call dnsmasq and how do I pass it a different config.

---

### Post by bab1 on 2010-11-01
> **DexterF said:**
> This is not helping. I am at 99% with the NM-ICS solution.
Going back to 0 and start all over with a different approach is viable after the first has proven impossible or impractical - which it hasn't by now.


All I need is: how does NM call dnsmasq and how do I pass it a different config.

NM has internal coding that directly talks to DNSmasq-base.  This is a subset of DNSmasq.  The user can't modify these.  

From the [**_DNSmasq _**]("https://help.ubuntu.com/community/Dnsmasq")  help pages: "Note that the package "dnsmasq" interferes with Network Manager which can use "dnsmasq-base" to provide DHCP services when sharing an internet connection. Therefore, if you use network manager (fine in simple set-ups only), then install dnsmasq-base, but not dnsmasq. If you have a more complicated set-up, uninstall network manager, use dnsmasq, or similar software (bind9, dhcpd, etc), and configure things by hand."

---

### Post by DexterF on 2010-11-02
Thanks for pointing that out. 
Too bad leaves me in even hotter water, for if I uninstalled network-manager I would not know how to talk to the umts modem.

---

