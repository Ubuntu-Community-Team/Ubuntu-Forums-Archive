---
title: "High pings to router, apache2 might be the cause."
date: 2009-09-10
forum: Networking &amp; Wireless
---

### Post by solidwinter on 2009-09-10
I'm running a debian lenny box at home with Samba, DHCP3-server, bind9, apache2, mysql5 and ssh.
 
I'm having issues of high pings too my router connecting me to the internet of about 3000-5000ms. I've found that stopping the apache2 process fixes it but I'm not enitrly convinced that its apache2 causing the issue.
 
I still get full speed on downloads, but each computer, including the debian box itself get high pings.
 
What does usually cause these types of issues?
 
Thanks, Solidwinter.

---

### Post by nandemonai on 2009-09-10
> **solidwinter said:**
> I'm running a debian lenny box at home with Samba, DHCP3-server, bind9, apache2, mysql5 and ssh.
 
I'm having issues of high pings too my router connecting me to the internet of about 3000-5000ms. I've found that stopping the apache2 process fixes it but I'm not enitrly convinced that its apache2 causing the issue.
 
I still get full speed on downloads, but each computer, including the debian box itself get high pings.
 
What does usually cause these types of issues?
 
Thanks, Solidwinter.

Do you have a LAN cable tester there? I'm guessing it's either EMI or a bad cable(s). Can you get decent pings from box to box?

Also, do you use a switch or are all the machines connected directly to the router?

---

### Post by solidwinter on 2009-09-10
Theres a switch between all the computer and all the cables are tested and fine.
 
I get fine pings between the boxes, only to the router.
 
It *only* happens when apache2 is running.

---

### Post by nandemonai on 2009-09-10
> **solidwinter said:**
> Theres a switch between all the computer and all the cables are tested and fine.
 
I get fine pings between the boxes, only to the router.
 
It *only* happens when apache2 is running.

Very bizzare.

Can you run a traffic monitor like iptraf, jnettop or even netstat while you have apache running to see if it's blasting the router with traffic?

---

### Post by solidwinter on 2009-09-11
I ran iptraf before I started apache and I didnt find anything unusual. About 20 minutes after running apache port 80 was going nuts. There wasnt any traffic on the network that should of been using port 80 at the time.

[IMG]http://img190.imageshack.us/img190/5959/capture2g.png[/IMG]

I also saw this being flooded whenever I did ping google or use firefox.

&#9488;
&#9474; ICMP dest unrch (port) (321 bytes) from 10.0.0.21 to 192.55.83.30 on eth0    &#9474;
&#9474; UDP (298 bytes) from 192.55.83.30:53 to 10.0.0.21:5123 on eth0               &#9474;
&#9474; ICMP dest unrch (port) (326 bytes) from 10.0.0.21 to 192.55.83.30 on eth0    &#9474;
&#9474; UDP (298 bytes) from 192.55.83.30:53 to 10.0.0.21:34863 on eth0              &#9474;
&#9474; ICMP dest unrch (port) (326 bytes) from 10.0.0.21 to 192.55.83.30 on eth0    &#9474;

After stopping apache2 port 80 closed and I could ping the router fine.

---

### Post by nandemonai on 2009-09-11
> **solidwinter said:**
> I ran iptraf before I started apache and I didnt find anything unusual. About 20 minutes after running apache port 80 was going nuts. There wasnt any traffic on the network that should of been using port 80 at the time.

[IMG]http://img190.imageshack.us/img190/5959/capture2g.png[/IMG]

I also saw this being flooded whenever I did ping google or use firefox.

&#9488;
&#9474; ICMP dest unrch (port) (321 bytes) from 10.0.0.21 to 192.55.83.30 on eth0    &#9474;
&#9474; UDP (298 bytes) from 192.55.83.30:53 to 10.0.0.21:5123 on eth0               &#9474;
&#9474; ICMP dest unrch (port) (326 bytes) from 10.0.0.21 to 192.55.83.30 on eth0    &#9474;
&#9474; UDP (298 bytes) from 192.55.83.30:53 to 10.0.0.21:34863 on eth0              &#9474;
&#9474; ICMP dest unrch (port) (326 bytes) from 10.0.0.21 to 192.55.83.30 on eth0    &#9474;

After stopping apache2 port 80 closed and I could ping the router fine.

Something weird going on here...

whois 192.55.83.30

OrgName:    VeriSign Global Registry Services 
OrgID:      VGRS
Address:    21345 Ridgetop Circle
City:       Dulles
StateProv:  VA
PostalCode: 20166
Country:    US

NetRange:   192.55.83.0 - 192.55.83.255 
CIDR:       192.55.83.0/24 
NetName:    VGRSGTLD-13
NetHandle:  NET-192-55-83-0-1
Parent:     NET-192-0-0-0-0
NetType:    Direct Assignment
NameServer: A2.NSTLD.COM
NameServer: H2.NSTLD.COM
NameServer: C2.NSTLD.COM
NameServer: D2.NSTLD.COM
NameServer: E2.NSTLD.COM
NameServer: F2.NSTLD.COM
NameServer: G2.NSTLD.COM
NameServer: L2.NSTLD.COM
Comment:    
RegDate:    2000-11-30
Updated:    2004-06-23

RTechHandle: NETWO480-ARIN
RTechName:   Network Admin 
RTechPhone:  +1-703-948-4300
RTechEmail:  [email]netadmin@verisign.com[/email] 

OrgTechHandle: NETWO480-ARIN
OrgTechName:   Network Admin 
OrgTechPhone:  +1-703-948-4300
OrgTechEmail:  [email]netadmin@verisign.com[/email]

# ARIN WHOIS database, last updated 2009-09-10 20:00
# Enter ? for additional hints on searching ARIN's WHOIS database.

Is this your ISP?

I think it's time to post your /etc/network/interfaces, /etc/resolv.conf and apache confs.

---

### Post by solidwinter on 2009-09-19
/etc/network/interfaces
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static

address 10.0.0.21
netmask 255.0.0.0
network 10.0.0.0
gateway 10.0.0.10

```

/etc/resolve.conf
```

nameserver 10.0.0.10

```

Does that look fine to you guys?

That whois info nandemonai posted is not my ISP.

---

