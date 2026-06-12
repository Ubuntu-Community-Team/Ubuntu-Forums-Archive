---
title: "dns working, ping working, firefox/synptic NOT working"
date: 2006-01-08
forum: Networking &amp; Wireless
---

### Post by punchy on 2006-01-08
Hi,

I have a Ubuntu (breezy) PC and a laptop (just installed ubuntu breezy on it) behind a router attached to DSL modem.

the PCs internet connection is fine, has been for over a year..

the laptop is connecting, but firefox isn't building the www sites i point them to. it says waiting for "URL" at the bottom, but comes up with a 'the document contains no data' message..

... and synaptic isn't connecting to the repositories either

that is.. 'ping' works (with ipnr and urlname), 'host' works..  so the connection is there.. and dns is working as well.. 

ideas ?! :(

thanks!
Punchy

---

### Post by amohanty on 2006-01-08
Can you post the output of the following:

> traceroute -v google.com
 and
> wget [http://www.google.com](http://www.google.com)

AM

---

### Post by punchy on 2006-01-08
[QUOTE=amohanty]Can you post the output of the following:


 and


AM[/QUOTE]
thanks for the quick reply amohanty.

traceroute i don't have.. theres a traceroute6.. it says:
> traceroute6 -v google.com
traceroute: unknown host google.com

whereas wget does the following:
> wget [http://www.google.com](http://www.google.com)
--19:08:21--  [http://www.google.com/](http://www.google.com/)
           => `index.html'
Resolving [www.google.com](www.google.com)... 66.102.9.99, 66.102.9.104, 66.102.9.147
Connecting to www.google.com|66.102.9.99|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://www.google.de/](http://www.google.de/) [following]
--19:08:21--  [http://www.google.de/](http://www.google.de/)
           => `index.html'
Resolving [www.google.de](www.google.de)... 72.14.207.99, 72.14.207.104
Connecting to www.google.de|72.14.207.99|:80... connected.
HTTP request sent, awaiting response...


So it doesnt seem to connect. On my PC (same setup, behind same DSL router) this seems to work..

---

### Post by amohanty on 2006-01-08
It appears that your gateway might not be setup properly, because googles ip is being resolved, the dns if probably ok. 

Can you post the output of:
> ifconfig

AM

BTW what did you ping ? does ping work with an external host eg google

---

### Post by punchy on 2006-01-08
gladly:

i've pinged a couple of places.. google and [www.kde.org](www.kde.org) amongst them..

my gateway is the router, right ? 
the router is configured as 192.168.1.1

> lopez@punchi:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:B0:BD:9D:53
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:febd:9d53/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1320  Metric:1
          RX packets:172 errors:0 dropped:0 overruns:0 frame:139
          TX packets:150 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:21991 (21.4 KiB)  TX bytes:12444 (12.1 KiB)
          Interrupt:10

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7746 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7746 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:705643 (689.1 KiB)  TX bytes:705643 (689.1 KiB)

lopez@punchi:~$

---

### Post by amohanty on 2006-01-08
> traceroute i don't have..
try:
> sudo apt-get install traceroute and see if that works.

Also I am assuming you are running under dhcp.
Could you post the contents of your /etc/network/interfaces

Thanks.
AM

---

### Post by punchy on 2006-01-08
[QUOTE=amohanty]try:
 and see if that works.

Also I am assuming you are running under dhcp.
Could you post the contents of your /etc/network/interfaces

Thanks.
AM[/QUOTE]

my /etc/network/interfaces file:
> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp


and on the subject of my gateway, i ran 'route -n', giving:
> Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

thats what i get with the working pc as well..


apt-get install doesnt work.. due to the problem we're talking about ... :(

---

### Post by amohanty on 2006-01-08
Can you add the following to the end of your /etc/network/interfaces

> auto eth0

then restart networking:

> sudo /etc/init.d/networking restart

HTH

---

### Post by punchy on 2006-01-08
done it..

no change !

](*,)

(btw. the laptop is dualboot.. everything works fine with windows home xp)

---

### Post by amohanty on 2006-01-08
Does a reboot work?

---

### Post by punchy on 2006-01-08
[QUOTE=amohanty]Does a reboot work?[/QUOTE]

nope...

argl.

(thanks for your time)

---

### Post by amohanty on 2006-01-08
Ok try this:
1. Turn off machine, router, dsl modem (pull power cable)
2. boot them on in reverse order waiting 30s between all three boots - dsl modem, router, machine.
3. Try hitting the router via firefox from the problem machine.
[http://192.168.1.1](http://192.168.1.1)

Also check the list of connected hosts listed in the router to make sure that it is not retaining the XP dhcp lease.

Post the results of this.

AM

---

### Post by punchy on 2006-01-08
[QUOTE=amohanty]Ok try this:
1. Turn off machine, router, dsl modem (pull power cable)
2. boot them on in reverse order waiting 30s between all three boots - dsl modem, router, machine.
3. Try hitting the router via firefox from the problem machine.
[http://192.168.1.1](http://192.168.1.1)

Also check the list of connected hosts listed in the router to make sure that it is not retaining the XP dhcp lease.

Post the results of this.

AM[/QUOTE]

i did what you said.

no difference, really. except that, interestingly, the router won't show up in firefox of the problem machine either..("document contains no data"). the lease on th same laptop, but when running with xp, is definitely not there anymore..

the packetnrs being sent and received are really low, too.. the count is below 100 for both, in contrast to the 30000 or so with the 'healthy' pc

---

### Post by amohanty on 2006-01-08
> no difference, really. except that, interestingly, the router won't show up in firefox 

That is strange. Its should be able to get to its router and gateway, no matter what. 
Can you ping and wget the router?

AM

---

### Post by punchy on 2006-01-08
[QUOTE=amohanty]That is strange. Its should be able to get to its router and gateway, no matter what. 
Can you ping and wget the router?

AM[/QUOTE]

ping works fine (as it does for google)

the wget output from the problem machine is the same as from the healthy one, which i assume is normal (?) :
> 
lopez@punch:~$wget 192.168.1.1
--20:38:17--  [http://192.168.1.1/](http://192.168.1.1/)
           => `index.html.1'
Connecting to 192.168.1.1:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.


---

### Post by mips on 2006-01-08
[http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)

Disable IPv6 and see what happens.
Manually configure DNS and see what happens.

---

### Post by punchy on 2006-01-08
[QUOTE=mips][http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)

Disable IPv6 and see what happens.
Manually configure DNS and see what happens.[/QUOTE]

hi mips, thanks for the attention,

well.. heres one glitch which seperates my healthy machine from this sick one. this output indicates an error.. no idea which, though..:
> lopez@punch:~$mii-tool eth0
SIOCGMIIPHY on 'eth0' failed: Operation not permitted


the newer command 'ethtool eth0' gives me:
> Settings for eth0:
        Supported ports: [ MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Half
        Port: Twisted Pair
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: d
        Current message level: 0x000000ff (255)
        Link detected: yes



changed from dhcp to static ip.. told router to give it this ip (to mac adress) no difference !

also: i cannot find any way to turn off the IPv6 protocoll in my router..

i've changed the firefox config in 'about:config', line 'network.dns.disableIPv6' to true.. and commented out the line

alias net-pf-10 ipv6

in /etc/modprobe/aliases

.. but none of that helped..

---

### Post by mips on 2006-01-08
Have you manually added your DNS servers to /etc/resolv.conf and removed whatever was there before.

What brand&model router do you have ?

---

### Post by punchy on 2006-01-08
[QUOTE=mips]Have you manually added your DNS servers to /etc/resolv.conf and removed whatever was there before.[/QUOTE]

the ip pf the router was there (192.168.1.1)
i removed it and added two dns servers i use at work (physics, university). still no difference.. which didn't surprise me, as the command 'host' works.. and ping works equally with the URL name and the 'raw' ipnr.

[QUOTE=mips]What brand&model router do you have ?[/QUOTE]
uhm... dsl T-teledat-331 LAN (Telecom)
i'd be surprised if that as it. i have a PC (breezy) running, with -as far as i can make out- the same setup. and it works fine.

my laptop has a NetXtreme Gigabit Ethernet Controller.. anybody know anything about it ?

---

### Post by lestat on 2006-01-08
HI there Guys and Girls,

I just installed Ubuntu 5.10 on my laptop and I have sort of a similar problem. Ubuntu recognizes the LAN connection and I can easily connect to the intranet which is the school network.However, since the ISP is an external company, for some reason I am not able to connect to internet sites like yahoo or google, immediately.
The internet connection does work,after say 10 mins of waiting.
I tried pinging the yahoo web site while I couldnt connect using firefox, and packets were sent and received perfectly fine.
I really do not know what the problem is and have tried to find similar solutions in the frums but in vain.
Thanks in anticipation.

Lestat

---

### Post by LightShear on 2006-01-08
Just a thought, and you probably tried it already, but in System > Administration >  Networking, click eth0 and view it's properties. DHCP is enabled, right?

Punchy,
/etc/resolv.conf has the correct domain server information that's on the router, right? You can usually view this in the status screen of your router.
> search DOMAIN NAME
nameserver DNS 1
nameserver DNS 2

*Substitute domain name and the dns's so it matches what's on the router.*

letstat,
Post what is in "/etc/network/interfaces" and "/etc/resolv.conf"

---

### Post by amohanty on 2006-01-08
Possibly completely OT but just wanted to know:
1. Do you have dynamic address allocation from your ISP or do you have a static IP?
2. If you do have a dynamic IP(s) do you have the same number of dynamic IPs as machines, because certain ISPs block based on port numbers assigned via NAT to determine how many machines are connected (I know its stupid but mine does so I know it happens, usually only for PPPoE based connections)

AM

---

### Post by lestat on 2006-01-08
This is from /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp

auto eth0

This is the /etc/resolv.conf

search apogeetelecom.com
nameserver 209.51.64.250
nameserver 209.51.64.242

Thanks for the help.

Lestat

---

### Post by dcstar on 2006-01-08
You may want to test if both UDP and TCP DNS requests work from your system:

"dig domain_name" should use UDP for the lookup;

"dig +tcp domain_name" should use a TCP query.

If either pauses then there may be port blocking somewhere in the path to the DNS server.

---

### Post by dcstar on 2006-01-08
As well, the people with problems may want to check their /etc/hosts file to ensure that their 127.0.0.1 entry matches their system name.

---

### Post by lestat on 2006-01-08
I think you might have gotten me wrong.The internet works perfectly fine right now but my problem is the time it takes to get working.
I dont know what is causing it to spend so much time trying to connect to internet servers. The intranet connection to my campus web sites work perfectly fine from the start.

Lestat

---

### Post by punchy on 2006-01-09
Hi,

Well.. everything works now.

Today, I took the laptop in to work and connected it to the net there. I proceeded to update everything..

I am now at home and the connecton works. The only difference to yesterday is that I explicitly wrote my nameservers into the network configuration (I had done this before, actually, to no avail), and that I told my router to assign the mac number of the laptop a static ip (192.168.1.3). I hadn't done that before.

I like it more when I know my ipnr anyway...

mips and amohanty and dcstar, I'm grateful for your time. 

Hope you find a solution, lestat.

Punchy the well connected

---

