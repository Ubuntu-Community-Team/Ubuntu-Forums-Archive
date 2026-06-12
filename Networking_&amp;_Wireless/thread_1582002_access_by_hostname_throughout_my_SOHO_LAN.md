---
title: "access by hostname throughout my SOHO LAN"
date: 2010-09-25
forum: Networking &amp; Wireless
---

### Post by SaintDanBert on 2010-09-25
I have a wired and wireless LAN inside my home. It runs my family and my small business. Like most folks, I use one of the RFC-1918 [http://www.faqs.org/rfcs/rfc1918.html](http://www.faqs.org/rfcs/rfc1918.html) private networks on this LAN.  My gateway hands out IP addresses to everyone who connects -- wired or wireless.

[highlight]Q1:[/highlight] What sort of configuration do I need to implement so that computers can access each other **by name** while inside the LAN?  I hope that my linux hosts work and that both win-doze and mac-aroni can cooperate.

What sort of cooperation am I looking for?
[list]
[*]linux publish and connect to NFS or similar resources
[*]everyone connect and interact with LAMP where ever I might want it
[*]enough SAMBA everywhere to be useful
[*]everyone can print to whichever printers exist somewhere
[*]everyone can find and access "network" drives (NAS, SAN, etc)
[/list]

This sounds like I need my own name server. I've no idea how to do that when everyone gets a changing DHCP ip address.

I can use a workstation MAC (hardware) address and config my gateway to give the same address to that MAC each time it connects.
[highlight]Q2:[/highlight] What do I do so that visitors can find named resources on the LAN?  I don't want to config a MAC address and IP mapping for any random visitor.
[highlight]Q3:[/highlight] What do folks do with phones and PDAs that can wifi?

Merci d'avance,
~~~ 0;-Dan

If this is answered somewhere already, I couldn't find it. I don't know enough to ask the right search questions.

---

### Post by mrhhug on 2010-09-25
sounds like your doing enough to justify a dedicated server, i would definitely use one if i was installing LAMP.

in your router it should allow you to setup a static IP, once you get the server installed with ubuntu server edition. have your router give a static IP to the server. - the rest can still use dynamic ips.

you can install all your scanners and printers to this server and file share easily using SAMBA. setup the server to give each user their own folder then map that folder on their personal desktop.

win linux and apples will all work nice with samba

---

### Post by lukeiamyourfather on 2010-09-25
In a typical home network the gateway (usually an off the shelf router) is also the name server. What kind of gateway are you using? If that isn't working or the gateway doesn't have a name server, you could use static IP addresses and modify the host file on each machine so they know where the other machines are by name.

---

### Post by mrhhug on 2010-09-25
im just using a cheapo netgear N router, it does everything i need - using virtual server and port forwarding, my server hosts my personal webpage listed at the bottom of my posts, its also hosts a few professional web sites.

my small network is setup so that everyone can get to my samba shares on  server. that why every time someone brings over a new laptop their getting a dynamic IP but they can always find 192.168.10.197.... the only IP that matters is the server's IP all other nodes can upload to X space on server that way its easy to share everything i need - as long as i give them the WPA password

to get more security i could set all the users that are allowed to hit server and all that, but i feel the WPA2 password is sufficient

---

### Post by SeijiSensei on 2010-09-25
The simplest solution is to add your IP and hostname to the "[hosts]("http://en.wikipedia.org/wiki/Hosts_%28file%29#Location_in_the_file_system")" file in Linux and Windows.  Of course, if you have lots of visitors, you can't really expect to edit each and every person's hosts file, so you probably should consider implementing DNS on the server.

If you're running the Server Edition of Ubuntu, you'll have the BIND nameserver already up and running.  If not, you'll need to install it using 'sudo apt-get install bind9' at a prompt.

The configurations are stored in /etc/bind; the server binary itself is called "named".  When named starts up, it reads named.conf in the /etc/bind directory.  In Ubuntu, that file contains a bunch of "include" statements that load separate files to configure a bare-bones local nameserver.  You'll probably want to put your definitions in a separate file and add it with an "include /etc/bind/hugfails.conf;" statement like the others in named.conf.

Next, create /etc/bind/hugfails.conf and enter the code to load your "zone" file:

```

zone "hugfails.com" {
    type master;
    file "/etc/bind/hugfails.com";
};

```

Be careful to include all the semicolons; named is very picky about syntax.

Now you need to define the "zone" file itself which I called "/etc/bind/hugfails.com" above.  This is a fairly complicated file.  It contains an "SOA" record that defines the domain, plus "A" records that map from hostnames to IP addresses, "NS" records that point to your nameserver(s), "MX" records that tell servers where to send mail for your domain, and perhaps "CNAME" records that alias one machine's name to another.  A quick Google search for 'example bind zone file' brings up a lot of helpful references.

You probably don't need to keep your zone information in sync with the addresses your router hands out.  It sounds like the important task is to allow people to access your local server with a hostname rather than an IP address.  If you find you need to create a complete census of the local machines, send me a PM, and I'll send you a bash script I wrote which polls the network and builds the zone file automatically.  (It also builds a file for the "reverse" zone that maps from IP addresses back to host names.)

When I first started doing system adminstration, I found [this book](http://oreilly.com/catalog/9780596002978/) an invaluable resource.  Today there are many free guides to network administration including the [Ubuntu Server Guide](https://help.ubuntu.com/10.04/serverguide/C/index.html) which you can consult.

When you're all done, you should be able to type commands like:

host mylocalserver.hugfails.com 127.0.0.1

on the server and get the correct address for mylocalserver.  It should also work if you replace 127.0.0.1 with the IP address of your server, 192.168.10.197, or replace "mylocalserver.hugfails.com" with an external hostname like "www.google.com".  

If everything works as expected, edit the DHCP configuration on your router so that it hands out the server's IP address as the primary nameserver.  I'd include your ISPs DNS server(s) as secondaries in case something goes wrong with your server.

---

### Post by SaintDanBert on 2010-09-26
is there some way:
[list]
[*]DHCP hands out an IP address
[*]some magic happens
[list]
[*]DHCP (or something) tells some utility the IP address
[*]the utility somehow invents a a {hostname}
[*]the utility tells the host about the invented name
and shares that name with other parts of the LAN
[/list]
[*]DNS learns a {name} and {IP} pair
[/list]

Stumbling,
~~~ 0;-/ Dan

---

### Post by mrhhug on 2010-09-26
> **SaintDanBert said:**
> is there some way:
[list]
[*]DHCP hands out an IP address
[*]some magic happens
[list]
[*]DHCP (or something) tells some utility the IP address
[*]the utility somehow invents a a {hostname}
[*]the utility tells the host about the invented name
and shares that name with other parts of the LAN
[/list]
[*]DNS learns a {name} and {IP} pair
[/list]

Stumbling,
~~~ 0;-/ Dan

im sooo comfy telling people 192.168.10.197 rather than "server64crosscreekdr"those names are just aliases anyway.... internet is numbers, not english .... your more than welcome to use bind and aliases on you network, but i personally feel you are overcomplicating things, just remember the static IP you assigned

SeijiSensei 's input was very very good. he is a master of tcp/ip obviously 
im just not sure why you are obsessed with naming things, just use the IP; when you use a name it get converted to binary anyway .... use the static ip - you'll skip like 25 steps

---

### Post by SeijiSensei on 2010-09-26
> **SaintDanBert said:**
> is there some way:
[list]
[*]DHCP hands out an IP address
[*]some magic happens
[*]DNS learns a {name} and {IP} pair
[/list]

[I believe there is]("http://www.debianadmin.com/howto-setup-dhcp-server-and-dynamic-dns-with-bind-in-debian.html") if you're running BIND and ISC DHCP on the same server.  This would mean making your server the source of DHCP addresses rather than your router.   

I'd agree with mrhhug, though.  If all you're trying to do is enable people to reach your server via a hostname instead of an IP address, either use hosts files, or just use the address.  DNS is way overkill just to name a single machine.

---

### Post by SaintDanBert on 2010-09-26
While reaching "server resources" is a central part of my objectives, I also want folks to access resources that are scattered among the workstations.

One example: I have a desktop wiki on MY laptop.  I routinely work with some other workstation. I'd like to reach out to that wiki to make some notes -- by name.  Yes,  the static-IP thing might work.  Sadly, I've had poor luck with getting static-IP installed and working. I will revisit that effort. Can someone recommend a good HOWTO?

~~~ 0;-Dan

---

### Post by lukeiamyourfather on 2010-09-26
> **SaintDanBert said:**
> I'd like to reach out to that wiki to make some notes -- by name.  Yes,  the static-IP thing might work.  Sadly, I've had poor luck with getting static-IP installed and working.

For configuring the network with static IP addresses see this.

[https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html](https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html)

Back to my first question if you're still interested in using a name server to access machines by host name, what gateway are you using? Is this an off the shelf router, a dedicated Linux machine, something else?

---

### Post by SaintDanBert on 2010-09-27
I'm using a Netgear WNDR3700 -- wire, wifi, router, switch, "usb server".

I used to be able to config DNS details for the gateway DHCP to hand out
with any IP address. Everyone seems to have moved away from that configuration feature.

One difficulty with static IP involves times when I go walk-about. In those cases, I don't want my static but whatever the public access doles out. I keep hoping that I'll learn to manage that someday.

~~~ 0;-Dan

---

### Post by SeijiSensei on 2010-09-27
> **SaintDanBert said:**
> I'm using a Netgear WNDR3700 -- wire, wifi, router, switch, "usb server".

I used to be able to config DNS details for the gateway DHCP to hand out
with any IP address. Everyone seems to have moved away from that configuration feature.

One difficulty with static IP involves times when I go walk-about. In those cases, I don't want my static but whatever the public access doles out. I keep hoping that I'll learn to manage that someday.

~~~ 0;-Dan

Most routers like yours don't provide any DNS services of their own.  In cases where the router presents itself as the DNS server, it's usually just forwarding requests to the ISP's DNS server that it discovers while connecting to the external network.  However, if you have a preferred DNS server, like one running inside the local network, you can usually configure the DHCP server on the router to give that address to the clients instead.  Are you telling us that the Netgear doesn't have that option?  If so, you might consider providing DHCP services on your Linux server instead.

As for the "walk-about" problem, you'll need to look into virtual private networking for that.  OpenVPN is pretty easy to set up and use.

---

### Post by lukeiamyourfather on 2010-09-27
> **SaintDanBert said:**
> I'm using a Netgear WNDR3700 -- wire, wifi, router, switch, "usb server".


This should work. No need to run a DNS on a Linux machine, the router has a DNS already.

[http://kb.netgear.com/app/products/model/a_id/11640](http://kb.netgear.com/app/products/model/a_id/11640)
[http://kb.netgear.com/app/answers/detail/a_id/64](http://kb.netgear.com/app/answers/detail/a_id/64)

---

