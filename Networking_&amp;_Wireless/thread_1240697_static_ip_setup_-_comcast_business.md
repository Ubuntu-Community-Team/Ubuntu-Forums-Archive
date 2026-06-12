---
title: "static ip setup - comcast business"
date: 2009-08-15
forum: Networking &amp; Wireless
---

### Post by thegrilledcheese on 2009-08-15
Today I upgraded to comcast business internet.  I am needing to figure out how to configure Ubuntu 9.04 to specify an specific IP.  The gateway is currently using DHCP to assign internal addresses.  However, the outside world sees both of my computers as the gateway's ip and not one of my 5 static ip's.  I read on another page how to login to the gateway and turn off DHCP, which will then require me to configure both of my desktops to use a specifc IP.  I've found tutorials online on how to set a static INTERNAL ip but haven't figured out how to set a static INTERNAL and EXTERNAL ip.  Any thoughts?

My network looks like this

Business IP Gateway >>> D-Link Router >>> 2 desktops

Here are the numbers:

Internal network
gateway: 10.1.10.1
subnet: 255.255.255.0
IPs: 10.1.10.10 - 10.1.10.199

External: (these aren't the real numbers but you get the point)
Gateway: 173.160.129.198
IPS: 173.159.129.10 - 173.159.129.14


So again....how do I set both internal AND external static IP address?  I've read to edit /etc/network/interfaces but that seems to only pertain to internal IPs

Thanks!!!

---

### Post by Iowan on 2009-08-15
Just "theorizing" (sounds better than "guessing").  The machines should be set to their external static IP's. The router will need to be tweaked... probably turn off NAT and DHCP. The gateway is the part that I'm not really sure about. It seems to be acting like a NAT-ing machine (router?). It *might* be unnecessary after your upgrade, but that's where the theory degenerates into a guess.

---

### Post by thegrilledcheese on 2009-08-15
I realized I don't need to set an internal ip if I have an external working IP.  I turned of DHCP on the gateway and plugged in the cat5 cable from it to the DLINK router in a regular port instead of the WAN port.  Configured /etc/network/interface like:

auto eth0
iface eth0 inet static
address x.x.x.x
netmask x.x.x.x
network x.x.x.x
broadcast x.x.x.x
gateway x.x.x.x

then :

sudo /etc/init.d/networking restart

then:

sudo gedit /etc/resolv.conf

added my nameservers



WORKS!!!

Except now everytime i reboot my desktop, somehow my resolv.conf gets changed back to DHCP DNS.  Anyone know how to turn this off?  The gateway isn't doing this.

---

### Post by Iowan on 2009-08-15
It didn't occur to me earlier that you could probably use DHCP to set the *external* address via MAC address (static lease), then use the dhclient.conf *prepend* line to set DNS servers.  But is should be possible to stop dhclient from running. BTW, use [gksudo]("http://www.psychocats.net/ubuntu/graphicalsudo") with **gedit**.

---

### Post by thegrilledcheese on 2009-08-19
So I found out why my resolv.conf was being reset after every reboot.  DHClient was running at startup and asking for DHCP information.  My gateway had DHCP turned off so it didn't change the /etc/network/interfaces file, it only reset /etc/resolv.conf.

So I found this solution online, and while isn't suggested as a good fix, it does work.  This basically tells dhclient to ignore any nameserver updates that it might get when requesting DHCP DNS.

```
gksudo gedit /etc/dhcp3/dhclient.conf
```I added the following line (add your own nameservers, don't forget the comma in between and semi-colon at the end):

```
supersede domain-name-servers xxx.xxx.xxx.xxx, xxx.xxx.xxx.xxx;
```I'm not sure if where you put it in the file makes a difference but I put it right above the 'request' command.

That seemed to fix the problem but upon reboot I found out Network Manager was still running and erasing resolv.conf.  SIGH!!

I completely removed all network manager components, reboot and it now works fine.  resolv.conf stays the same.

---

### Post by bluestix on 2009-10-04
> **thegrilledcheese said:**
> 

That seemed to fix the problem but upon reboot I found out Network Manager was still running and erasing resolv.conf.  SIGH!!

I completely removed all network manager components, reboot and it now works fine.  resolv.conf stays the same.



There is a much easier way to prevent overwrites of your resolve.conf file.


sudo chattr -i /etc/resolve.conf

---

### Post by Peetii on 2011-01-30
> **bluestix said:**
> There is a much easier way to prevent overwrites of your resolve.conf file.


sudo chattr -i /etc/resolve.conf

sudo chattr **+**i /etc/resolve.conf


... to be precise.  ( + vs - )

---

