---
title: "Ubuntu 11.04 Fresh Install -- Can't open ports?"
date: 2011-06-28
forum: Networking &amp; Wireless
---

### Post by eladnava on 2011-06-28
Hi all,
Yesterday I switched from CentOS to Ubuntu, and wanted to install TeamSpeak3 which runs on ports 9987 UDP and 10011 TCP. The TeamSpeak3 worked fine on CentOS before this.

It appears to be running and netstat -an reports:

```

udp        0      0 0.0.0.0:9987            0.0.0.0:*
tcp        0      0 0.0.0.0:10011            0.0.0.0:*               LISTEN

```

I believe the only firewall for Ubuntu is "UFW", am I correct? If so, "ufw status" reports:

```
Status: inactive

```

I do have other things running on UDP (Counter Strike Source servers) and people can connect just fine.

When I **telnet localhost 10011** I get a response from the TeamSpeak3 server:
```

Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
TS3
Welcome to the TeamSpeak 3 ServerQuery interface, type "help" for a list of commands and "help <command>" for information on a specific command.
```

However, telnetting from outside just gets no answer, this is what leads me to believe it is a firewall in the way.

Anyone know what I'm doing wrong?

Thanks!

---

### Post by eladnava on 2011-06-29
Does anyone have any idea what this could be? Maybe a network firewall?

---

### Post by Dangertux on 2011-06-29
Are you behind a NAT router of any type?

---

### Post by eladnava on 2011-06-29
I'm not supposed to be -- is there any way to check? The server is hosted in a ISP datacenter in my country, and we asked to be taken off the firewall.

This is my network configuration:
```

# The primary network interface
auto eth0
iface eth0 inet static
        address 212.199.167.172
        netmask 255.255.255.248
        network 212.199.167.0
        broadcast 212.199.167.175
        gateway 212.199.167.169
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 80.179.55.100 80.179.50.100
        dns-search co.il

```

In CentOS, the ports were accessible and working, but ever since switching to Ubuntu (which is much much better!) this problem has been occurring where the "unpopular" ports are not open.

For example, all the popular services ports, e.g. 21, 22, 25, 53, 80, 110, 443, 8080 are open and accessible, but all of the "uncommon" ports are not open. (e.g. 9987, 10011) This would sound like a firewall configuration that only allows the popular server ports by default.

---

### Post by eladnava on 2011-06-29
OK I checked with my Datacenter support team they said my specific server is NOT on any firewall.

So my question is, are there any other firewalls or means of blocking traffic in Ubuntu? Something like IPTables? How can I temporarily disable them to see if they are causing the traffic block?

[size=6]**Edit: Fixed,**[/size] problem was within IPTables -- My unopen ports were not listed in "iptables -L". It was dropping all connections except a bunch of them configured by Ispconfig3 in its administration panel. All I had to do was add my desired ports to the list.

---

