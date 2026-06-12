---
title: "Local network access, No Internet"
date: 2011-09-07
forum: Networking &amp; Wireless
---

### Post by Coolcolly on 2011-09-07
Hello,

Still very new to Ubuntu.

I am running 11.04.

I have had network access for quite some time until I was playing around with EBOX. I have removed it completely, and don't have internet.

I have local access to it, but no outside internet. Verified IPv6 is set to ignored/off.

I verified all subnet, IP, and gateway are set correctly. Even tried setting it all back to DHCP to see if that would fix it.

Tried restarting the networking service, and the computer, still no luck.

I have done some research on the forums here, and tried a few suggestions but no luck.

Please let me know how to reset it back to defaults, and what information you may need.

Thank you!

---

### Post by Coolcolly on 2011-09-07
Does anyone have any requests for information they need to help me resolve this.

I know for a fact, I haven't provided enough information.

---

### Post by papibe on 2011-09-07
Could you post the result of these commands?
```
$ lspci -nn | grep -i net

$ sudo lshw -C network

$ ifconfig

$ route -n

$ nslookup ubuntu.com

$ dig ubuntu.com
```
Please use the # tags (CODE tags) to post your results.
Regards.

---

### Post by Coolcolly on 2011-09-07
> **papibe said:**
> Could you post the result of these commands?
```
$ lspci -nn | grep -i net

00:07.0 Bridge [0680]: nVidia Corporation MCP61 Ethernet [10de:03ef] (rev a2)

$ sudo lshw -C network

Briefly displays PCI (sysfs) then disappears.

$ ifconfig

eth0      Link encap:Ethernet  HWaddr f4:6d:04:e6:1d:d5  
          inet addr:192.168.1.122  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::f66d:4ff:fee6:1dd5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27225752 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14474323 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:40184508436 (40.1 GB)  TX bytes:1544667225 (1.5 GB)
          Interrupt:43 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6143 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6143 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:873665 (873.6 KB)  TX bytes:873665 (873.6 KB)

$ route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0

$ nslookup ubuntu.com

Server:		192.168.1.1
Address:	192.168.1.1#53

Non-authoritative answer:
Name:	ubuntu.com
Address: 91.189.94.156

$ dig ubuntu.com

; <<>> DiG 9.7.3 <<>> ubuntu.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 17656
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 3, ADDITIONAL: 3

;; QUESTION SECTION:
;ubuntu.com.			IN	A

;; ANSWER SECTION:
ubuntu.com.		539	IN	A	91.189.94.156

;; AUTHORITY SECTION:
ubuntu.com.		25481	IN	NS	ns2.canonical.com.
ubuntu.com.		25481	IN	NS	ns1.canonical.com.
ubuntu.com.		25481	IN	NS	ns3.canonical.com.

;; ADDITIONAL SECTION:
ns1.canonical.com.	28265	IN	A	91.189.94.173
ns2.canonical.com.	28265	IN	A	91.189.94.219
ns3.canonical.com.	30863	IN	A	209.6.3.210

;; Query time: 12 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Wed Sep  7 18:14:02 2011
;; MSG SIZE  rcvd: 156
```



Here are the results for everything you asked me to run. Oh and I am using Firefox as the default web browser for web surfing.

---

### Post by papibe on 2011-09-07
It looks you don't have a default route. Try running this:

```
$ sudo route add default gw 192.168.1.1 eth0
```
Then check if the route is sticking:
```
$ route -n
```
It should be a line like this:
```
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
```
If it's there, try accessing the Internet using Firefox (it may be necessary restart Firefox).

Tell us how it goes,
Regards.

---

### Post by gvanleijen on 2011-09-14
@Coolcolly, Thanks for asking this question - i'm suffering from the same problems
@papibe, Thanks for that answer, it helped me out. After applying your solution Internet works but after a reboot it stops working again.

Any thoughts?

Thanks in advance!

---

### Post by HugoSerrano on 2011-09-14
Show us your /etc/network/interfaces file.


Regards!

---

### Post by gvanleijen on 2011-09-15
```
auto lo
iface lo inet loopback
```

it's a new installation.

tia,

Cheers,

---

### Post by HugoSerrano on 2011-09-15
humm...

if you do:
#sudo dhclient eth0

works?

---

### Post by gvanleijen on 2011-09-15
nope, it tells me that after several retries there is not dhcpserver available, which is true because there is none in this network. that's why i'm trying to configure it manually.

after that even local network didn't work any more, which was solved after a reboot

i'll try to post the displayed lines later today.

---

### Post by dineshs on 2011-09-15
If you are using networkmanager for configuring devices try [this]("http://ubuntuforums.org/showpost.php?p=9467538&postcount=5")

---

### Post by HugoSerrano on 2011-09-16
> **dineshs said:**
> If you are using networkmanager for configuring devices try [this]("http://ubuntuforums.org/showpost.php?p=9467538&postcount=5")

if not, your /etc/network/interfaces should look like:

> 

auto lo
iface lo inet loopback


auto eth0
iface eth0 inet static
    address 192.168.1.122
    netmask 255.255.255.0
    network 192.168.1.0
    nameserver 192.168.1.1
    broadcast 192.168.1.255
    gateway 192.168.1.1



And your /etc/resolv.conf

> 
nameserver 192.168.1.1
domain your.domain
search your.domain


---

### Post by Coolcolly on 2011-10-10
To fix the issue, I added the line ```
gateway 192.168.1.1
``` to /etc/network/interfaces.

My end result of this file looks like this.

```
auto lo eth0

iface lo inet loopback
iface eth0 inet static
        address 192.168.1.122
        netmask 255.255.255.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
```

Thank you all for your help! :)

---

