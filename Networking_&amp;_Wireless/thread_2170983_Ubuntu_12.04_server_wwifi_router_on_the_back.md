---
title: "Ubuntu 12.04 server w/wifi router on the back"
date: 2013-08-28
forum: Networking &amp; Wireless
---

### Post by Fenderian_Mayhew on 2013-08-28
"on the back" = behind the system,
 
Inet > router > eth0 > U12.04 > eth1 > "behind" router >wifi(passworded and restricted via mac address white list, Isolated guest network)
eth1 goes to the "internet/Wan" port of the router
Ubuntu 12.04 is setup where eth1 is IPv4 shared, IPv6 Ignored

I want to serve out via eth1 SSH, VNC, FTP, Etc. what can i disable/adjust in routers to give connection between eth1 & the router clear access?

I know port forwarding would work for most things but i would like to know how to make a router open every port(yes i know that is usually a bad idea), auto configure (UPnP laptop smart Terminal?) or just create a unsecured connection from the router to the server and handle security in ubuntu & Or not at all (Is it even nessasary to secure the eth1>routerWan hardline's connections in this situation?)

end goal is an isolated secure wifi network i can controll my main pc from and can play any one of the many games i have installed on it via vnc or other meathod. 
Thanks for reading and please ask any clarifying questions or refer to links. thanks ^.^

---

### Post by papibe on 2013-08-28
Hi Fenderian_Mayhew.

The simplest way would be to set a [DMZ]("http://en.wikipedia.org/wiki/DMZ_%28computing%29") in your Internet facing router. The DMZ should point to the U12.04 machine. 

Caveats:
[LIST]
[*]Depending in how your router works, you would (probably) need to:
[LIST]
[*][*]Set U12.04 to use DHCP on the eth0 interface.
[*][*]Reboot U12.04, or renew its DHCP lease.
[/LIST]
[*]You would have to tighten security in U12.04, since the external router won't do any.
[/LIST]
Another thoughts:
[LIST]
[*]Make sure you disable wireless on the Internet router.
[*]Install a firewall software, or use iptables on U12.04.
[/LIST]
Hope it helps. Let us know how it goes.
Regards.

---

### Post by Fenderian_Mayhew on 2013-08-28
Ive Gotten the internet fine through eth0 and plan to leave it secure. the seccond router though, the one connected via its wan port to the U12.04 via eth1, the connections on it should be able to access served screens(vnc) and act as remote controller(ssh). how do i open the Router2>eth1 WAN connection so the device on 10.0.0.* (R2) can use and controll services on system 192.168.0.4(R1) which connects to its internet over eth0 and shares its internet back to R2 and its atached deivces. 

the latter works. i can get internet on any device atached to the wifi & hard wired router2.

 but how do i open the routers Internet port so my pc can network w/o restrictions to other devices on the seccond routers LAN.

---

### Post by papibe on 2013-08-28
This is a couple of alternatives that I would consider:

**Option 1**:
[LIST]
[*]Disable DHCP on the internal router.
[*]This way the router would be providing WIFI (as an access point), serve a switch for wired connections, but no filtering or rules.
[*]Install and configure DHCP and DNS services on U12.04 (eth1).
[*]That way all machines will be on the same network as U12.04 (no port forwarding rules necessary).
[/LIST]
**Option 2**:
[LIST]
[*]Change the layout to:
```
Inet > router1 > router2 > wifi
                         > U12.04
```
[*]router2 will provide DHCP and DNS.
[*]All clients machine are in the same network.
[/LIST]
Does that help?
Regards.

---

### Post by Fenderian_Mayhew on 2013-08-28
> **papibe said:**
> This is a couple of alternatives that I would consider:

**Option 1**:
[LIST]
[*]Disable DHCP on the internal router.
[*]This way the router would be providing WIFI (as an access  point), serve a switch for wired connections, but no filtering or rules.
[*]Install and configure DHCP and DNS services on U12.04 (eth1).
[*]That way all machines will be on the same network as U12.04 (no port forwarding rules necessary).
[/LIST]
**Option 2**:
[LIST]
[*]Change the layout to:
```
Inet > router1 > router2 > wifi
                         > U12.04
```
[*]router2 will provide DHCP and DNS.
[*]All clients machine are in the same network.
[/LIST]
Does that help?
Regards.
Much Thanks ^.^

Op2 was thought of but not implimented beacuse eth0, & router1 are Gbit and eth1 and Router2 is 100m. 
Gbit is used for Priter, Mcraft, local house files.
Router 2 is inended to be an isolated IP and wifi network. using a mac  address witelist on R2 provides sufficant security for now.

---

### Post by Fenderian_Mayhew on 2013-08-29
the DHCP & DNS Idea sounds like a learning experance & most likely to give the right results. 

do you know of any recommendable software or tutuorials.

---

### Post by papibe on 2013-08-29
Instead of DHCP server and BIND, I suggest installing Dnsmasq. It is simpler to configure and provide both DHCP and DNS services. I would start taking a look at this [tutorial]("https://help.ubuntu.com/community/Dnsmasq").

Regards.

---

### Post by Fenderian_Mayhew on 2013-08-30
Dnsmasq could very well be my ultimate sollution. i was looking for a DHCP/Routing program with PXE that could be used to boot a Smart terminal OS/Tinycore/other Distro. 

thanks.

---

### Post by Fenderian_Mayhew on 2013-08-30
I have found that running dnsmasq prevents the system from sharing out the network.
with dnsmasq daemonized the share internet setting causes the connection from eth1>router 2 to fail. 
with dnsmasq disabled the router detects my systems shared connection and connects to it with DHCP. the network applet's connection information lists the system as 10.42.0.1 and my subnet as 255.255.255.0 (255.0.0.0 would be approperate) . 
I remember defining someware my systems Subnet as 10.42.*.* but i cant remember where i set it and how.

---

