---
title: "firefox 3.0.8 cannot load page in Ubuntu 9.04"
date: 2009-12-07
forum: Networking &amp; Wireless
---

### Post by elaine81 on 2009-12-07
Hi all , 

as abv , i tried all kind of web address , but it always show " page cannot be loaded" , or " Address Not Found." Wifi enabled , already connected . Pls guide me , as i am a new user of Ubuntu . I dun hv the recovery cd for my Acer laptop , so i install Ubuntu. I have posted this topic in the software clinic but nobody seem to know how to resolve this issue. My Laptop model is Acer Travelmate 2420. 


The only info i hv from my ubuntu is:

[B][SIZE=1]My result back from adapter Setting

[/SIZE][/B]Link encap:Ethernet HWaddr 00:0a:e4:f5:9d:6c

UP BROASTCAST MULTICAST MTU: 1500 Metric:1

RX packets:0 errors:0 dropped:0 overruns:0 frame:0

TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

Collisions:0 txqueuelen:1000

RX bytes:0 (0.0 B) TX btyes:0 (0.0 B)

Interrupt:20 Base Address : 0x3000


**& then when i tried to ping to yahoo.com , the result :**

unknown host yahoo.com


Any Ubuntu Expert , pls help me with this , or my laptop will be left untouched , thanks !!! :-)

---

### Post by elaine81 on 2009-12-07
anyone ?

---

### Post by x33a on 2009-12-07
possibly a dns issue.

try opening this address: 74.125.53.100 (google)

if it opens google, then it's definitely a dns issue.

---

### Post by chili555 on 2009-12-07
> Wifi enabled , already connected .> Link encap:Ethernet HWaddr 00:0a:e4:f5:9d:6c

UP BROASTCAST MULTICAST MTU: 1500 Metric:1
--- snip ---This does not tell us if it is your ethernet interface or your wirless interface. It also shows no IP address, so there is no indication you are actually connected. Please open a terminal and do:```
iwconfig
```Please post the result.

---

### Post by elaine81 on 2009-12-07
> **chili555 said:**
> This does not tell us if it is your ethernet interface or your wirless interface. It also shows no IP address, so there is no indication you are actually connected. Please open a terminal and do:```
iwconfig
```Please post the result.
 
**As followed  , pls assist , thanks**
 
lo                  no wireless extensions
 
wmaster@      no wireless extensions
 
 
wlan@             IEEE 802.11bg    ESSID: "NETGEAR"
 
                       Mode:Managed Frequency:2.432 GHz  Access Point: Not-Associated
 
                       Tx-Power=20dBm
 
 
                       Retry min Limit:7  RTS thr:off Fragment thr=2352 B
 
 
                       Link Quality:0  Signal level:0 Noise level:0
 
 
                        Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
 
                       Tx excessive retries:0 Invalid misc:0 Missed beacon:0
 
pan0               no  wireless extensions.

---

### Post by elaine81 on 2009-12-07
upz....

---

### Post by diablo75 on 2009-12-07
Are you able to ping your own router?

Did you try to ping google via it's IP address (not "ping google.com" but "ping 74.125.53.100") as suggested above?

Do you have access to a different router (I ask this because I noticed the ESSID in your iwconfig says "NETGEAR", and I had a [VERY BAD experience with netgear ]("http://davestechsupport.com/blog/2009/05/30/ill-never-buy-a-netgear-router-again/")a few months ago).

It seems like you are successfully connecting to at least your router and to confirm your computer and it are talking to each other, you should ping it.  You should also ping another known IP address that is beyond your network (like that google address above).

On occasion I've had to enter my DNS server IP manually into Ubuntu, through System>Preferences>Network.  If you are able to ping your router, then you should be able to browse to it's configuration page via Firefox by entering it's IP address in the address bar at the top, then looking for the status page to see what address has been assigned to the router by your ISP.

---

### Post by elaine81 on 2009-12-07
> **diablo75 said:**
> Are you able to ping your own router?
 
Did you try to ping google via it's IP address (not "ping google.com" but "ping 74.125.53.100") as suggested above?
 
Do you have access to a different router (I ask this because I noticed the ESSID in your iwconfig says "NETGEAR", and I had a [VERY BAD experience with netgear ]("http://davestechsupport.com/blog/2009/05/30/ill-never-buy-a-netgear-router-again/")a few months ago).
 
It seems like you are successfully connecting to at least your router and to confirm your computer and it are talking to each other, you should ping it. You should also ping another known IP address that is beyond your network (like that google address above).
 
On occasion I've had to enter my DNS server IP manually into Ubuntu, through System>Preferences>Network. If you are able to ping your router, then you should be able to browse to it's configuration page via Firefox by entering it's IP address in the address bar at the top, then looking for the status page to see what address has been assigned to the router by your ISP.
 
Hi as per ur advise  , 
 
 hv ping facebook ( [69.63.181.15]("http://www.who.is/whois-ip/69.63.181.15/"))
 
& youswop ([202.157.168.87]("http://www.who.is/whois-ip/202.157.168.87/"))
 
 
 but both result :  Network is unreachable

---

### Post by elaine81 on 2009-12-07
> **elaine81 said:**
> Hi as per ur advise , 
 
hv ping facebook ( [69.63.181.15]("http://www.who.is/whois-ip/69.63.181.15/"))
 
& youswop ([202.157.168.87]("http://www.who.is/whois-ip/202.157.168.87/"))
but both result : Network is unreachable
 
 
 
Hi all , thanks a lot for all ur help , but somehow  i disabled & enable the wireless connection again. Now it's getting online , Thanks!!! will appreciate more help if i happen to bump into another problem in future  , thanks!!!;)

---

