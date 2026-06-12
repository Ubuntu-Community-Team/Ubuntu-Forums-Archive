---
title: "Two NIC problem: eth0 intranet, eth1 internet"
date: 2009-11-11
forum: Networking &amp; Wireless
---

### Post by vmajor on 2009-11-11
Hi,

this has caused me two days of near insomnia, so I apologize in aedvance if the message does not make all the sense it should.

After installing eth1, eth0 is no longer reachable from the ineternet.

OS: Ubuntu 8.10

interfaces:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo eth0 eth1
iface lo inet loopback

# The primary network interface
iface eth0 inet static
        address 192.168.1.191
        netmask 255.255.255.0
        gateway 192.168.1.254
        network 192.168.1.0

iface eth1 inet static
        address 61.xxx.xxx.183
        netmask 255.255.255.0
        gateway 61.xxx.xxx.254
        broadcast 61.xxx.xxx.255
        network 61.xxx.xxx.0

```

route -n output

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
61.xxx.xxx.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 vnet0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         61.xxx.xxx.254  0.0.0.0         UG    100    0        0 eth1
0.0.0.0         192.168.1.254   0.0.0.0         UG    100    0        0 eth0
```

This is the setup and the reasons for it.

**eth0 191.168.1.191** runs behind Vyatta router/firewall/nat and our erp, web, ssh and ftp servers are being served from 191.168.1.191 through eth0. Vyatta is connected to the internet via a static IP 61.xxx.xxx.185

**eth1 61.xxx.xxx.183** is used to connect directly to the static IP ISP to allow us to run bind and have our domain visible on the internet. eth1 will be completely firewalled allowing only bind related traffic.

Current status:

eth1 works well now. It is reachable both from the internet and from the intranet.

eth0 does not work well at all. It is reachable only from the local addresses. None of the servers are reachable from the internet. We had no problems reaching eth0 from the internet before I installed the eth1 NIC. Vyatta has been eliminated as a possible reason for this eth0 malfunction.

I am lost, tired and confused. Please help. 

Cheers,

V.

---

### Post by scorp123 on 2009-11-11
Works as designed. Please read **RFC1918** ... and the bit about private range addresses (10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16 ...) not being routed / routable on the internet.

You have two interfaces now. Hence if you want anything on the 192.168.x.x network to be visible on the Internet side you have to configure your firewall, adapt/adjust your routing and your NAT rules. Or else this will not work ... exactly as the TCP/IP standard intends.

---

### Post by scorp123 on 2009-11-11
> **vmajor said:**
> 
# The primary network interface
iface eth0 inet static
        address 192.168.1.191
        netmask 255.255.255.0
        gateway 192.168.1.254
        network 192.168.1.0 

... snip ...

> **vmajor said:**
> 
**eth0 191.168.1.191** runs behind Vyatta router/firewall/nat 

Up there it's **19[COLOR="Red"]2[/COLOR]**.168.1.191 and now you all of a sudden talk about **19[COLOR="Red"]1[/COLOR]**.168.1.191 .... You're sure about this?

According to whois the 191.168.0.0 range belongs to an IP registrar in Montevideo, Uruguay.

So either this was a typo and you in fact meant the RFC1918 private range address 192.168.1.191  ... or you should stop using IP addresses that do not belong to you.

---

### Post by t0mppa on 2009-11-11
@scorp123: Of course it works as designed, we're not talking about bugs here. The issue clearly is that the user asking the question doesn't know how to properly tell the system what he wants it to do and simply replying: "It's doing just what you asked it to." is not helpful in any way and thus a totally irrelevant reply, no matter how many standards you quote.

@vmajor: The problem is having two default gateways in one routing table. That simply doesn't work. It's like if you were giving your friend driving instructions and said something like: "Go straight unless I tell you to turn, ..., oh and keep turning left if I don't specify anything else." How does he know what to do, when you don't say anything? He can pick either one, but not both. Same applies to your two gateways, the traffic can't be routed into two different routes simultaneously.

So, you will need to give the system some instructions on how to do the routing. Basically you can tell it to reply through eth0 for packages that came in through eth0 and vice versa for eth1 and then pick up either interface as the default gateway for outgoing packets that are not replies to earlier contacts, which sounds to me to be the solution you're looking for.

To do that, you'll need to create two more routing tables. That can be accomplished by editing */etc/iproute2/rt_tables* and adding in two lines, for example:```
201     Vyatta
200     bind
```

After that you need to add the routes in their individual tables with:```
sudo ip route add 192.168.1.0/24 dev eth0 src 192.168.1.191 table Vyatta
sudo ip route add default via 192.168.1.254 dev eht0 table Vyatta
sudo ip route add 61.xxx.xxx.0/24 dev eth1 src 61.xxx.xxx.183 table bind
sudo ip route add default via 61.xxx.xxx.254 dev eth1 table bind
```

Then add in the rules to make sure that replies to traffic coming in from either route will be using the routes we defined for its subnet above:```
sudo ip rule add from 192.168.1.191 table Vyatta
sudo ip rule add from 61.xxx.xxx.183 table bind
```

The rules above are the part that is failing in your current configuration, when the answers to traffic coming from eth0 get pushed to the default gateway of eth1, the other end trying to contact the servers doesn't recognize the IP from which the replies come from.

Finally kill either one of your current default rules in the main table to specify which interface to use for outgoing traffic generated by this machine or you can even add load balancing between the two gateways, but that's beyond the scope of your original problem.

P.S. Note that you may have to use **ip route flush cache** to update the cache to start using your new routes and rules now and not when it's appropriate for the system to do its next update.

---

### Post by vmajor on 2009-11-11
Hi scorp,

I am indeed talking about 192. 191 is a typo.

Why are you thinking that I want to route 192.x.x.x on the internet? 

Is it something in the interface settings that makes you think that?

Just to clarify:

eth0: inTRAnet behind Vyatta router [http://www.vyatta.org](http://www.vyatta.org) that handles the inTRAnet and provides access to and from the inTERnet via a fixed IP at the ISP (we have a pool of 6 fixed IPs)

eth1: inTERnet direct connection to fixed IP at the ISP

Alas, as per my original post, there is no longer any server response to any requests coming in to eth0 via Vyatta from the internet. This worked well before I installed the second NIC for eth1.

Intranet requests are fine. For example httpd responds to 192.168.1.191, but not to the Vyatta managed 61.x.x.185 internet address. 

Httpd does respond to the eth1 direct IP 61.x.x.183, but that is just for testing since as I said the only reason why there is an eth1 now is so that we can run bind9, thus all non DNS related ports on eth1 will be blocked.

Cheers,

V.

---

### Post by scorp123 on 2009-11-11
> **t0mppa said:**
>  The issue clearly is that the user asking the question doesn't know how  Apparently you're underestimating OP's level of knowledge ... something which I tried to avoid. If OP didn't understand what I meant they can still ask and we can still elaborate on the topics at hand. Capisce?

---

### Post by vmajor on 2009-11-11
@t0mppa. Wow. Thank you for the extremely informative reply! I hope that it resolves my issue.

Owing to my undiscolsed level of newbness and my lack of sleep, can you please take me through by what you meant with: 

> Finally kill either one of your current default rules in the main table to specify which interface to use for outgoing traffic generated by this machine or you can even add load balancing between the two gateways, but that's beyond the scope of your original problem.

Tomorrow, when I wake up from my long delayed slumber I will most likely cringe at my naïve and superflous question, but just in case I am not granted clarity of thought even then, could you give me an example of how that is done.

Right now all of the ip route commands have been executed and route cache has been flushed. 61.xxx.xxx.183 talks to the internet, 61.xxx.xxx.185 still does not.

I am at a complete loss when it comes to routing and interfaces. Setting up Vyatta was a painful experience, but that was also made possible due to the helpful people like you.

Cheers,

V.

---

### Post by scorp123 on 2009-11-11
> **vmajor said:**
>  I am indeed talking about 192. 191 is a typo.  Good. Just to be sure. I have seen people make up IP addresses (e.g. 129.0.0.0) and then wondering why so many strange things happen ...

> **vmajor said:**
>  Why are you thinking that I want to route 192.x.x.x on the internet?  You said you wanted to access something that's behind the 192.168.0.0/16 network from the Internet side. You can't do that unless you have NAT in place. Direct access is impossible. Or maybe I was reading too quick and I misunderstood your intentions?

> **vmajor said:**
> 
This worked well before I installed the second NIC for eth1.
So if I understand correctly ... Your schematics look like this:

Intranet => eth0 => server => eth1 => Vyatta router => WWW

?

---

### Post by vmajor on 2009-11-11
@scorp123

The schemas are actually separate:

1. Internet (61.xxx.xxx.185) => Intranet (Vyatta 192.168.1.254) => eth0 (192.168.1.191) => server (httpd, erp, ssh, ftp)

2. Internet (61.xxx.xxx.183) => eth1 => server (dns)

I do not want schema 1 and 2 to talk to each other, I want both of them to work separately and I want both of them to be accessible from the internet.

At the moment only schema 2 is accessible from the internet.

Cheers,

V.

---

### Post by t0mppa on 2009-11-11
> **scorp123 said:**
> Apparently you're underestimating OP's level of knowledge ... something which I tried to avoid. If OP didn't understand what I meant they can still ask and we can still elaborate on the topics at hand. Capisce?

Well, the way I saw it, OP asked the following question: "I had a working setup with interface A, which stopped working after I installed interface B, what's wrong?" Since he had managed to route the server on the intranet perfectly fine to Internet earlier, why should RFC1918 suddenly become relevant?

> **vmajor said:**
> Owing to my undiscolsed level of newbness and my lack of sleep, can you please take me through by what you meant with: 

> Finally kill either one of your current default rules in the main table to specify which interface to use for outgoing traffic generated by this machine or you can even add load balancing between the two gateways, but that's beyond the scope of your original problem.

Tomorrow, when I wake up from my long delayed slumber I will most likely cringe at my naïve and superflous question, but just in case I am not granted clarity of thought even then, could you give me an example of how that is done.

It just means that since you can't have two default gateways in one table, you need to remove one of them. And it's up to you which one you remove. This gateway in the main routing table only applies to traffic that is originally created at your system, i.e., if you login and browse the net from it for instance. Everything that is an answer to an outside device connecting to the system should get handled by the other two tables, if we got the rules set up properly.

---

### Post by scorp123 on 2009-11-11
> **vmajor said:**
>  Vyatta has been eliminated as a possible reason for this eth0 malfunction. 

Are you sure it's not a NAT issue? Because:
```
1. Internet (61.xxx.xxx.185) => Intranet (Vyatta 192.168.1.254) => eth0 (192.168.1.191) => server (httpd, erp, ssh, ftp)
```

In that case the Vyatta router would have to translate any incoming requests on 61.xxx.xxx.185 to the eth0 (192.168.1.191) address.

So the NAT/PAT rules should look something like this:

61.xxx.xxx.185:80 => 192.168.1.191:80
61.xxx.xxx.185:443 => 192.168.1.191:443
61.xxx.xxx.185:22 => 192.168.1.191:22
61.xxx.xxx.185:21 => 192.168.1.191:21
61.xxx.xxx.185:8080 (or whatever your ERP is using) => 192.168.1.191:8080


You are sure that NAT/PAT is properly configured? e.g. you did not forget to adjust the rules when you added the additional interface?

Sorry if I am slow ... it's early morning here and I can't sleep despite being tired like hell ...

---

### Post by vmajor on 2009-11-11
@scorp123

heh, I know all about tired...

No, it is not a NAT issue since the eth1 is not plugged into the Vyatta managed network. It connects directly to one of the ports on the ADSL modem (fixed IP).

Besides, the Vyatta managed NAT worked flawlessly until I installed the eth1 NIC.

V.

---

### Post by vmajor on 2009-11-11
@t0mppa

It works! You fixed it. Thank you.

I redid all the commands you gave me and deleted one of the original "default" settings, flushed the cache and we are alive!

...now, are these settings persistant, will they survive a reboot?

Cheers,

V.

---

### Post by t0mppa on 2009-11-12
The tables naturally are persistent, since the file was edited. The rest you can put into your */etc/network/interfaces* file or then just write a script for them, if that feels better.

For the former, you can use the pre-up, up, post-up, pre-down, down and post-down options followed by the command to execute for setting the routing up. For instance if eth0 was your primary interface and eth1 only got used from time to time, you could append the eth1 configuration to add all the extra routes and rules on up and then remove them on down. If they're both always used, it naturally doesn't matter which interface you associate the creation of the routes and rules with.

---

### Post by vmajor on 2009-11-21
UPDATE: I rebooted yesterday and the new routing tables were not persistent.

I had to redo the setup to regain the functionality.

I will now need to look at the extra scripts...feel free to suggest what needs to be done where :D

V.

---

### Post by t0mppa on 2009-11-22
Did you add them into the interfaces file? That way you'd have all the configuration in one file. Of course, can always create an external script out of those commands and just have it executed at boot with the help of *update-rc.d* or then simply add the necessary lines into */etc/rc.local* before the *exit 0* line.

They all get the job done, just in different ways. Should pick the option which stores the lines in a place where you'll find them later.

---

