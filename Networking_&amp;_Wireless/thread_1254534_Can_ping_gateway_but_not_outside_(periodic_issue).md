---
title: "Can ping gateway but not outside (periodic issue)"
date: 2009-08-31
forum: Networking &amp; Wireless
---

### Post by SeekerDK on 2009-08-31
[quote="[COLOR=Red]Information update[/COLOR]"]
Update 09/09/09 :)
ndiswrapper DIES. How do I troubleshoot?
Any and all (relevant *gg*) suggestions and/or link are most welcome.

Update "last week"
Allright, so I've done a great job on spamming my own thread with conflicting information. Bottom line is, RIGHT now, the server has inet connection, BUT I expect it to break again sometime soon. I have no idea what so ever, on what can cause this behavior, but the problem is as such:
Routing (inet connection through the gateway) dies at some point AFTER the machine is booted.
Setting a continues ping seems to solve the problem. Don't know how or why, but so far it seems to keep the connection alive (indefinitely?). 

When dead, I have not found any other way to get it back in working order, then to reboot the server. 
I've haven't check a lot of logs, as I actually don't know in which logs to look for what (suggestions?)
**[COLOR=Red]This textbox will be removed only when the problem is confirmed fixed. Until then, consider the case unsolved[/COLOR]**
[/quote]

Here is a real head scratcher :-k

I install Jaunty 64 server on a IBM 3650 server - LAMP, Virtuallization, DNS, SSH.
Dual NIC, both connected, one static, one DHCP.

All of a sudden, the Inet connection breaks, but I can still ping the gateway and the server still reponds (slowly) to ssh terminals on both IPs. 

I reboot, and voila, inet is back, I install upgrades (apt-get upgrade) it crashes midway, same problem. 
I reboot, back online, finish upgrades, finishes, inet dies 
I reboot (beginning toi sound like Microsoft, isn't it :P) restart /etc/init.d/networking, inet goes away again... 
At some point it looked like it was only when it updated or messed with the netconf is died, but it happened later, when I had just been using ssh and ssh -X.

I try investigating resolv.conf, interfaces configuration and checks routes with netstat -nr and I simply can't find anything wrong. The one hint that I have, is that SSH responds really slow, when the inet creashes, which could point towards a DNS issue, so I installed bind. On the other hand, I can't even ping IPs outside the subnet, so that pretty much elminates a DNS issue, so my guess is that some route/NAT/subnet config has gone completly FUBAR (unless it some strange comatability issue with switch/router/firewall, I've pretty much eleminated external causes).

I'm not a complete Ubuntu newbie, but on this, I've exausted all my toubleshooting capabilities. If there is a google'able solution out there, please tell me the Q-words, cause I've been searching and cursing all day about this.

Please give me some pointers.
Let me know if I should post any logs og configs.
(work-realated - going home for today, will follow up tomorrow)

---

### Post by SeekerDK on 2009-09-01
"so I installed bind" I of cause ment that I UNinstalled bind :)

On top of that, last I saw, it was now a stable problem. I rebooted to do some more testing and tried to connect some 20 min after estimated boot up and the inet was dead. 

I'll try some more diagnostic/troubleshooting/reboots, but any and all help (where to look, what to look for, any logs I might have missed ect, things to try). My personal best, next step is simply to reinstall :(

---

### Post by eylisian on 2009-09-01
Glad to know you un-installed BIND =)

Is your /etc/resolve.conf file reporting that it was configured via NetworkManager?

I agree the SSH slowness sounds like DNS. Files to check;

/etc/network/interfaces

auto lo

auto eth0
iface eth0 inet static
address <addr-here>
netmask <mask-here>
broadcast <bcast-here>
network <optional>
gateway <gw-addr-here>

auto eth1
iface eth1 inet static
address <addr-here>
netmask <mask-here>
broadcast <bcast-here>
network <optional>
gateway <gw-addr-here>

/etc/resolv.conf  # points to known good name server 4.2.2.2 works in a pinch

If /etc/resolv.conf is reporting NetworkManager built the file you can try disabling NM with;

sudo /etc/init.d/NetworkManager stop
sudo update-rc.d NetworkManager remove

That will remove it from startup (not from the system)

After that you should be able to invoke;

/etc/init.d/networking restart

And packets should be flowing to their respective destinations.

Hope this was helpful,
Regards.

---

### Post by SeekerDK on 2009-09-01
> **eylisian said:**
> Glad to know you un-installed BIND =)

Is your /etc/resolve.conf file reporting that it was configured via NetworkManager?
No, resolv.conf is owerwritten by the DHCP on eth1. I tried to change the DHCPclient conf, as to not update DNS's, domain and searchdomain, but no luck.

> **eylisian said:**
> 
I agree the SSH slowness sounds like DNS. Files to check; **[COLOR=Red]<- But it is not the actual problem. DNS server are unreachable (on another subnet) when the inet/subnetrouting dies.[/COLOR]** 

/etc/network/interfaces

auto lo

auto eth0
iface eth0 inet static
...

auto eth1
iface eth1 inet static **[COLOR=Red]<- Nope DHCP otherwise "check"[/COLOR]**
...

/etc/resolv.conf  # points to known good name server 4.2.2.2 works in a pinch
**[COLOR=Red]Points to a private server primary and openDNS secondary[/COLOR]**


This far, I'm completly in line. I can see from all this, that I need to read up on what NM is all about. 

Unfortunaly, I'm at a customer today, and don't expect to get around to actually test your solution, but you sound fairly confident that the below is the solution? But what is the downside of disabling the network manager?, or is NM just a non-essential aimed at facilitating a frequent switch between subnet, locations and NICs?

> **eylisian said:**
> 
If /etc/resolv.conf is reporting NetworkManager built the file you can try disabling NM with;

sudo /etc/init.d/NetworkManager stop
sudo update-rc.d NetworkManager remove

That will remove it from startup (not from the system)

After that you should be able to invoke;

/etc/init.d/networking restart

And packets should be flowing to their respective destinations.

Hope this was helpful,
Regards.

I hope so to :) And in any case, I've gotten some more leads to follow up on. 
Thanks eylisian

---

### Post by SeekerDK on 2009-09-02
Nope. Disabling the NetworkManager didn't do the trick.

But now confirmed that it is a constant problem, as in the inet is broken right from reboot. Wondering if the unconfigured virtualization could somehow be the cause? Again, any and all help will be greatly appreciated.  

Setup (taken shortly after reboot):

**resolv.conf**
search [domain].local
nameserver 192.168.42.71[COLOR=Red]<- AD server on other subnet - unreachable[/COLOR]
nameserver 208.67.222.222 [COLOR=Red]<- OpenDNS[/COLOR][COLOR=Red] - unreachable[/COLOR]
[COLOR=Red]
[/COLOR][B]dhcpclient.conf
[/B]request subnet-mask, broadcast-address, time-offset, routers,
#       domain-name, domain-name-servers, domain-search, host-name, [COLOR=Red]<- **NOTE**[/COLOR]
        netbios-name-servers, netbios-scope, interface-mtu,
        rfc3442-classless-static-routes, ntp-servers;[COLOR=Red]Updated so not to overwrite resolv.conf.  [/COLOR]
**Netstat -nr** 
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.122.0   0.0.0.0         255.255.255.0   U         0 0          0 virbr0
10.10.0.0       0.0.0.0         255.255.0.0     U         0 0          0 eth0
10.10.0.0       0.0.0.0         255.255.0.0     U         0 0          0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         10.10.1.1       0.0.0.0         UG        0 0          0 eth1
0.0.0.0         10.10.1.1       0.0.0.0         UG        0 0          0 eth0
[COLOR=Red]Yes, gateway is correct :) Not completly sure what 169.154.0.0 is, but google surgests it is OK[/COLOR]

[B]interfaces
[/B]auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
address 10.10.1.12
netmask 255.255.0.0
network 10.10.0.0
broadcast 10.10.255.255
gateway 10.10.1.1

auto eth1 
iface eth1 inet dhcp


[B]ifconfig
[/B]eth0      Link encap:Ethernet  HWaddr [COLOR=Red]hidden[/COLOR]
          inet addr:10.10.1.12  Bcast:10.10.255.255  Mask:255.255.0.0
          inet6 addr: fe80::221:5eff:fe57:1470/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:581 errors:0 dropped:0 overruns:0 frame:0
          TX packets:162 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:62604 (62.6 KB)  TX bytes:24560 (24.5 KB)
          Interrupt:16 Memory:ce000000-ce012700 

eth1      Link encap:Ethernet  HWaddr [COLOR=Red]hidden[/COLOR]
          inet addr:10.10.1.116  Bcast:10.10.255.255  Mask:255.255.0.0
          inet6 addr: fe80::221:5eff:fe57:1472/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:413 errors:0 dropped:0 overruns:0 frame:0
          TX packets:180 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:38375 (38.3 KB)  TX bytes:19204 (19.2 KB)
          Interrupt:17 Memory:ca000000-ca012700 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:35 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2144 (2.1 KB)  TX bytes:2144 (2.1 KB)

virbr0    Link encap:Ethernet  HWaddr [COLOR=Red]hidden[/COLOR]
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::2cba:c7ff:fed2:d679/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:78 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:12288 (12.2 KB)

Anything else I should post?

---

### Post by SeekerDK on 2009-09-02
HANG ON!!! 
Disabling the NM might have worked after all. (or the problem is in fact at temporary one).

RIGHT is minute, it has inet connection (first try, I just restarted networking, after shutting down NM, now I rebooted with the updated rc.d and seems that it is working (at least I can apt-get update now). 

Updates will follow, but right this moment, the problem is "solved".

---

### Post by SeekerDK on 2009-09-02
**Nope. Not fixed** (I guess)

Note sure what causes the inet/routing to fall down and GW log (10.10.1.1) shows nothing.
It seems to breaks down some random time after reboot (from almost immediately to bordering 30 mins) and I've not been able to link the breakage to any specific activity (what apparently kills it in one run, have not effect in another).

NB. 
I forgot to mention that I've also install ubuntu-desktop to make adminitration easier (ssh -X gnome-panel)
Right now, it has been working for 30 minutes straight, but I fear it is only a matter of time (I've setup a constant ping (every 5 secs) to find out excatly where/when it breaks, but of cause it just keeps on working now :-S )

Just generating ideas here:
Could the fact that I'm running a class B subnet on a class A address possible have any effect?
What could cause a periodical issue like this, when only routing/inet dies, but localnet still works?

---

### Post by SeekerDK on 2009-09-02
In an amazing feat of Quantum Theory, I've change the outcome by measuring the result. 

I have done NO changes to configuration, but to open a ssh term from a client and started a ping. And is has now been running for almost 3 hours. 

Closed the ping window and true enough, 5 mins later the inet/router was down.

I'm going INSANE here :sad:

(edit: I really need to get moving on configuring the server for its purpose, so I "quick-fixed" it with [COLOR=DarkOrchid]*ping [our outside DNS server] > null &*[/COLOR]
Ugly and pretty lame if I have to say it my self, but it works)

---

### Post by SeekerDK on 2009-09-09
Got something to go on...
[http://ubuntuforums.org/showthread.php?t=573765](http://ubuntuforums.org/showthread.php?t=573765)

This led me to find that the ndiswrapper actually dies on me. To be continued

---

