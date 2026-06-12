---
title: "Network connection problem"
date: 2009-02-10
forum: Networking &amp; Wireless
---

### Post by Otu on 2009-02-10
I'm having some problems with my network on Ubuntu 8.10, i have cable internet with dynamic ip.

The first problem is that the network connection icon on the upright corner is showing little orange triangle and some of my programs, qBittorrent for example are claiming that im not connected to internet while the downloads are still going and internet browsing is working fine.

The second problem is that when I'm downloading somethings with qBittorrent or uTorrent, the downloads work fine for some time, but then suddenly they stop, no downloads or uploads are working, also i cannot browse internet with any browser, the network tools show that there is still going some packets in and out but only very few, also my ip address remains as it is when i have full working connection.

I have Firestarter firewall and I've tried to enable and disable port 80 and the ports that my torrent software uses, also i have tried this command: sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT

---

### Post by superprash2003 on 2009-02-10
try using this online port scanner to see if your ports are open [http://www.t1shopper.com/tools/port-scanner/](http://www.t1shopper.com/tools/port-scanner/) .. also post output of **ifconfig** from the temrinal

---

### Post by Otu on 2009-02-10
As i said in my first post, i cannot browse internet when it stops working after using bittorrent software for some time, usually less than an hour, so i cant use any online tools, and obviously my needed ports are open enough as my network connection works fine when i havent been using bittorrent software.

Here is the output of ifconfig:

```
eth1      Link encap:Ethernet  HWaddr 00:0b:6a:0e:b3:7a  
          inet addr:82.181.71.161  Bcast:82.181.71.255  Mask:255.255.248.0
          inet6 addr: fe80::20b:6aff:fe0e:b37a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:73700 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15076 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:30341976 (30.3 MB)  TX bytes:1534911 (1.5 MB)
          Interrupt:23 Base address:0xae00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:57 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2402 (2.4 KB)  TX bytes:2402 (2.4 KB)

```

---

### Post by Neural oD on 2009-02-10
It sounds like it could be due to faulty dns servers - check with your provider to see if there is issues with their dns

-also as a test - disable firestarter -and test - if no problems - then you need to look at your firestarter setup

---

### Post by Otu on 2009-02-10
I have already tried disabling Firestarted and it didnt help.

How can i test if there is problems with my ISP dns servers?  also could faulty dns servers cause my connection to shut down after about half an hour of bittorrent downloading? it doesnt happen in any other use that bittorrent, also the problem is gone when i restart my computer.

---

### Post by Neural oD on 2009-02-10
usually you need to get in touch with your providers - often they have other dns servers that you could use. Also some providers could try to shape your bandwidth or even block certain protocols - like torrents. I would recommend that u use encryption - and use random ports in your client - this should help

---

### Post by JK3mp on 2009-02-10
I know some ISP's are enforcing filters and blocks/bans on Torrent sites etc. so that could of maybe caused it. Consult your provider possibly about TOS.

---

### Post by Otu on 2009-02-10
Hm.. indeed they could be against torrent using.. thanks for the idea, i will now go to put the encryption to forced setup and wonder what ports and how should i use with qbittorrent, ill make a post after using bittorrent for an hour if it still crashes my internet or not :)

---

### Post by Neural oD on 2009-02-10
> **Otu said:**
> Hm.. indeed they could be against torrent using.. thanks for the idea, i will now go to put the encryption to forced setup and wonder what ports and how should i use with qbittorrent, ill make a post after using bittorrent for an hour if it still crashes my internet or not :)
never used qbittorrent - so can't help you there - but utorrent supports all that functionality. Another I recommend is rtorrent - it works on the command line - use with screen and ssh to control your torrents remotely. Rtorrent really rocks - but I'd recommend compiling from source - if u're up to it - as the ones in the repos tend to be a bit dated.

---

### Post by Otu on 2009-02-10
I decided to get Vuze (used to be called Azureus) as qbittorrent doesnt support other ports than the preset, which are most probably controlled by my ISP, now after an hour of downloading with Vuze, internet still works but Vuze says on diagnostic: No incoming connections received, likely NAT problems. I dont have NAT as far as i know.. but there is "new" thing when i do traceroute for any website (IP) there is IP address 10.204.0.1 which to me looks like some kind of router thingie, and thats the first bounce from my computer, after that there is my ISP server and so on..

anyways, if anyone knows how to fool the router which i dont have physical access to, please tell :)  thanks for the help for everyone, have some popcorn :popcorn:

---

