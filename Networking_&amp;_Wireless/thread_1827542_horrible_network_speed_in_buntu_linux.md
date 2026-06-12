---
title: "horrible network speed in buntu linux"
date: 2011-08-18
forum: Networking &amp; Wireless
---

### Post by shubham1 on 2011-08-18
im running ubuntu linux 11.04 with 1mbps connection my speed is horribel
0bytes/sec webpage refuse to opne files dont upload.in my bothers laptoprunning on same wifi connection
with windows has superb speed.i like everything execpt network probelm this problem is from when i install ubuntu linux.reinstalled to.

---

### Post by papibe on 2011-08-18
Could you post the result of these commands?
```
$ ifconfig

$ route -n

$ nslookup ubuntu.com

$ dig ubuntu.com
```
Regards.

---

### Post by shubham1 on 2011-08-18
ifconfig
```
eth0      Link encap:Ethernet  HWaddr bc:ae:c5:93:92:5d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3203 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3203 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1152058 (1.1 MB)  TX bytes:1152058 (1.1 MB)

wlan0     Link encap:Ethernet  HWaddr 00:a1:b0:ee:18:8d  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2a1:b0ff:feee:188d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25556 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25566 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13235805 (13.2 MB)  TX bytes:21648149 (21.6 MB)

```

---

### Post by shubham1 on 2011-08-18
$ route -n

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

```

---

### Post by shubham1 on 2011-08-18
ns lookup ubuntu.com:
Server:        192.168.1.1
Address:    192.168.1.1#53

Non-authoritative answer:
Name:    ubuntu.com
Address: 91.189.94.156

---

### Post by shubham1 on 2011-08-18
; <<>> DiG 9.7.3 <<>> ubuntu.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 52710
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;ubuntu.com.            IN    A

;; ANSWER SECTION:
ubuntu.com.        2    IN    A    91.189.94.156

;; Query time: 1787 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Thu Aug 18 13:26:15 2011
;; MSG SIZE  rcvd: 44

---

### Post by papibe on 2011-08-18
> **shubham1 said:**
> 
;; Query time: [COLOR="Red"]1787 msec[/COLOR]
Holly Cow!!

That's too long to resolve an address. It should be in the 2 digits range. Either your router has problems to relaying your DNS requests, or there's some problems with your ISP's DNS.

Try this as a test. Open Network connections. Goto Wireless. Select wlan0. Press Edit. Go to the IPv4 tab. Change the method to 'Automatic (DHCP) addresses only'. Put this on 'DNS Servers:'
```
 208.67.222.222, 208.67.220.220
```
(those are OpenDNS servers).

Restart your machine and see how the browsing experience goes.

Tell us how it went,
Regards.

---

### Post by shubham1 on 2011-08-18
there is no wlan0 my connection is Airtel

---

### Post by papibe on 2011-08-18
Did you try on the Airtel connection?

Regards.

---

### Post by shubham1 on 2011-08-19
thanks
yes the speed is icreased but still less than my borthers i have got to learn that
one tutorial tell me to do this
result here
shubham@workspace:~$ sudo iwconfig Airtel rate 54M
[sudo] password for shubham: 
Error for wireless request "Set Bit Rate" (8B20) :
    SET failed on device Airtel ; No such device.
shubham@workspace:~$

---

### Post by shubham1 on 2011-08-19
can you tell when i try to upgrade any software using apt-get upgrade
it does upgradetion for all softwares that i dont want i want to upgrade php,ubuntu one.
in my ubuntu one there is ednless sync.

---

### Post by shubham1 on 2011-08-19
my send speed is still very poor

---

### Post by collisionystm on 2011-08-19
> sudo iwconfig Airtel rate 54M

sudo iwconfig wlan0 rate 54M

---

### Post by shubham1 on 2011-08-19
> **collisionystm said:**
> sudo iwconfig wlan0 rate 54M
i already did it it gives a erorr but i did tried again
see my post
[http://ubuntuforums.org/showpost.php?p=11166523&postcount=10](http://ubuntuforums.org/showpost.php?p=11166523&postcount=10)

---

### Post by shubham1 on 2011-08-20
hello my speed is still low.

---

### Post by dineshs on 2011-08-20
collisionystm suggested sudo iwconfig wlan0 rate 54M not sudo iwconfig [COLOR="Red"]Airtel[/COLOR] rate 54M.Try running  [COLOR="Red"]sudo iwconfig wlan0 rate 54M[/COLOR]

---

### Post by shubham1 on 2011-08-21
> **dineshs said:**
> collisionystm suggested sudo iwconfig wlan0 rate 54M not sudo iwconfig [COLOR="Red"]Airtel[/COLOR] rate 54M.Try running  [COLOR="Red"]sudo iwconfig wlan0 rate 54M[/COLOR]
yes i runned it to it does nothing.

---

