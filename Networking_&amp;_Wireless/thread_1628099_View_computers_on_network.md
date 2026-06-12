---
title: "View computers on network"
date: 2010-11-22
forum: Networking &amp; Wireless
---

### Post by Vexiphne on 2010-11-22
Does anyone know of an app that I can use to view all the computers connected to my network and the IP addresses to those computers?

---

### Post by SeijiSensei on 2010-11-22
> **Vexiphne said:**
> Does anyone know of an app that I can use to view all the computers connected to my network and the IP addresses to those computers?

If you know your network address and subnet mask you can use nmap like this:

```
nmap -sP 192.168.1.0/24
```

That will ping every address between 192.168.1.0 and 192.168.1.255 and list those it finds.  If you have a DNS server with the reverse ("in-addr.arpa") zone for the subnet, you'll get the hostnames as well.

You can also use "nmblookup -A" from the Samba suite with an IP address to obtain the Netbios hostname that Windows computers advertise.  I've written a script that uses nmap to develop the list of addresses, then iterates over them and uses nmblookup to compile a list of their Windows hostnames.  I don't know of application that does the same thing.

---

### Post by Vexiphne on 2010-11-22
That was way to complicated :)
Isn't there a simpler way of doing it?

---

### Post by desnaike on 2010-11-22
I use etherape run from terminal with sudo command .

---

### Post by SeijiSensei on 2010-11-22
> **Vexiphne said:**
> That was way to complicated :)
Isn't there a simpler way of doing it?

It's a one-line nmap command; how simple does it need to be?

Remember you asked to see the addresses of *all* the devices.  If you're looking for the equivalent of a Windows "Network Neighborhood" you won't find anything that meets the requirement of all devices.  NN only displays machines advertising Netbios names.  Routers, network-connected printers, etc., Linux servers, etc., won't show up in NN either.  nmap will list any machine with an IP address.

---

### Post by VanillaMozilla on 2010-11-22
Log in to your router?  It will share that information.

---

### Post by camorri on 2010-11-22
There is a gui front end for nmap called zenmap. Then you can select ping scan from the drop down, and key in the network you want to scan. 

Nmap for the most part requires root privileges. So use sudo zenmap to launch it.

---

### Post by SeijiSensei on 2010-11-22
> **camorri said:**
> Nmap for the most part requires root privileges. So use sudo zenmap to launch it.

Only if it's scanning ports.  I can run a ping scan as an ordinary user.

---

### Post by gregorydillon on 2010-11-30
If I could hop on your thread.   I've got a mixed network, two Ubuntu machines, a Windows 7, a WHS Server, and a networked printer.   On one of my Ubuntu machines, when I click Places, Network, it shows all the other machines that are turned on.   On the other Ubuntu machine, it does not show the names of the other machines, (although it does allow me to connect to the server)

I can't figure out what extra software, or settings I have on the machine that lists all the other computers, but I would like to.

---

### Post by MestreLion on 2012-02-11
> **SeijiSensei said:**
> Only if it's scanning ports.  I can run a ping scan as an ordinary user.

**No you can't**. -sP in nmap for non-root users does NOT send an ICMP echo (the "classic" ping). Instead, it send "pings" to ports 80 and 443, which will web servers will reply. So it's quite useless...

And that is not nmap's fault: the kernel only allows root users to send ICMP echo. The only reason a user can ping is because the binary /bin/ping is **setgid** , meaning it runs with root privileges even when invoked by a regular user.

---

### Post by Iowan on 2012-02-12
Thread closed.
From the Code of Conduct:
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

