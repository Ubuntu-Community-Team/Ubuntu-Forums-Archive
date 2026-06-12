---
title: "ubuntu 11.10 router ALMOST working"
date: 2011-11-06
forum: Networking &amp; Wireless
---

### Post by brianm88 on 2011-11-06
Hi, after using 11.04 on my router/server for a long time, I've upgraded to 11.10 and rearranged my storage array now.

my network looks like this: Cablemodem -> eth0 -> eth1 -> switch -> other computers

Internet works fine on the server, i'm posting this message from it right now.

On the other computers, the server is giving them a proper ip. I can ping the server, I can ping any website, I can do nslookup on any site.  But when I try to sign into a messenger or use the web browser, nothing happens.  In internet explorer on the windows pc it just says "website found, waiting for reply" forever.  I've let it auto-detect settings, I've let it run the diagnose problems dialog, and I've ipconfig /renew.

Here is my /etc/network/interfaces:
> 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
    address 192.168.0.1
    network 192.168.0.0
    netmask 255.255.255.0
    broadcast 192.168.0.255


Here is dhcpd.conf:
> 
default-lease-time 600;
max-lease-time 7200;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.0.255;
option routers 192.168.0.1;
option domain-name-servers 208.67.222.222, 208.67.220.220;
#option domain-name "opendns.com";

subnet 192.168.0.0 netmask 255.255.255.0 {
range 192.168.0.2 192.168.0.100;
} 


I have uncommented the 2 lines for forwarding in sysctl.conf.

I have made the nat.sh script and added it to init.d

I have added this to rc.local:
> 
/sbin/iptables -P FORWARD ACCEPT
/sbin/iptables --table nat -A POSTROUTING -o eth0 -j MASQUERADE


I know I've made some small mistake somewhere and I'm just not spotting it.  Does anybody see what's wrong ?  Why isn't the windows pc fully functional ?  It seems to me if ping and nslookup are working then I'm on the verge of full functionality.

here is the report from ifconfig:
> 

eth0      Link encap:Ethernet  HWaddr 00:04:23:cc:cd:3d  
          inet addr:XXXXXXXXXXX  Bcast:255.255.255.255  Mask:255.255.252.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:47987 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6866 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7198348 (7.1 MB)  TX bytes:796136 (796.1 KB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:04:23:cc:cd:3c  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::204:23ff:fecc:cd3c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:849 errors:0 dropped:0 overruns:0 frame:0
          TX packets:559 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:118275 (118.2 KB)  TX bytes:57787 (57.7 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


---

### Post by brianm88 on 2011-11-06
Running ubuntu off a usb stick on the other computers yields the same result, things are pingable and nslookup works but browser hangs on "website found, waiting for reply"

---

### Post by brianm88 on 2011-11-06
Problem was the MTU setting on eth0....

ifconfig eth0 mtu 1500 

fixed the problem. other computers can access anything now

---

### Post by dannyboy79 on 2011-11-14
> **brianm88 said:**
> Problem was the MTU setting on eth0....

ifconfig eth0 mtu 1500 

fixed the problem. other computers can access anything nowawesome, thanks for sharing BUT can you paste where you added that MTU option in your config files? Hopefully it's not something you have to AFTER ity's up and running thru a terminal. Thanks  a lot if you can help!

---

