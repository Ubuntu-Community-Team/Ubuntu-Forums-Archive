---
title: "Cannot get online - network issue"
date: 2006-06-15
forum: Networking &amp; Wireless
---

### Post by explosive on 2006-06-15
Hi,

I'm having some problems getting online with Xubuntu 6.06. I have been using Ubuntu 5.04 but decided to update to 6.06 today (I decided to use xubuntu as I fancied trying out another desktop environment). I did a clean install of xubuntu and I have tried setting up my wireless adaptor on my laptop exactly the same way that I did in 5.04 but I cannot get onto the internet.

I connect to the internet via a wireless router. I use static IPs for my machines rather than DHCP. I have entered all the detailes including essid/wep key/IP/subnet and the dns servers and I cannot access any websites. The only page that I can access is my router's config page, which shows that the network itself is working.

Also when I click "ok" to exit the network tool it takes a long time to close. (It blanks all the controls out and the "waiting" pointer remains on the screen. It takes a couple of minutes for the networking tool to close).

Any ideas?

---

### Post by kripkenstein on 2006-06-15
Some more data would be helpful. Can you ping any sites? (try 4.2.2.2, for example). Does DNS work? What is the output of ifconfig and iwconfig?

---

### Post by explosive on 2006-06-15
Ping

```

PING 4.2.2.2 (4.2.2.2) 56(84) bytes of data.
64 bytes from 4.2.2.2: icmp_seq=1 ttl=247 time=88.3 ms
64 bytes from 

4.2.2.2: icmp_seq=2 ttl=247 time=89.3 ms
64 bytes from 4.2.2.2: icmp_seq=3 ttl=247 time=88.0 ms
64 bytes from 

4.2.2.2: icmp_seq=4 ttl=247 time=88.5 ms

--- 4.2.2.2 ping statistics ---
4 packets transmitted, 4 received, 0% 

packet loss, time 3002ms
rtt min/avg/max/mdev = 88.065/88.567/89.362/0.531 ms

```

ifconfig
```

eth1      Link encap:Ethernet  HWaddr 00:0E:35:B1:F2:CB  
          inet addr:10.20.251.179  Bcast:10.20.251.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:35ff:feb1:f2cb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:63 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:2254 (2.2 KiB)  TX bytes:3325 (3.2 KiB)
          Interrupt:10 Base address:0xc000 Memory:d0001000-d0001fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:172 (172.0 b)  TX bytes:172 (172.0 b)



```

iwconfig

```

eth1      IEEE 802.11g  ESSID:"{my essid}"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:30:F1:E9:E7:14   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=80/100  Signal level=-49 dBm  Noise level=-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:6



```

How do I check to see if DNS is working?

---

### Post by kripkenstein on 2006-06-15
To see if DNS works, try

```
host www.google.com
```

Well, ping works - so you CAN access the 'net. Ifconfig and iwconfig also seem fine, at first glance. Post your result to the host command above and we'll have a more complete picture.

Also - what error message do you get, when you try to access a web site?

---

### Post by explosive on 2006-06-15
I get a "connection times out, no host could be found" message when I do the host command. 

When I try to access a website I get a "this page could not be found" message after a long time waiting for it to time out.

I guess the problem is to do with the DNS. I'm not sure what it could be because I have entered both the DNS servers just as I did with the ubuntu 5.04.

---

### Post by kripkenstein on 2006-06-15
Let's make sure that DNS is the issue: try to connect to these IPs in a browser window:

```

66.249.93.99
66.249.93.104

```

and see what happens.

EDIT: Also, see what happens when you ping them.

---

### Post by explosive on 2006-06-15
The Ips both take me straight to google.

The pings are also fine.

It appears there is a problem translating the domain name to the relevant IP address.

---

### Post by kripkenstein on 2006-06-15
Ok, so at this point we are 100% sure that you have a DNS problem only.

Look at /etc/resolv.conf, that contains the nameservers (there is also a GUI way to do it, I believe). But what the nameservers should be, depends on your isp, etc. You need to make sure the numbers there are accurate.

---

### Post by explosive on 2006-06-15
Solved!

I have a really big apology to make! After looking in resolv.conf I realised I had entered 217.159.... rather than 212.159.... ! This is all because I had the DNS servers written down on a scrubby bit of paper with my poor handwriting!

I'm very sorry for wasting your time on this one :oops:  and thanks you for all your help :)

---

### Post by kripkenstein on 2006-06-15
No problem. I'm glad things worked out.

---

