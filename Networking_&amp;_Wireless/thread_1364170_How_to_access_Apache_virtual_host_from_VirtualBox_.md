---
title: "How to access Apache virtual host from VirtualBox Windows 7 guest?"
date: 2009-12-25
forum: Networking &amp; Wireless
---

### Post by r.osmanov on 2009-12-25
Hi guys.

I've installed VirtualBox 3.1.2 under Ubuntu 9.10. 
What should I do in order to browse virtual hosts from a Windows 7 guest?

For the sake of simplicity, I made the following vhosts:
ServerName server.myhost

```
NameVirtualHost 127.0.0.2:80
NameVirtualHost 127.0.0.3:8080

<VirtualHost 127.0.0.2:80>
DocumentRoot /var/www/localhost
ServerName myhost
</VirtualHost>
    
<VirtualHost 127.0.0.3:8080>
DocumentRoot /var/www/myhost8080
ServerName myhost8080
</VirtualHost>
```Both are browsable in Ubuntu. Now I want access one of them from Windows 7 guest. 
The guest settings are:
Adapter: NAT
Adapter type: Intel PRO/1000MT Desktop (82540EM)

I think the last step should be forwarding port from the guest to host. 
Tried the following commands:
```
VBoxManage setextradata "windows7" \
"VBoxInternal/Devices/e1000/0/LUN#0/Config/http/Protocol" TCP
VBoxManage setextradata "windows7" \
"VBoxInternal/Devices/e1000/0/LUN#0/Config/http/GuestPort" 80
VBoxManage setextradata "windows7" \
"VBoxInternal/Devices/e1000/0/LUN#0/Config/http/HostPort" 8080
```No results. What could i omit?

Regards.

---

### Post by r.osmanov on 2009-12-25
Still doesn't work. ipconfig shows:
IPv4Address: 10.0.2.15
Default Gateway: 10.0.2.2
Both are not accessible from browser.

---

### Post by r.osmanov on 2009-12-25
By the way, in Ubuntu ifconfig shows:
[SIZE=1]```
eth0      Link encap:Ethernet  HWaddr 00:1f:d0:89:08:95  
          inet6 addr: fe80::21f:d0ff:fe89:895/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24357 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25575 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21094654 (21.0 MB)  TX bytes:3421230 (3.4 MB)
          Interrupt:28 Base address:0x6000 

eth0:avahi Link encap:Ethernet  HWaddr 00:1f:d0:89:08:95  
          inet addr:169.254.6.100  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:28 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:362 errors:0 dropped:0 overruns:0 frame:0
          TX packets:362 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:144146 (144.1 KB)  TX bytes:144146 (144.1 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:94.141.77.248  P-t-P:94.141.64.242  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:21765 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22649 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:20456037 (20.4 MB)  TX bytes:2734547 (2.7 MB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          inet addr:192.168.56.1  Bcast:192.168.56.255  Mask:255.255.255.0
          inet6 addr: fe80::800:27ff:fe00:0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:429 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:45280 (45.2 KB)

```[/SIZE]
when the virtual machine is running

---

### Post by r.osmanov on 2009-12-26
Yeah, I've got it! :)

It was an IP issue. Vhost and the guest IPs were merely different.
So I tried to setup vhost on 10.0.2.2, but it didn't work even in Ubuntu itself. I don't know why, maybe Apache configuration is wrong somewhere. 
Then I simply relayed port 8080 connections to IP 127.0.0.3:
```
iptables -t nat -A OUTPUT -p tcp --dport 8080 -j DNAT --to-destination 127.0.0.3
```and forwarded port 8080 in VBox:
```
VBoxManage setextradata "winxp" \
"VBoxInternal/Devices/pcnet/0/LUN#0/Config/http/Protocol" TCP
VBoxManage setextradata "winxp" \
"VBoxInternal/Devices/pcnet/0/LUN#0/Config/http/GuestPort" 8080
VBoxManage setextradata "winxp" \
"VBoxInternal/Devices/pcnet/0/LUN#0/Config/http/HostPort" 8080
```I aware, it is not very elegant solution. But all I need it for is just testing some of my scripts in IE7, IE8

Edit: Almost forgot. I also issued the following command:
```
iptables -t nat -I PREROUTING -p tcp --dport 8080 -j DNAT --to-destination 127.0.0.3
```

Btw, in Windows 7 I needed follow a [workaround]("http://support.microsoft.com/kb/923947") to edit c:\windows\system32\drivers\etc\hosts since it said I have no permissions.
But Windows XP worked without problems. And it runs much faster in VBox.

---

### Post by r.osmanov on 2009-12-26
> **r.osmanov said:**
> 
...
VBoxManage setextradata "winxp" \
"VBoxInternal/Devices/pcnet/0/LUN#0/Config/http/Protocol" TCP
...

Yes, it worked in Windows XP. I just tried to launch it on any Windows :)
But similar commands successfully forward port for Windows 7 too.

---

