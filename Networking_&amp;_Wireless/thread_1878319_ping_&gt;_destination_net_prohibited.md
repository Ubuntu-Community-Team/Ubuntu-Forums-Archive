---
title: "ping &gt; destination net prohibited"
date: 2011-11-09
forum: Networking &amp; Wireless
---

### Post by danube on 2011-11-09
Hi friends!

I've checked in to a hotel which provides wifi. Connection is set up with DHCP and I'm bonded with the access point.

Now my browser should be redirected to a site where I can enter the credentials I've got at the desk. That page is not opening. When I type an address and hit the go button, I see another address loading in the status bar (hotspot.hhi.local). But the page never loads! Firefox says: Server not found.

Doing a ping to Google or any other site,the IP address seems to be resolved correctly as it is always pinging a different IP for each address I'm pinging to.

Okay, here's the network setup I receive from the DHCP:
IP: 10.21.0.248
Bcast: 10.21.255.255
Mask: 255.255.0.0

I also find inet6 data in ifconfig. Here is what it's saying:
fe80::21b::77ff::fe00::7ef0/64

Strange thing: My mobile phone connects without a hassle!

I'd be really thankful if we could solve that.

Thanks! Tom

---

### Post by RedSingularity on 2011-11-10
Whats the output of:

ifconfig and iwconfig

---

### Post by danube on 2011-11-10
$ ifconfig

wlan1     Link encap:Ethernet  Hardware Adresse 00:1b:77:00:7e:f0  
          inet Adresse:10.21.0.248  Bcast:10.21.255.255  Maske:255.255.0.0
          inet6-Adresse: fe80::21b:77ff:fe00:7ef0/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:214 errors:0 dropped:0 overruns:0 frame:0
          TX packets:306 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:36425 (36.4 KB)  TX bytes:49173 (49.1 KB)


$ iwconfig

wlan1     IEEE 802.11abg  ESSID:"BESTWESTERN Hotel"  
          Mode:Managed  Frequency:2.472 GHz  Access Point: 00:0C:42:65:3F:4B   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=39/70  Signal level=-71 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:107   Missed beacon:0

---

### Post by jonobr on 2011-11-10
Go to application/accessories

open a terminal

try 

```
sudo tcpdump -vvv -i any port 80
```

Open your browser 
capture the results and hopefully that will capture the intial web request and redirect.

Post the results here

Lastly, 
post the result of ```
cat /etc/resolv.conf
```

hopefully its getting a dns server to resolve against

---

### Post by danube on 2011-11-10
Hi jonobr, thanks for helping me out. Here are the results:

$ sudo tcpdump -vvv -i any port 80
[sudo] password for tom: 
tcpdump: listening on any, link-type LINUX_SLL (Linux cooked), capture size 65535 bytes
20:34:49.192588 IP (tos 0x0, ttl 64, id 13544, offset 0, flags [DF], proto TCP (6), length 60)
    ai.local.43328 > [www.l.google.com.www:](www.l.google.com.www:) Flags [S], cksum 0x7d22 (incorrect -> 0x733f), seq 2889309893, win 14600, options [mss 1460,sackOK,TS val 879149 ecr 0,nop,wscale 4], length 0
20:34:49.194203 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto TCP (6), length 60)
    [www.l.google.com.www](www.l.google.com.www) > ai.local.43328: Flags [S.], cksum 0xf45e (correct), seq 1487953346, ack 2889309894, win 5792, options [mss 1460,sackOK,TS val 13756917 ecr 879149,nop,wscale 2], length 0
20:34:49.194232 IP (tos 0x0, ttl 64, id 13545, offset 0, flags [DF], proto TCP (6), length 52)
    ai.local.43328 > [www.l.google.com.www:](www.l.google.com.www:) Flags [.], cksum 0x7d1a (incorrect -> 0x3635), seq 1, ack 1, win 913, options [nop,nop,TS val 879149 ecr 13756917], length 0
20:34:49.194306 IP (tos 0x0, ttl 64, id 13546, offset 0, flags [DF], proto TCP (6), length 932)
    ai.local.43328 > [www.l.google.com.www:](www.l.google.com.www:) Flags [P.], cksum 0x39b4 (correct), seq 1:881, ack 1, win 913, options [nop,nop,TS val 879149 ecr 13756917], length 880
20:34:49.197474 IP (tos 0x0, ttl 64, id 46134, offset 0, flags [DF], proto TCP (6), length 52)
    [www.l.google.com.www](www.l.google.com.www) > ai.local.43328: Flags [.], cksum 0x2ef6 (correct), seq 1, ack 881, win 1888, options [nop,nop,TS val 13756917 ecr 879149], length 0
20:34:49.213537 IP (tos 0x0, ttl 64, id 46135, offset 0, flags [DF], proto TCP (6), length 191)
    [www.l.google.com.www](www.l.google.com.www) > ai.local.43328: Flags [P.], cksum 0x38a9 (correct), seq 1:140, ack 881, win 1888, options [nop,nop,TS val 13756918 ecr 879149], length 139
20:34:49.213562 IP (tos 0x0, ttl 64, id 13547, offset 0, flags [DF], proto TCP (6), length 52)
    ai.local.43328 > [www.l.google.com.www:](www.l.google.com.www:) Flags [.], cksum 0x7d1a (incorrect -> 0x31f1), seq 881, ack 140, win 980, options [nop,nop,TS val 879154 ecr 13756918], length 0
20:34:49.213908 IP (tos 0x0, ttl 64, id 46136, offset 0, flags [DF], proto TCP (6), length 827)
    [www.l.google.com.www](www.l.google.com.www) > ai.local.43328: Flags [FP.], cksum 0x3896 (correct), seq 140:915, ack 881, win 1888, options [nop,nop,TS val 13756918 ecr 879149], length 775
20:34:49.213928 IP (tos 0x0, ttl 64, id 13548, offset 0, flags [DF], proto TCP (6), length 52)
    ai.local.43328 > [www.l.google.com.www:](www.l.google.com.www:) Flags [.], cksum 0x7d1a (incorrect -> 0x2e88), seq 881, ack 916, win 1077, options [nop,nop,TS val 879154 ecr 13756918], length 0
20:34:49.214179 IP (tos 0x0, ttl 64, id 13549, offset 0, flags [DF], proto TCP (6), length 52)
    ai.local.43328 > [www.l.google.com.www:](www.l.google.com.www:) Flags [F.], cksum 0x7d1a (incorrect -> 0x2e87), seq 881, ack 916, win 1077, options [nop,nop,TS val 879154 ecr 13756918], length 0
20:34:49.233409 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto TCP (6), length 52)
    [www.l.google.com.www](www.l.google.com.www) > ai.local.43328: Flags [.], cksum 0x2b5a (correct), seq 916, ack 882, win 1888, options [nop,nop,TS val 13756920 ecr 879154], length 0


$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 10.21.0.1

 [/CODE]

---

### Post by jonobr on 2011-11-10
hello


what does ```
nslookup google.com
```
look like from a terminal?

does it give you an ip adress?

What about putting 
[http://74.125.224.82](http://74.125.224.82) into your browser

What does that show?

Looking at the output below, it looks as if there are packets being sent by google and received by you, 
I dont see any redirection
(unless and this is possible its happening on a port other the port 80)

---

### Post by danube on 2011-11-10
$ nslookup google.com
Server:		10.21.0.1
Address:	10.21.0.1#53

Non-authoritative answer:
Name:	google.com
Address: 74.125.39.147

Going to both your URL or the one above, Firefox says: Nachschlagen von hotspot.hhi.local (something like 'Looking for hotspot.hhi.local').

Looks as I'm being redirected somehow and on the other side I'm not. I'm really screwed, hum?

---

### Post by jonobr on 2011-11-10
What happens if you (and this is a complete stab in the dark)

nslookup hotspot.hhi.local

---

### Post by jonobr on 2011-11-10
on other thing
in firefox
Goto Tools > Options > Advanced > General : Accessibility "Warn me when web sites try to redirect or reload the page" 

How is that setup?

---

### Post by danube on 2011-11-10
```
$ nslookup hotspot.hhi.local
Server:		10.21.0.1
Address:	10.21.0.1#53

Non-authoritative answer:
Name:	hotspot.hhi.local
Address: 10.21.0.1
```

The setup in firefox is deactivated. When ticked, firefox brings a warning that the page is going to redirect me and gives me a button to allow that. Then, the same result, unfortunately.

At least, your dark is brighter than mine. ;)

Tom

---

### Post by jonobr on 2011-11-10
Put 10.21.0.1 in the browser, see if that brings you to the login signup page

---

### Post by 1clue on 2011-11-10
Have you turned off a bunch of scripting languages in your browser?

I didn't see it mentioned anywhere, but you're describing the sort of WIFI that coffee shops use.  There are different approaches for that, but if you turned off scripting on your browser then that might be what's preventing you from seeing the page.

You DO want to allow redirects, or you just won't get out.

That IPV6 address is localnet.  FE80 is sort of like 192.168.

---

### Post by danube on 2011-11-10
Well, it does. On my mobile device. But my laptop don't seem to be impressed at all...

Pinging that address brings also: Destination Net Prohibited.

wtf???

---

### Post by danube on 2011-11-10
1clue, thank you for the info. I've checked this, JavaScript is enabled (if you meant that) and the redirection is allowed again, after I tried to invert this setting.

I don't really know, but can it be a browser problem at all? I mean, I cannot even ping that stupid access point! I really go crazy with this crap... Zero points on hrs... lol

---

### Post by 1clue on 2011-11-10
Does your system hook up to other wireless access points properly?  Meaning not yours but some restaurant or library?

---

### Post by danube on 2011-11-10
Yes it does. During the day I'm working with the same machine in the wifi network of our customer. There, the access point is open but also access is secured with credentials. As here in the hotel.

---

### Post by jonobr on 2011-11-10
> I cannot even ping that stupid access point!

Hey there

A lot of APs restrict things like ping as a security measure,
just FYI......

---

### Post by 1clue on 2011-11-10
It's also possible that your box isn't what's messed up.  Maybe you got a bogus configuration on the router.

---

