---
title: "Samba Network will not work without Router"
date: 2009-07-13
forum: Networking &amp; Wireless
---

### Post by speed32219 on 2009-07-13
Ok, I have been pulling my hair out and I found that unless I have the router/Gateway connected to the my network it does not work. (Been working for over a year with the router)
1 XP PC
4 Ubuntu PC's

If all the devices are connected through a local switch without a router/gateway I can not access files between machines.  They just can't find each other unless I connect up a wired connection to a Gateway/Router and then everything is just fine.  I need some advice.

All machines are set with a staic IP and assigned to Workgroup and configured with Samba/smb (I also started installing NFS for the Ubuntu Pc's but haven't configured that just yet).  Now the problem might be and I have removed it and re-insertd it to no avil is the gateway address of 192.168.1.1, and all PC's have static IP's of 192.168.1.100-110. When they were MS devices I don't think I had this issue, just don't remeber, its been awhile.

---

### Post by doas777 on 2009-07-13
sounds almost like the hosts are on differant vlans. what kinda switch do you have?

also can they ping eachother, and are you connecting by name or IP. if name, what kind of nameserver, and where on your network?

---

### Post by LMZKJ on 2009-07-13
It does sound like a name server issue.  Do you have host files configured with the name/IP addresses of each machine?  If you don't have a DNS server configured, this would let you communicate by name across all machines.

---

### Post by speed32219 on 2009-07-13
Ping - Network is unreachable.

When I configured the SW on the Ubuntu machines, they were connected to the Dlink Gateway/router.  Name server was not installed (Network just came up as part of the Ubuntu installation), just basic networking at the time and each madhine has a unique name (Vids-server, station1, station2, statioin3, etc.). I am now trying to set a basic network up and add a wireless device to the server and use it as a Gateway/bridge (for the other PC's) if I can do that.  Most these PC's do not require Internet access, they are just front ends for an HTPC setup. That is if I can drop the wired connection to the Gateway/Router, I have to run a 100' cable all the time to keep them up and running.  Wifie says it has to go, and its to hot to go into the roof and run it. LOL!

So first things first, I need to get a working network between these machnies for file sharing.

---

### Post by doas777 on 2009-07-13
> **speed32219 said:**
> Ping - Network is unreachable.

When I configured the SW on the Ubuntu machines, they were connected to the Dlink Gateway/router.  Name server was not installed (Network just came up as part of the Ubuntu installation), just basic networking at the time. I am now trying to set a basic network up and add a wireless device to the server and use it as a Gateway/bridge (to the other PC's) if I can do that.  Most these PC's do not require Internet access, they are just front ends for an HTPC setup. That is if I can drop the wired connection to the Gateway/Router, I have to run a 100' cable all the time to keep them up and running.  Wifie says it has to go, and its to hot to go into the roof and run it. LOL!

So first things first, I need to get a working netowrk between these machnies for file sharing.

what do you get from 
```

ifconfig
route
cat /etc/interfaces

``` on one of the affected hosts?

---

### Post by speed32219 on 2009-07-13
I am reading this off a machine and retyping into a machine that has internet access, so bear with me.  Also, I can ping now, the cable on the Dlink switch was half out,  The palstic cable clip is broken from me connecting and disonnecting. sorry.

ifconfig - inet addr: 192.168.1.109 Bcast 192.168.1.255 Mask 255.255.255.0
 
route Kernel routing table
Destination   Gateway  Genmask     Flags  Metric  Ref  Use  Iface
192.168.0.0   *       255.255.255.0      U     0       0    0   Eth0

cat /etc/interfaces - No such file or directory

Ubuntu 8.10 2.6.27-14-generic

Thank you for your help. I probably need to take a class on Networking for Dummies.

---

### Post by redmk2 on 2009-07-13
> **speed32219 said:**
> I am reading this off a machine and retyping into a machine that has internet access, so bear with me.  Also, I can ping now, the cable on the Dlink switch was half out,  The palstic cable clip is broken from me connecting and disonnecting. sorry.

ifconfig - inet addr: 192.168.1.109 Bcast 192.168.1.255 Mask 255.255.255.0
 
route Kernel routing table
Destination   Gateway  Genmask     Flags  Metric  Ref  Use  Iface
192.168.0.0   *       255.255.255.0      U     0       0    0   Eth0

cat /etc/interfaces - No such file or directory

This should be /etc/network/interfaces> 

Ubuntu 8.10 2.6.27-14-generic

Thank you for your help. I probably need to take a class on Networking for Dummies.

There is no need for a gateway or the setting of a default route if this is a LAN only based network.

You need to have all of the hosts in the 192.168.1.(1-254) range.  If you have a subnet mask of 255.255.255.0 along with the appropriate IP address that will take care of the addressing.  Then you need to setup DNS via hosts files or other means.

EDIT: All the hosts should be interconnected by a common switch.  No router is needed as they are all on the same subnet

---

### Post by doas777 on 2009-07-13
> **redmk2 said:**
> This should be /etc/network/interfaces


quite right, sorry bout that.

ok, so your showing that you have an IP for your internal network, and that traffic for 192.168.1.0/24 goes out over eth0. basically, everything looks like it should work.

now back to names vs addresses. can you ping if you use the IP address instead of hostnames? I think your router may be acting as a dns server. if you can ping by IP, then we know that the issue is name-based.

---

### Post by redmk2 on 2009-07-13
> I think your router may be acting as a dns server... And probably the switch as well.  The multiple ports on SOHO routers are really to a internal switch (L2) device.

---

### Post by speed32219 on 2009-07-13
cat /etc/network/interfaces
auto lo
if lo inet loopback

#The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.109
netmask 255.255.255.0
network 192.168.1.1
broadcast 192.168.1.255

I can only ping by IP addresses.  If I ping by name I get unknown host Vids-server. If I ping by name on  the machine I am using it works, accross the network nothing.  By the way, I am using just a dumb Dlink 5 port switch.

---

### Post by bab1 on 2009-07-13
Then all you need do is add the names to the /etc/hosts file on all the hosts.

Edit:  To clarify -- each Ubuntu host has an /etc/hosts file.  The file looks like this:```
127.0.0.1 localhost
192.168.1.12 malibu
192.168.1.200 printer

```

The host in this case is "malibu".  I can ping printer by name because I added it to the /etc/hosts file.  Do that on all 4 of your hosts files and you will be able to ping by name.

---

### Post by issih on 2009-07-13
Alternatively ping the host name with .local appended.

i.e. ping mycomputer.local if the host is called mycomputer.

This uses avahi for name resolution, and should work across heterogenous networks of macs/windows and lini computers.

Hope that helps

---

### Post by doas777 on 2009-07-13
> **bab1 said:**
> Then all you need do is add the names to the /etc/hosts file on all the hosts.

Edit:  To clarify -- each Ubuntu host has an /etc/hosts file.  The file looks like this:```
127.0.0.1 localhost
192.168.1.12 malibu
192.168.1.200 printer

```The host in this case is "malibu".  I can ping printer by name because I added it to the /etc/hosts file.  Do that on all 4 of your hosts files and you will be able to ping by name.

This is the easiest approach if you want to leave the router offline. if you do configure your host file, and bring the router back online, just remember, when changing addresses in one place you must change them in the other as well (as hosts is usually tried first). 
another possibility is to set up an internal bind server (mine has been running with basically no administration forever.)
Ive never had any luck wiht avahi, but I think it's time to look into it more seriously.

have fun

---

### Post by speed32219 on 2009-07-13
Thank you, Thank you, Thank you everyone. I'm in business. I had problems at first but then I added the same entries in both machines so far and it started working.  Originally I only added it to the Vid-server and I couldn't get through to it. I re-read 
bab1 post and it stated "add the names to the /etc/hosts file on **all the hosts**" and that did it.

Now, if I connect to the internet do I have to worry? Guess not it seams to work too!  I'll do more testing later.

Also I have been reading (not good) but what about the /etc/resolv.conf file?

Could I setup the Vid-server with just the resolv.conf file configured for name lookups by simply adding their addresses/names to /etc/resolv.conf.  It would then be the DNS for the local network?  Remember, my next step is to add a wireless card to the Vid-server and use that machine as a gateway/bridge for the other attached pc.'s on the network pointing toward 192.168.0.1 the network/gateway to the internet.  My stomach is a little upset just thinking about it. LOL!  This has taken me a long time to get to this point, whenever I would get upset I would just hook the cable up to the router/gateway to get my movie fix. 

Again, thank you everyone for your help and guidance.

---

### Post by doas777 on 2009-07-13
hosts files are used by the machine they reside on, to look up ipaddresses for given names. the file is not shared so only that host can access it. you have to configure it manually, so remember, if you rename or readdress one of your boxen, you will have to change the hosts file manually on all other PCs.

your hosts file does not have any internet addresses in it (usually) so if you search for [www.google.com](www.google.com), the file will not have it, but your system will fall back to using DNS to get the url.  DNS (Domain Name Service) is a differant type of service than a hosts lookup, but they do both do about the same job. the differance is that dns is for much larger networks, whereas hosts is only really manageable while you can count all your hosts on your fingers. 

if you want, you can set up a dns server (bind is typical) for your internal network, and then have it forward unresolved queries to your ISP network. it's a little involved but could be worthwhile.

---

### Post by bab1 on 2009-07-13
> **speed32219 said:**
> Thank you, Thank you, Thank you everyone. I'm in business. I had problems at first but then I added the same entries in both machines so far and it started working.  Originally I only added it to the Vid-server and I couldn't get through to it. I re-read 
bab1 post and it stated "add the names to the /etc/hosts file on **all the hosts**" and that did it.

Now, if I connect to the internet do I have to worry? Guess not it seams to work too!  I'll do more testing later.

Not for local (LAN) name resolution.  If you have set your IP addresses statically (and it appears you have) then there should be not problems there either.> 

Also I have been reading (not good) but what about the /etc/resolv.conf file?
The /etc/resolv.conf file is used to denote the IP addreses of the DNS servers you wish the host to use when resolving host names in the LAN or FQDN on the internet.> 

Could I setup the Vid-server with just the resolv.conf file configured for name lookups by simply adding their addresses/names to /etc/resolv.conf. 
No.  It is not to be used for the mapping of host names, but to point to the DNS servers that handle the mapping.> 

 It would then be the DNS for the local network?
Nope> 
  Remember, my next step is to add a wireless card to the Vid-server and use that machine as a gateway/bridge for the other attached pc.'s on the network pointing toward 192.168.0.1 the network/gateway to the internet.
You don't need to do that.  Just add the gateway IP address in the /etc/network/interfaces file on each host.  My network uses 192.168.1.0/24 addressing. It looks like this:```
# The primary network interface

iface eth0 inet static
address 192.168.1.12
netmask 255.255.255.0
**[COLOR="Blue"]gateway 192.168.1.1[/COLOR]**

```> 
My stomach is a little upset just thinking about it. LOL!  This has taken me a long time to get to this point, whenever I would get upset I would just hook the cable up to the router/gateway to get my movie fix. 

Again, thank you everyone for your help and guidance.

---

### Post by speed32219 on 2009-07-13
"You don't need to do that. Just add the gateway IP address in the /etc/network/interfaces file on each host. My network uses 192.168.1.0/24 addressing. It looks like this:
Code:
# The primary network interface

iface eth0 inet static
[B]address 192.168.1.109
netmask 255.255.255.0
gateway 192.168.0.1 "[/B]

Holy crap, that's all I need to do!  I better stop reading the wiki's, I can see where I would be working on that for months.  I'm going to try this now!!!

Thank you

PS.  Even if I install the wireless as a dhcp device in the Vid-server? 
I think I'll slow up here, somehow I screwed up the wireless. The saga goes on. LOL!

---

