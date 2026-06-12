---
title: "Network setup - dsl, linksys, eth0"
date: 2010-02-24
forum: Networking &amp; Wireless
---

### Post by feb23 on 2010-02-24
New to Ubuntu (9.04); I am not quite sure how to setup the network.  I have a ISP-supplied DSL modem, Linksys 160N router and, of course, the built-in network adapter, eth0.
 I am running ufw -- default deny, plus some miscellaneous rules.
 Everything works, but is my setup correct, and most importantly - SAFE?  
 ….........................................................
 Router settings:
 
 Internet Connection Type: PPPoE
 Username: xxxxxxx
 Password: xxxxxxx
 
Network Setup Router IP:
     Local IP Address: 192.168.1.1
     Subnet Mask: 255.255.255.0
 DHCP Server Setting:
     DHCP Server: Enabled
     Start IP Address: 192.168.1.100
     Max. Number of Users: 50
     IP Address Range: 192.1681.100 to 149
     Static DNS 1: xxxxxx
     Static DNS 2: xxxxxx
 …..........................................................
 After applying the above-mentioned settings, when I right-click on the network manager icon - Connection Information, output is as follows:  
     Auto eth0 (default)
     Interface: Ethernet (eth0)
     Hardware Address: xxxxxxxx
     Driver: xxxxxxx
     Speed: 100 Mb/s
     Security: None
 
     IP Address: 192.168.100
     Broadcast Address: 192.168.1.255
     Subnet Mask: 255.255.255.0
     Default Route: 192.168.1.1
     Primary DNS: xxxxxxx
     Secondary DNS: xxxxxxx
 …..........................................................
 deb@ub:~$ ifconfig 
 
 eth0      Link encap:Ethernet  HWaddr xx xx xx xx   
           inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0 
           inet6 addr: xxxx xx xx xxx xxx/64 Scope:Link 
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
           RX packets:16715 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:18156 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:16298750 (16.2 MB)  TX bytes:2471660 (2.4 MB) 
           Interrupt:17 Base address:0x2000  
  
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0 
           inet6 addr: ::1/128 Scope:Host 
           UP LOOPBACK RUNNING  MTU:16436  Metric:1 
           RX packets:20 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:20 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:0  
           RX bytes:1416 (1.4 KB)  TX bytes:1416 (1.4 KB) 
 ….....................................................................
 Finally, this is what I get when I check interfaces:
 
 deb@ub:/$ cat /etc/network/interfaces 
 auto lo 
 iface lo inet loopback 
  THIS IS NOT RIGHT - IS IT???
 
 Any input is appreciated, thanks.

---

### Post by suseendran.rengabashyam on 2010-02-24
Hi,

Network Manager is a GUI tool for managing your network interfaces. If you have used the NM to configure your network interface then you don't need to add anything in your /etc/network/interfaces file.

---

### Post by chili555 on 2010-02-24
> Everything works, but is my setup correct, and most importantly - SAFE? It looks perfectly correct to me. If you are careful and conservative with your ufw settings, then it's safe as well. Remember, your router and probably your DSL modem have firewalls, too. This is not to say that a determined hacker can't get in, but why? If the hacker has the determination, resources and time to get through *three * firewalls and then into a non-Windows system which requires an administrators password, why not just hack the bank? They have millions. I have twenties.

---

### Post by feb23 on 2010-02-24
Suseendran & chili,
 

 Thank you so much for taking time to respond.
 This has been the easiest setup, yet!!! 
 

 UBUNTU – TWO THUMBS UP

---

