---
title: "No Internet When Using Static IP"
date: 2012-11-06
forum: Networking &amp; Wireless
---

### Post by wagb278 on 2012-11-06
I just installed Ubuntu 12.04.1 and if I set static IP in /etc/network/interfaces I cannot access the Internet, but can ping nodes on the LAN. This computer was configured with a static IP with the older Ubuntu version and was working (LAN access and Internet access).  I am guessing I missed some setting, but I don't know where and what. 

Is there an additional configuration setting somewhere needed to permit accessing the Internet when using a static IP?

The router is set to split DHCP and Static addresses.  Static addresses start at #200; below that everything gets DHCP assigned IPs.  The Ubuntu 12.04 node was connecting to the Internet before I assigned the static IP.  Another node with Lubuntu 12.10 could also access the Internet before I changed the interfaces file on that node to use a static IP. 

The interfaces file contents are: 
```
auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.0.205
netmask 255.255.255.0
gateway 192.168.0.1

auto eth0
```

I rebooted after changing the interfaces file and I cycled power on my router thinking that might help, but it did not. 

I am quite sure I can change the interfaces file back to DHCP and I will get Internet connection back. 

If there is some additional information I can provide please ask.  I am stumped as to where to look. 

Thanks,
Jim

---

### Post by papibe on 2012-11-06
Hi wagb278.

Could you post the result of these commands?
```
ifconfig

route -n

nslookup ubuntu.com

dig google.com

apt-cache policy network-manager
```
Regards.

---

### Post by ahallubuntu on 2012-11-06
Try this in your interfaces file instead (in this exact order):

```
auto eth0
iface eth0 inet static
address 192.168.0.205
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1
```

I loathe using static IP and avoid it if at all possible.  I much prefer using DHCP reservations in the router itself to force the same IP at each connection.  That way, each new OS or upgrade can remain set to "DHCP" or automatic and I can manage my network in one place!

---

### Post by wagb278 on 2012-11-07
Sorry it has been so long returning - life gets in the way.

The results of the commands requested are: 

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:1c:c0:35:03:e6  
          inet addr:192.168.0.205  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:c0ff:fe35:3e6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:67 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:712 (712.0 B)  TX bytes:10274 (10.2 KB)
          Interrupt:20 Memory:e3200000-e3220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:92 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6768 (6.7 KB)  TX bytes:6768 (6.7 KB)

```
route:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
```
dig:
```

; <<>> DiG 9.8.1-P1 <<>> google.com
;; global options: +cmd
;; connection timed out; no servers could be reached
```

nslookup:
```
;; connection timed out; no servers could be reached

```

cache:
```
network-manager:
  Installed: 0.9.4.0-0ubuntu4.1
  Candidate: 0.9.4.0-0ubuntu4.1
  Version table:
 *** 0.9.4.0-0ubuntu4.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     0.9.4.0-0ubuntu3 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
```

I tried the suggested contents for the interfaces file, but that did not resolve the issue - I did a computer restart after changing that file. I still cannot access the Internet.

I only use static IP for computers that will host Apache web server for developing & testing websites on my LAN.

Thanks for assisting me with this. 
Jim

---

### Post by chili555 on 2012-11-07
Please try this:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.205
netmask 255.255.255.0
gateway 192.168.0.1
dns-nameservers 8.8.8.8 192.168.0.1
```Get the interface to re-read the file:```
sudo ifdown eth0 && sudo ifup eth0
```Check:```
ping -c3 www.google.com
```

---

### Post by papibe on 2012-11-07
Thanks.

It looks like this is not a server, but a Desktop edition.

Network-Manager is installed, and thus the settings on /etc/network/interfaces are not being consider.

Either set the setting using the GUI tool 'Network Connections', or uninstall network-manager.

For the GUI options take a look at this [tutorial]("http://www.ubuntugeek.com/ubuntu-networking-configuration-using-graphical-tool.html"). Although, it is a little old, it should show you the basics.

Let us know how it goes.
Regards.

---

### Post by wagb278 on 2012-11-07
Thanks chili555 - that got the Internet access back working. 

I guess I need to do some research to better understand this.  I looked at the Man pages for /etc/network/interfaces and it does not include dns-nameserver entries. I saw some articles on a /etc/resolv.conf that I need to understand; but at least I have Internet access to do that with. 

I tried using - again - the Network Manager but that only messes things up and I even tried to disable that tool, but doing that just screws up the interface.  I discovered an article [[COLOR="Blue"]here[/COLOR]]("http://www.sitepoint.com/ubuntu-12-04-lts-precise-pangolin-networking-tips-and-tricks/") that I only scanned quickly, but might help others.

I will mark the original post as solved; but I have some studying to do that should not justify keeping this post active. Thanks All.

---

### Post by chili555 on 2012-11-08
This is an issue in 12.04 and following because of dnsmasq. Here is a good discussion of it. [http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/](http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/)

---

### Post by sirkong on 2013-02-08
> **chili555 said:**
> Please try this:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.205
netmask 255.255.255.0
gateway 192.168.0.1
dns-nameservers 8.8.8.8 192.168.0.1
```Get the interface to re-read the file:```
sudo ifdown eth0 && sudo ifup eth0
```Check:```
ping -c3 www.google.com
```
Thank you very much! This helped me solve my internet access problem.

---

### Post by Edward Hermanson on 2013-04-18
You so rule. 2 days trying to solve this. I might name my first born chili555. I was stunned when my ping worked :)

---

