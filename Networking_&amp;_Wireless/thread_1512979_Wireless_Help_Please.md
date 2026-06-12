---
title: "Wireless Help Please"
date: 2010-06-18
forum: Networking &amp; Wireless
---

### Post by jonathonwebb on 2010-06-18
I have Ubuntu Lucid loaded on an old Compaq Armada E500 Laptop (used to run Windows 2k). I'm having issues when I try to access the internet using my D-link DWA-652 pcmcia wireless card. It appears to be connected to the network, and even pings successfully , but when I go to get on the internet in Chrome or Firefox, it says the server is not available. I would like to get this fixed so i won't have to go back to Windows (scary thought).

---

### Post by ElderDarkReaper on 2010-06-18
I think I may be having a similar problem. Can you access local site? (eg router). While connected to Wireless the only thing I can do is connect local sites and install packages from the net (wtf) but no browsing. This is a fresh install of Ubuntu 10.04 with only the updates installed (didn't work before updates either).

I Also have a USB Wireless Mobile Broadband for when I am not home, and with that in, I can browse using that.

Any Ideas?

---

### Post by varunendra on 2010-06-19
> **jonathonwebb said:**
> I'm having issues when I try to access the internet using my D-link DWA-652 pcmcia wireless card. It appears to be connected to the network, and even pings successfully , but when I go to get on the internet in Chrome or Firefox, it says the server is not available.
Are you sure you have got the gateway address?
post here the output of following commands:```
ifconfig -a
``` & ```
route -n
```
> **ElderDarkReaper said:**
> While connected to Wireless the only thing I can do is connect local sites and install packages from the net (wtf) but no browsing.
What do you mean by local sites?
Can you connect to the Ubuntu servers for downloading the packages?

---

### Post by ElderDarkReaper on 2010-06-19
> **varunendra said:**
> 
What do you mean by local sites?
Can you connect to the Ubuntu servers for downloading the packages?

Well Synaptic can connect and download/install packages, but firefox, or any other browser can't. This includes Rhythmbox as well. 
I can't browse to the package sites using a web browser either.

By local sites I mean the router and the printer. (They have web interfaces)

However when I'm connected with the Wireless Mobile Broadband USB Stick it all works. Also on my windows pc the wireless works fine.

```
ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:1d:72:13:52:74  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:23604 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23604 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:120.21.58.43  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 

wlan0     Link encap:Ethernet  HWaddr 00:1e:4c:a5:38:f4  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:4cff:fea5:38f4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:207271 errors:0 dropped:0 overruns:0 frame:0
          TX packets:134143 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 

route -n

10.64.64.64     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
```

---

### Post by varunendra on 2010-06-19
> **ElderDarkReaper said:**
> Well Synaptic can connect and download/install packages, but firefox, or any other browser can't. This includes Rhythmbox as well. 
I can't browse to the package sites using a web browser either.

By local sites I mean the router and the printer. (They have web interfaces)

However when I'm connected with the Wireless Mobile Broadband USB Stick it all works. Also on my windows pc the wireless works fine.

Your WLan has both valid IP & Gateway. As you said it is a fresh install, it may be a DNS issue then.
Post here the output of 'dig' command.```
dig
```
Also, log on to your Windows pc where the wireless is working. While it is working, do as told [here]("http://ubuntuforums.org/showpost.php?p=9424917&postcount=3") & post the results here.

Be informed though- I'm not an expert at it. But if the issue is with DNS, the solution would be rather simple.

---

### Post by ElderDarkReaper on 2010-06-20
> **varunendra said:**
> Your WLan has both valid IP & Gateway. As you said it is a fresh install, it may be a DNS issue then.
Post here the output of 'dig' command.```
dig
```
Also, log on to your Windows pc where the wireless is working. While it is working, do as told [here]("http://ubuntuforums.org/showpost.php?p=9424917&postcount=3") & post the results here.

Be informed though- I'm not an expert at it. But if the issue is with DNS, the solution would be rather simple.
```


; <<>> DiG 9.7.0-P1 <<>>
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 21300
;; flags: qr rd ra; QUERY: 1, ANSWER: 13, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;.				IN	NS

;; ANSWER SECTION:
.			37975	IN	NS	m.root-servers.net.
.			37975	IN	NS	c.root-servers.net.
.			37975	IN	NS	e.root-servers.net.
.			37975	IN	NS	l.root-servers.net.
.			37975	IN	NS	b.root-servers.net.
.			37975	IN	NS	k.root-servers.net.
.			37975	IN	NS	g.root-servers.net.
.			37975	IN	NS	f.root-servers.net.
.			37975	IN	NS	j.root-servers.net.
.			37975	IN	NS	d.root-servers.net.
.			37975	IN	NS	h.root-servers.net.
.			37975	IN	NS	i.root-servers.net.
.			37975	IN	NS	a.root-servers.net.

;; Query time: 330 msec
;; SERVER: 8.8.8.8#53(8.8.8.8)
;; WHEN: Sun Jun 20 15:51:18 2010
;; MSG SIZE  rcvd: 228


```
See attached file for ipconfig.

---

### Post by varunendra on 2010-06-20
Well... now I am a bit puzzled.
It has a valid DNS address too! (8.8.8.8, it's a google's open DNS)

However, the expected 'Additional Section' is missing in the output of your dig command (Additional: 0). But I can't say if it is normal or abnormal. It maybe normal in the sense that if it were there, then perhaps you wouldn't have had any problems at all ;).

Since I've got no clue what the reason maybe for this behavior, I can only speculate a few ones:

[LIST=1]
[*]It may be a firewall issue (you can install gufw tool via synaptic to check/manage it)
[*]You may try other open DNS servers (google for them)
[*]FF browser somehow set to use a proxy server & others imported the same settings. (check tools>options>advance>network>settings in FireFox. it should be set to 'No Proxy')
[*]Browsers are set to work in 'Offline' mode. (check File>Work Offline. It shouldn't be checked!)
[*]A reason that is beyond my imagination or my knowledge at the moment :(
[/LIST]
Now speculation1 is unlikely, 3 is highly unlikely & 4 is most likely. But you should check all of 1, 2 & 3 to be sure.


I'd like you to try one more thing. Try pinging google.com or any other common site to see if you can get a reply. Plus, post the output of following command:```
dig www.google.com
``` (you can change google.com with any other internet site if it can give you the 'Additional Section' in the output).



EDIT: @Jonathon & D.Reaper, have you tried your wireless while running a Live session (from Live CD)? How does it go then?

---

