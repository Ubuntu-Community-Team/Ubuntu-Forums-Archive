---
title: "Crazy strange network issue where HTTP request hangs"
date: 2012-10-04
forum: Networking &amp; Wireless
---

### Post by kanedase7en on 2012-10-04
Hi all,

Have a really strange problem which has been driving me crazy. When I try to resolve a domain it hangs. I've tested with both wget and curl (result pasted below - notice the 49:17 request time without response, yes, that's 50 minutes!), just in case it was a browser issue (tested with Firefox, Chrome, Opera and SeaMonkey), but the same happens from shell. Pinging the URL works because I assume the first node resolves, it just hangs on the second forwarded location.

But wait, here's the "real" issue: It ONLY happens until now with [http://www.google.com](http://www.google.com) (please bare with me). I have 2 other laptops with the same OS (Ubuntu 11.04), and they work perfect. NO ISSUE. Am I losing my mind? Could this possibly be malware?

Thank you in advance to anyone who can help.


$ uname -a
Linux homedev 2.6.38-16-generic #67-Ubuntu SMP Thu Sep 6 17:58:38 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux


$ ifconfig
eth0      Link encap:Ethernet  HWaddr 78:ac:c0:5b:4a:6d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1495 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1495 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:201227 (201.2 KB)  TX bytes:201227 (201.2 KB)

wlan0     Link encap:Ethernet  HWaddr 1c:65:9d:e2:6b:f2  
          inet addr:192.168.1.128  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::1e65:9dff:fee2:6bf2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:83519 errors:0 dropped:0 overruns:0 frame:0
          TX packets:125590 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23481536 (23.4 MB)  TX bytes:149335230 (149.3 MB)
          Interrupt:11 Memory:ffffc900050c0000-ffffc900050c0100 


$ curl --location --verbose google.com
* About to connect() to google.com port 80 (#0)
*   Trying 173.194.34.201...   % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0connected
* Connected to google.com (173.194.34.201) port 80 (#0)
> GET / HTTP/1.1
> User-Agent: curl/7.21.3 (x86_64-pc-linux-gnu) libcurl/7.21.3 OpenSSL/0.9.8o zlib/1.2.3.4 libidn/1.18
> Host: google.com
> Accept: */*
> 
< HTTP/1.1 301 Moved Permanently
< Location: [http://www.google.com/](http://www.google.com/)
< Content-Type: text/html; charset=UTF-8
< Date: Thu, 04 Oct 2012 17:50:23 GMT
< Expires: Sat, 03 Nov 2012 17:50:23 GMT
< Cache-Control: public, max-age=2592000
< Server: gws
< Content-Length: 219
< X-XSS-Protection: 1; mode=block
< X-Frame-Options: SAMEORIGIN
< 
* Ignoring the response-body
{ [data not shown]
100   219  100   219    0     0   1175      0 --:--:-- --:--:-- --:--:--  3590* Connection #0 to host google.com left intact
* Issue another request to this URL: 'http://www.google.com/'
* About to connect() to [www.google.com](www.google.com) port 80 (#1)
*   Trying 212.106.221.23... connected
* Connected to [www.google.com](www.google.com) (212.106.221.23) port 80 (#1)
> GET / HTTP/1.1
> User-Agent: curl/7.21.3 (x86_64-pc-linux-gnu) libcurl/7.21.3 OpenSSL/0.9.8o zlib/1.2.3.4 libidn/1.18
> Host: [www.google.com](www.google.com)
> Accept: */*
> 
  0   219    0     0    0     0      0      0 --:--:--  0:49:17 --:--:--     0


$ ping google.com
PING google.com (173.194.34.206) 56(84) bytes of data.
64 bytes from mad01s08-in-f14.1e100.net (173.194.34.206): icmp_req=1 ttl=56 time=111 ms
64 bytes from mad01s08-in-f14.1e100.net (173.194.34.206): icmp_req=2 ttl=56 time=36.9 ms
64 bytes from mad01s08-in-f14.1e100.net (173.194.34.206): icmp_req=3 ttl=56 time=78.3 ms
64 bytes from mad01s08-in-f14.1e100.net (173.194.34.206): icmp_req=4 ttl=56 time=98.9 ms
^C
--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3003ms
rtt min/avg/max/mdev = 36.961/81.428/111.546/28.283 ms


$ traceroute google.com
traceroute to google.com (173.194.34.200), 30 hops max, 60 byte packets
 1  192.168.1.1 (192.168.1.1)  1.924 ms  2.024 ms  3.467 ms
 2  1.224.222.87.dynamic.jazztel.es (87.222.224.1)  35.101 ms  35.456 ms  36.146 ms
 3  10.255.5.254 (10.255.5.254)  64.945 ms  68.373 ms  68.416 ms
 4  102.217.106.212.static.jazztel.es (212.106.217.102)  44.825 ms 110.217.106.212.static.jazztel.es (212.106.217.110)  45.824 ms 102.217.106.212.static.jazztel.es (212.106.217.102)  45.786 ms
 5  109.217.106.212.static.jazztel.es (212.106.217.109)  44.671 ms  45.863 ms  45.794 ms
 6  254.216.106.212.static.jazztel.es (212.106.216.254)  53.943 ms  35.877 ms  36.087 ms
 7  2.217.106.212.static.jazztel.es (212.106.217.2)  34.672 ms  35.079 ms  35.053 ms
 8  216.239.49.196 (216.239.49.196)  36.728 ms  36.102 ms  36.662 ms
 9  72.14.237.124 (72.14.237.124)  38.013 ms  37.379 ms  38.274 ms
10  mad01s08-in-f8.1e100.net (173.194.34.200)  37.606 ms  38.579 ms  39.164 ms

---

### Post by AndroidICS on 2012-10-04
I am new to Ubuntu (And other than Android, Linux period) but I would guess  your Internet connection is not configured properly. Or you may need to reinstall Ubuntu on that computer, maybe that would fix it.

---

### Post by mevun on 2012-10-04
Since there is some unknown link inside the google.com page that is hanging, then that is probably just a DNS issue for that particular domain name in that link.

A reason that not all of your PCs have this problem could be that the DNS cache has already expired on the failing PC.  So this is the only one PC (out of your 3) that needs to resolve the domain name.  If the domain name is not resolvable right now, then it fails even as the other PCs with a cached entry still reach the IP of that domain name.

In other words, you don't need malware to have this problem.

---

### Post by kanedase7en on 2012-10-04
> **mevun said:**
> Since there is some unknown link inside the google.com page that is hanging, then that is probably just a DNS issue for that particular domain name in that link.

A reason that not all of your PCs have this problem could be that the DNS cache has already expired on the failing PC.  So this is the only one PC (out of your 3) that needs to resolve the domain name.  If the domain name is not resolvable right now, then it fails even as the other PCs with a cached entry still reach the IP of that domain name.

In other words, you don't need malware to have this problem.

Thanks for the prompt reply mevun. The strange thing is, that when loading the domain in a browser it displays correctly (shows the Google logo with the search box), but any subsequent request (i.e: searching), the request hangs. So, it works for the first request, but fails after that, as demonstrated with curl in my example.

The only way to get it to resolve again is to RESET my internet connection - in Ubuntu, from the network icon in the taskbar (gnome2) clicking the icon of my active WiFi connection in the popup menu to reconnect - then it magically works again. That's an important fact I'm not sure if I stated in my post: I'm using a WiFi connection, not cable.

---

### Post by mevun on 2012-10-04
> **kanedase7en said:**
> Thanks for the prompt reply mevun. The strange thing is, that when loading the domain in a browser it displays correctly (shows the Google logo with the search box), but any subsequent request (i.e: searching), the request hangs. So, it works for the first request, but fails after that, as demonstrated with curl in my example.

The only way to get it to resolve again is to RESET my internet connection - in Ubuntu, from the network icon in the taskbar (gnome2) clicking the icon of my active WiFi connection in the popup menu to reconnect - then it magically works again. That's an important fact I'm not sure if I stated in my post: I'm using a WiFi connection, not cable.

I don't know much about WiFi, but I agree then that it isn't a DNS caching problem that I described.  I have read that Firefox has its own DNS cache; don't know if it can become corrupt or how/why resetting a wifi connection would help.

Anyway, I still doubt the cause is malware since I thought that is fairly rare for Linux, but I don't know how  you can further debug this problem either.

---

