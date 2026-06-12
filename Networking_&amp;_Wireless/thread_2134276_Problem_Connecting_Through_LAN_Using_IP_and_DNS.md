---
title: "Problem Connecting Through LAN Using IP and DNS"
date: 2013-04-10
forum: Networking &amp; Wireless
---

### Post by Ashfaqur Rahman on 2013-04-10
I want to know my computer's IP address and DNS to make a LAN connection.
How Can I Know?

I am using ubuntu 12.10.

---

### Post by chili555 on 2013-04-10
Please open a terminal and run:```
nm-tool
```

---

### Post by somethingcatchy on 2013-04-10
There is a really handy set of tools in the repos called "net-tools". I don't know if it's included with your distro. If not then:

```
sudo apt-get install net-tools
```

will install it.

It includes arp, ifconfig, netstat, rarp, nameif, route, and utilities relating to particular network hardware types (plipconfig, slattach, mii-tool) and advanced aspects of IP configuration (iptunnel, ipmaddr).

ifconfig will yield an output like this:

```
eth0      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1462 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1497 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1483541 (1.4 MB)  TX bytes:192495 (192.4 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7455 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7455 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:380973 (380.9 KB)  TX bytes:380973 (380.9 KB)

wlan0     Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1053 (1.0 KB)  TX bytes:4766 (4.7 KB)
```

Then if you

```
dig www.google.com
```

the results wll include your name server. (You may need to install "dnsutils" to get dig.)

You can also:

```
cat /etc/resolv.conf
```

to get your name servers depending on how you set things up.

If you're in an old style destop GUI and have network-manager + network-manager-gnome installed you can also right click the network connections icon in the task bar and check connection information (no idea where that is in unity though).

Hope this helps.

---

### Post by Ashfaqur Rahman on 2013-04-10
thinkI I have net-tools as after giving code:
```

ifconfig

```

I got those eth0, lo ,wolan0.

I have dnsutils also as after giving
```

dig www.google.com

```

I got this
```

; <<>> DiG 9.8.1-P1 <<>> www.google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 38049
;; flags: qr rd ra; QUERY: 1, ANSWER: 6, AUTHORITY: 0, ADDITIONAL: 0


;; QUESTION SECTION:
;www.google.com.			IN	A


;; ANSWER SECTION:
www.google.com.		100	IN	A	74.125.129.147
www.google.com.		100	IN	A	74.125.129.103
www.google.com.		100	IN	A	74.125.129.106
www.google.com.		100	IN	A	74.125.129.104
www.google.com.		100	IN	A	74.125.129.105
www.google.com.		100	IN	A	74.125.129.99


;; Query time: 382 msec
;; SERVER: 156.154.70.1#53(156.154.70.1)
;; WHEN: Thu Apr 11 04:12:03 2013
;; MSG SIZE  rcvd: 128



```

Is This "156.154.70.1" my DNS?

Actually i am trying to connect my Desktop(win8) and laptop(Ubuntu 12.10) through LAN.
In my Desktop Its Saying " Unidentified network ".
In laptop ubuntu gets connection and try to connect and after sometimes it gets disconnected!!

So i am trying to make this network identified in desktop by giving my laptops IP and DNS.

---

### Post by chili555 on 2013-04-10
What did nm-tool say?

---

### Post by Ashfaqur Rahman on 2013-04-10
It says

```

NetworkManager Tool


State: disconnected


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             unavailable
  Default:           no
  HW Address:        9C:2A:70:37:ED:6F


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             disconnected
  Default:           no
  HW Address:        E0:DB:55:D5:8C:C1


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on



```

---

### Post by chili555 on 2013-04-10
You seem to be disconnected from both wired and wireless and so no IP and DNS are shown.

---

### Post by somethingcatchy on 2013-04-10
Well, I'm just learning myself. So I may not be able to give you all the answers. One of the gurus may have to pick this up and run with it. But, I'll give what help I can.

Yes, 156.154.70.1 is the address that you are curently using to resolve DNS. That is an address for [DNS Advantage]("https://en.wikipedia.org/wiki/DNS_Advantage").

You (or someone) would have had to manually have set up your system to use them to resolve DNS.

This could have been done in any of several ways. One of the gurus has actually been helping me fix a DNS issue on here for the last day or so.

If you look at the thread I started about not being able to connect to any wifi but my own there is a lot of stuff in there that can help you look through your system and see where DNS is fouled up.

In my case I ended up have to do a lot of system repairs because I broke some stuff. You may not need to do anything more than change a configuration file or two.

Look through that thread, see if it gives you any ideas, and I'll help where I can.[URL="https://en.wikipedia.org/wiki/DNS_Advantage"]




[/URL]

---

### Post by Ashfaqur Rahman on 2013-04-10
Now I Am Trying To Make A Wired Connection Through LAN.
I want to connect my Desktop(Win 8) and laptop(Ubuntu 12.10) through LAN.
After giving LAN connection Windows 8 saying that I Have An Active Network But As It Is An **Unidentified** Network,  Access Type: **No Network Access!**
My ubuntu is trying to make a connection it says "connecting" but after sometimes it gets[B] disconnected!

[/B]So I am trying to make ubuntu identified by giving ip and DNS. @This Is For Network Experts

And thanks for your help. O:)  @ [**[COLOR=#000000]somethingcatchy[/COLOR]**]("http://ubuntuforums.org/member.php?u=1807763")

---

### Post by somethingcatchy on 2013-04-10
And most, if not all, of that will turn out to be DNS related. You're not resolving names in either windows or ubuntu. Which I would say (and remember I'm still learning too) is indicative of a wider network problem and not just a problem on the machine themselves. Although it could be a combo of both.

Are you trying to connect the machines through a wireless router, a wired router or did you have a dedicated gateway? Do you have samba installed? (I assume you're trying to share files between windows and ubuntu?)

---

### Post by Ashfaqur Rahman on 2013-04-10
Ok I am clearing it out.

Actually I am trying to make a wired connection between my Desktop(which is running windows 8) and my Laptop(which is running Ubuntu 12.10).
After making a wire connection(or LAN connection) between my Desktop And Laptop.
I have noticed My Laptop(Ubuntu) Is Trying To Connect To This Network(or my Desktop) But after sometimes it gets Disconnected!
And for my Desktop(Windows 8) its saying that it has found an active network which is public and Unidentified and access type is "No network access"!!
And I Cant Make A Connection Between My Laptop And Desktop Though I Have Turned Every Sharing Option On In My Desktop(Windows 8)!

So its clearly seen that my Desktop cant identify my laptop's wired network.So I thought that if i gave my desktop my laptop's(Ubuntu) IP and DNS it could identify this network(or my laptop).

after giving this code in terminal:
```

ifconfig -a

```

I get this:
```

eth0      Link encap:Ethernet  HWaddr e0:db:55:d5:8c:c1  
          inet6 addr: fe80::e2db:55ff:fed5:8cc1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:559 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2842 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:71633 (71.6 KB)  TX bytes:718844 (718.8 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9912 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9912 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:768544 (768.5 KB)  TX bytes:768544 (768.5 KB)


ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.128.24.192  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:26621 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29027 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:18329167 (18.3 MB)  TX bytes:4631559 (4.6 MB)


wlan0     Link encap:Ethernet  HWaddr 9c:2a:70:37:ed:6f  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



```

From this I can see that my IP is " 10.128.24.192 ".
and from:
```

dig www.google.com

```

I found my DNS " 156.154.70.1 ".

So I Give This IP and DNS in my Desktop's(Windows 8) Ethernet Properties IPV4 settings.
But yet it is not working!!Giving same problem  :(
Thats All.

---

### Post by Ashfaqur Rahman on 2013-04-10
Yahoo!

Just Got Connection!!

In Ubuntu(i mean my laptop) In After Going To **edit connection> wired> edit> IPV4 Settings> Method>**
It was set to "Automatic(DHCP)" I make it to **"Shared to other computer" **and connection Established!!!! :guitar:

Thanks everybody for help. :)

---

