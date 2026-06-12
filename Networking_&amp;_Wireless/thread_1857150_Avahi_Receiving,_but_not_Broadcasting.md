---
title: "Avahi Receiving, but not Broadcasting"
date: 2011-10-09
forum: Networking &amp; Wireless
---

### Post by kaivanes on 2011-10-09
I recently installed Ubuntu Server 10.04 LTS on an old windows box (Pentium 4 era) to set up some home server stuff (file sharing, web server etc).  I've successfully installed Netatalk and LAMP, and I can access both services using the server ip address.

I installed Avahi, but the other computers still cannot see the advertised services.  What's weird is that sometimes I can see other Bonjour services from the Ubuntu box using avahi-browse, and sometimes I cannot (I don't have any idea why, or what it could be correlated with).  

Notes: Apollo is the server, Morpheus is a MacBook (10.7.1), and Icarus is an iPod(4.3.2).  Apollo is connected by ethernet to the router, all other computers are on WiFi.

Always show up:
```
+ eth0 IPv4 Apollo                                        Apple File Sharing        local
+ eth0 IPv4 Apollo                                        _device-info._tcp         local
+ eth0 IPv4 Apollo                                        Web Site                 local
+ eth0 IPv4 Apollo                                        SSH Remote Terminal       local
+ eth0 IPv4 Apollo [00:0f:9f:d7:ba:2b]                   Workstation                 local

```  
Sometimes show up:
```
+ eth0 IPv4 Morpheus                                   Apple File Sharing        local
+ eth0 IPv4 Morpheus                                   SSH Remote Terminal        local
+ eth0 IPv4 Icarus                                         SSH Remote Terminal        local
etc...
```

Kicker: I can still use the mdns names of the other computers (i.e. ssh user@Morpheus works from Apollo) even when Avahi can't see them.  This doesn't work the other way around though (i.e.. ssh user@Apollo doesn't work from Morpheus).  

It seems that the server can receive the broadcasts well enough, but has trouble broadcasting itself?  The problem is still there when I connect my laptop to the router directly by ethernet, so it doesn't seem to be a wireless broadcast issue...  I am quite stumped; any help would be greatly appreciated.


Relevant configuration files are included below.

nsswitch.conf looks like this:
```
passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4 mdns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```

avahi.conf looks like this:
```
[server]
host-name=Apollo
#domain-name=local
#browse-domains=0pointer.de, zeroconf.org
use-ipv4=yes
use-ipv6=no
#allow-interfaces=eth0
#deny-interfaces=eth1
#check-response-ttl=no
#use-iff-running=no
#enable-dbus=yes
#disallow-other-stacks=no
#allow-point-to-point=no

[wide-area]
enable-wide-area=no

[publish]
#disable-publishing=no
#disable-user-service-publishing=no
#add-service-cookie=no
#publish-addresses=yes
#publish-hinfo=yes
#publish-workstation=yes
#publish-domain=yes
#publish-dns-servers=192.168.50.1, 192.168.50.2
#publish-resolv-conf-dns-servers=yes
#publish-aaaa-on-ipv4=yes
#publish-a-on-ipv6=no

[reflector]
#enable-reflector=no
#reflect-ipv=no

[rlimits]
#rlimit-as=
rlimit-core=0
rlimit-data=4194304
rlimit-fsize=0
rlimit-nofile=300
rlimit-stack=4194304
rlimit-nproc=3
```

afpd.service looks like this:
```
<?xml version="1.0" standalone='no'?><!--*-nxml-*-->
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
<name replace-wildcards="yes">%h</name>

<service>
<type>_afpovertcp._tcp</type>
<port>548</port>
</service>

<service>
<type>_device-info._tcp</type>
<port>0</port>
<txt-record>model=Xserve</txt-record>
</service>

<service>
<type>_http._tcp</type>
<port>80</port>
</service>

<service>
<type>_ssh._tcp</type>
<port>22</port>
</service>

</service-group>
```

The logs don't show anything weird (at least to me):

```
Oct  9 18:25:55 Apollo avahi-daemon[2101]: Found user 'avahi' (UID 107) and group 'avahi' (GID 115).
Oct  9 18:25:55 Apollo avahi-daemon[2101]: Successfully dropped root privileges.
Oct  9 18:25:55 Apollo avahi-daemon[2101]: avahi-daemon 0.6.25 starting up.
Oct  9 18:25:55 Apollo avahi-daemon[2101]: Successfully called chroot().
Oct  9 18:25:55 Apollo avahi-daemon[2101]: Successfully dropped remaining capabilities.
Oct  9 18:25:55 Apollo avahi-daemon[2101]: Loading service file /services/afpd.service.
Oct  9 18:25:55 Apollo avahi-daemon[2101]: Loading new static hostname router.local.
Oct  9 18:25:55 Apollo avahi-daemon[2101]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.43.
Oct  9 18:25:55 Apollo avahi-daemon[2101]: New relevant interface eth0.IPv4 for mDNS.
Oct  9 18:25:55 Apollo avahi-daemon[2101]: Network interface enumeration completed.
Oct  9 18:25:55 Apollo avahi-daemon[2101]: Registering new address record for fe80::20f:9fff:fed7:ba2b on eth0.*.
Oct  9 18:25:55 Apollo avahi-daemon[2101]: Registering new address record for 192.168.2.43 on eth0.IPv4.
Oct  9 18:25:55 Apollo avahi-daemon[2101]: Registering HINFO record with values 'I686'/'LINUX'.
Oct  9 18:25:55 Apollo avahi-daemon[2101]: Server startup complete. Host name is Apollo.local. Local service cookie is 2855093504.
Oct  9 18:25:56 Apollo avahi-daemon[2101]: Service "Apollo" (/services/afpd.service) successfully established.
Oct  9 18:25:56 Apollo avahi-daemon[2101]: Static host name "router.local" successfully established.
```

eth0 configuration:
```
eth0      Link encap:Ethernet  HWaddr 00:0f:9f:d7:ba:2b  
          inet addr:192.168.2.43  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:9fff:fed7:ba2b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7862 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5502 errors:1 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:956746 (956.7 KB)  TX bytes:2810284 (2.8 MB)
          Interrupt:21 Base address:0xd800 
```

---

### Post by papibe on 2011-10-09
```
inet addr:**192.168.2.43**  Bcast:192.168.2.255  Mask:255.255.255.0
```
Hi kaivanes, I see that the server 'lives' on the 192.168.2.0 network. Are the other machines in the same network? May be the router creates a different network for its WiFi connections.

Just a thought,
Regards.

---

### Post by kaivanes on 2011-10-09
Sadly not; they are all on the .2 subnet :( 

That *is* the kind of thing that I would overlook though :p

---

### Post by papibe on 2011-10-10
Does the service/daemon goes down? or Is it still up but broadcasting?

Could you check next time you loose Apollo?
```
$ ps aux | grep avahi
```
Regards.

---

### Post by kaivanes on 2011-10-16
The Avahi Daemon does appear to be running:

```
XXXXX@Apollo:~$ ps aux | grep avahi
avahi    13786  0.6  0.1   2928  1588 ?        S    11:25   0:00 avahi-daemon: running [Apollo.local]
avahi    13787  0.0  0.0   2928   548 ?        Ss   11:25   0:00 avahi-daemon: chroot helper
XXXX    13789  0.0  0.0   3324   792 pts/0    S+   11:25   0:00 grep --color=auto avahi
```

Additionally, the machine seems to be able to broadcast (at least for ping)... I'm starting to think that this is just a symptom of the awful router/modem combo that Bell gave us.  ](*,)

---

