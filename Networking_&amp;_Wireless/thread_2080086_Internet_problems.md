---
title: "Internet problems"
date: 2012-11-03
forum: Networking &amp; Wireless
---

### Post by umfunix on 2012-11-03
Hi

I/m at the end of my knowledge (and patience).  I'm struggling to get consistent internet connectivity.

For ex: I can ping my mail pop address but can't open any web site.  Then suddenly, I will be able to open google, but not ubuntuforums.org.  Keep on trying, I manage to open ubuntuforums (hence I'm writing this....) but then can't open any other web sites (like linuxquestions.org) .

Results for pinging a dns server looks good...
```
PING 196.36.199.229 (196.36.199.229) 56(84) bytes of data.
64 bytes from 196.36.199.229: icmp_req=1 ttl=58 time=18.6 ms
64 bytes from 196.36.199.229: icmp_req=2 ttl=58 time=18.8 ms
64 bytes from 196.36.199.229: icmp_req=3 ttl=58 time=18.4 ms
64 bytes from 196.36.199.229: icmp_req=4 ttl=58 time=18.6 ms
64 bytes from 196.36.199.229: icmp_req=5 ttl=58 time=18.3 ms
64 bytes from 196.36.199.229: icmp_req=6 ttl=58 time=18.0 ms

```Pinging a host name is very inconsistent....or even suddenly "unknown host" which means there is no connection?  But, immediately after the hostname reply "unknown host", I can ping an IP address (that of the dns server) with no problem.

Pinging the exact same host, first with the IP address and then with the host name, replies differently.
IP ping of a mail server
```
PING 78.46.7.31 (78.46.7.31) 56(84) bytes of data.
64 bytes from 78.46.7.31: icmp_req=1 ttl=50 time=222 ms
64 bytes from 78.46.7.31: icmp_req=2 ttl=50 time=221 ms
64 bytes from 78.46.7.31: icmp_req=3 ttl=50 time=221 ms
64 bytes from 78.46.7.31: icmp_req=4 ttl=50 time=222 ms

```The same mail server but with the host name...
```
64 bytes from dedi2031.nur4.host-h.net (78.46.7.31): icmp_req=1 ttl=50 time=223 ms
64 bytes from static.31.7.46.78.clients.your-server.de (78.46.7.31): icmp_req=2 ttl=50 time=650 ms
64 bytes from dedi2031.nur4.host-h.net (78.46.7.31): icmp_req=3 ttl=50 time=221 ms
64 bytes from static.31.7.46.78.clients.your-server.de (78.46.7.31): icmp_req=4 ttl=50 time=223 ms
64 bytes from 78.46.7.31: icmp_req=5 ttl=50 time=222 ms
64 bytes from dedi2031.nur4.host-h.net (78.46.7.31): icmp_req=6 ttl=50 time=221 ms
64 bytes from static.31.7.46.78.clients.your-server.de (78.46.7.31): icmp_req=7 ttl=50 time=221 ms
64 bytes from dedi2031.nur4.host-h.net (78.46.7.31): icmp_req=8 ttl=50 time=221 ms
64 bytes from 78.46.7.31: icmp_req=9 ttl=50 time=222 ms
64 bytes from static.31.7.46.78.clients.your-server.de (78.46.7.31): icmp_req=10 ttl=50 time=222 ms
64 bytes from 78.46.7.31: icmp_req=11 ttl=50 time=222 ms
64 bytes from 78.46.7.31: icmp_req=12 ttl=50 time=225 ms
64 bytes from 78.46.7.31: icmp_req=13 ttl=50 time=222 ms
64 bytes from 78.46.7.31: icmp_req=14 ttl=50 time=222 ms
64 bytes from 78.46.7.31: icmp_req=15 ttl=50 time=222 ms
64 bytes from 78.46.7.31: icmp_req=16 ttl=50 time=222 ms
64 bytes from 78.46.7.31: icmp_req=17 ttl=50 time=222 ms
64 bytes from 78.46.7.31: icmp_req=18 ttl=50 time=222 ms

```At the same time while this inconsistent connectivity happens, I can't setup my email account - assumably of the Internet connection...

nslookup [www.google.com]("http://www.google.com") give me this
```
Server:        127.0.0.1
Address:    127.0.0.1#53

Non-authoritative answer:
*** Can't find www.google.com: No answer


```...and then suddenly, this...
```
Server:        127.0.0.1
Address:    127.0.0.1#53

Non-authoritative answer:
Name:    google.com
Address: 173.194.34.163
Name:    google.com
Address: 173.194.34.162
Name:    google.com
Address: 173.194.34.161
Name:    google.com
Address: 173.194.34.174
Name:    google.com
Address: 173.194.34.166
Name:    google.com
Address: 173.194.34.169
Name:    google.com
Address: 173.194.34.165
Name:    google.com
Address: 173.194.34.164
Name:    google.com
Address: 173.194.34.167
Name:    google.com
Address: 173.194.34.160
Name:    google.com
Address: 173.194.34.168


```OK, the picture is probably clear.  Can anyone explain to me why this is happening and how to fix this.  

My settings are as follows:
I'm connecting wireless from this laptop  to my router, which connects via dsl to the internet.  The router is  setup with DHCP.  My laptop was set up to receive all DHCP.  Because it  didn't want to work, I changed it to only IP and entered the DNS  settings.  IPv6 is on full automatic.



Could it be that some sites are genuinely not available, because as I'm typing this, linuxquestions are still not available while I can google....

And while alllllll this was happening on my Ubuntu 12.0.4 TLS, I was able to browe the internet very consistently on my Windows laptop with the exact dsl, wireless config, DHCP config etc.

HELP, thanks. :)

OH, of course, I couldn't post this.  Had to try and wait and try....

---

### Post by umfunix on 2012-11-03
Update

I was installing quite a few apps through the terminal (apt-get).  It didn't seem to have any complaints with "not finding any site".

---

