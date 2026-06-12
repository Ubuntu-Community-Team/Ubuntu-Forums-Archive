---
title: "How do I create a networking bridge between a wireless and wired network?"
date: 2006-01-01
forum: Networking &amp; Wireless
---

### Post by daller on 2006-01-01
Hi There,

I have a laptop with integrated wireless (eth1), it also has a wired network (eth0)

I also have a desktop pc with wired network (eth0) - the two wired network cards is connected with a cable!

How do I setup the laptop to bridge it's eth1 and eth0, so that I can get internet og my desktop? (DHCP)

I've tried firestarter, but can't get it to work! (Is there a KDE alternative?)

---

### Post by cwaldbieser on 2006-01-01
[QUOTE=daller]Hi There,

I have a laptop with integrated wireless (eth1), it also has a wired network (eth0)

I also have a desktop pc with wired network (eth0) - the two wired network cards is connected with a cable!

How do I setup the laptop to bridge it's eth1 and eth0, so that I can get internet og my desktop? (DHCP)

I've tried firestarter, but can't get it to work! (Is there a KDE alternative?)[/QUOTE]

Are the two wired cards connected with a normal cable or a crossover cable?  Also, what is your gateway to the Internet?  Do you have a wireless router?

---

### Post by daller on 2006-01-01
[QUOTE=cwaldbieser]Are the two wired cards connected with a normal cable or a crossover cable?  Also, what is your gateway to the Internet?  Do you have a wireless router?[/QUOTE]

 I have a wireless router!

The gateway is: 83.72.96.1

I use a crossover cable!

---

### Post by cwaldbieser on 2006-01-02
[QUOTE=daller]I have a wireless router!

The gateway is: 83.72.96.1

I use a crossover cable![/QUOTE]
When you tried to use Firestarter, can you explain what didn't work?

Also, could you post the output of the following commands from *both* your PCs (laptop and desktop)?
```

$ ifconfig
$ route

```
These show you network card configurations and routing table information, respectively.

---

### Post by az on 2006-01-02
[QUOTE=cwaldbieser]can you explain what didn't work?

[/QUOTE]


:)

The kde equivalent to firestarter is guarddog and guidedog.
Gueaddog is the firewall and Guidedog is the networking thing.

---

### Post by Lambert on 2006-01-02
Not 100% sure as I haven't done this set up but these are things I believe you need to do.

1. Make sure you have different subnets for the two nics on the laptop 

wireless 192.168.0.x
wired 192.168.1.x

2. Turn on ipforwarding.

Open /etc/sysctl.conf and you should see this line (or add it). It should look just like this.

# Uncomment the next line to enable packet forwarding for IPv4
net/ipv4/ip_forward=1

3. on the desktop make sure the gateway points to the ip address of the wired nic on the laptop. If it's ubuntu then here are the steps on the desktop.

```
sudo ifconfig eth0 192.168.1.3
```
(this brings up device and assigns it an ip of .1.3)
```
sudo route add default gw 192.168.1.2 dev eth0
```

(in the route command I assume you set the ip address of the wired nic on the laptop as .1.2)

4. The last step  I'm not sure about  but you may have to set up dns nameservers.

If I'm off base or missing something, someone else add to or correct me.

---

### Post by daller on 2006-01-02
I'd like to have the laptop work just like a router with DHCP!

Your solution looks nice, but it doesn't offer DHCP! (I has to offer DHCP, since the connect computers are computers for installation of ubuntu, etc...)

It would be nice if firestarter just did it all! (I mean, you tell it which interface has internet-connection, and which has client-machines connected. - That's all the computer needs to know, isn't it?)

Firestarter has a DHCP-option, but it still complains about eth0 (the wired NIC - where the clients are to be connected!)

Starting firestarter from terminal, I get:

```
Internal network device eth0 is not ready. Aborting..
```

"Local network connected device" should be "eth0" in my case, right?

---

### Post by Lambert on 2006-01-02
Yes, I provided static ip setting, (missed the dhcp part) so if you want the laptop to serve as a dhcp server look into the package dhcp3-server.

---

### Post by cwaldbieser on 2006-01-02
[QUOTE=daller]I'd like to have the laptop work just like a router with DHCP!

Your solution looks nice, but it doesn't offer DHCP! (I has to offer DHCP, since the connect computers are computers for installation of ubuntu, etc...)
[/QUOTE]
I'm not sure I follow this reasoning.  For most home or simple office networks, assigning static IP addresses tends to be a lot simpler to set up.  Otherwise, you have to configure a DHCP server, as Lambert suggested.

---

### Post by mips on 2006-01-03
daller,

Have a look at [http://ubuntuforums.org/showthread.php?t=89320](http://ubuntuforums.org/showthread.php?t=89320)

it will do everything you want to do + more ;) just scratch around in there.

---

