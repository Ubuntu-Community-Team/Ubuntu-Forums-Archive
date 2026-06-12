---
title: "BSNL Wireless settings"
date: 2010-07-22
forum: Networking &amp; Wireless
---

### Post by sandyclone on 2010-07-22
I have a bsnl broadband connection to my system.my modem supports wireless connectivity.I want to use this internet connection in my laptop using wifi.Iam getting connected notification in my laptop but Iam unable to use internet.Please help me regarding this.my system os is xp and laptop is ubuntu.:D

---

### Post by dineshs on 2010-07-22
What is the model name of your modem?
How do you connect to iternet in Windows ?Do you have a dialler ?
Please post the output of
```
ping 192.168.1.1 -c3
```via wireless?(disconnect ethernet cable while trying this)

---

### Post by sandyclone on 2010-07-22
my modem is ZTE ZXDSL 531B.This one is connected to windows xp.

---

### Post by dineshs on 2010-07-22
Is the internet lamp flashing in the modem?
Can you ```
ping 192.168.1.1 -c3
```from ubuntu laptop (pl post output)

---

### Post by raghavdeepak on 2010-08-25
Hi Dinesh,

I am also facing similar kind of issue. I can connect to Internet using cable, but not wifi. I am also using BSNL modem. I thing to be noted is that I can connect to internet but i cannot connect to modem using 192.168.1.1. When i did a ifconfig, it shows my ip as 117.*.*.*

Any help will be appreciated.

---

### Post by dineshs on 2010-08-25
You are using bridge mode hence the IP 117.XXXXXX
What does
```
lshw -C network
```and```
iwconfig
``` say?pl post results

---

### Post by raghavdeepak on 2010-08-25
Thanks for the response, I will post reply, once i reach home....(thats my home computer, with the issue)

---

### Post by raghavdeepak on 2010-08-25
jiya@jiya-laptop:~$ [COLOR=Red][B]lshw -C network
[/B][/COLOR]WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 01
       serial: 00:1c:26:3e:a2:ab
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:18 memory:c0200000-c0203fff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:8e:21:b4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 multicast=yes
       resources: irq:21 memory:c0300000-c0301fff

jiya@jiya-laptop:~$ [COLOR=Red]**iwconfig**[/COLOR]
lo        no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0      no wireless extensions.

ppp0      no wireless extensions.

for your info, i am using internet on the same laptop using cable...

---

### Post by dineshs on 2010-08-25
```
Access Point: Not-Associated 
```is not a good sign
Do you have windows on the same machine?If yes,are you able to use wifi in windows?Do you use a PPPoE dialler,I mean Is the modem configured in BRIDGE mode?
What is the model name of your modem?

---

### Post by raghavdeepak on 2010-08-25
Earlier , I was using windows 7, did  a clean install.................in windows wifi worked grt....no issues at all................model is nokia siemens SL2_141..

In windows yes in bridge mode,....... currently i have saved user name and password in connection manager............so i just connect cable and use internet

---

### Post by dineshs on 2010-08-25
I suggest you configure your modem in PPPoE mode.First connect your modem via ethernet port .The following link
[http://ernakulam.sancharnet.in/ernakulam/bbservice.html](http://ernakulam.sancharnet.in/ernakulam/bbservice.html) 
will help you configure modem in PPPoE mode(Click CPE config and select SL2141)

Once configured the data/internet lamp in the modem will start flickering
Now remove your cable and run
```
sudo dhclient
```
Any progress?

---

### Post by raghavdeepak on 2010-08-25
see the problem is i cant even connect to my modem................i cant get 192.168.1.1........

---

### Post by raghavdeepak on 2010-08-25
i got my modem ip and i have tried pinging it and it pings...................but when i type in web browser, it says it is taking too long to respond and page cannot be displayed..

---

### Post by dineshs on 2010-08-25
Can you post the results of(when cable is connected)
```
ifconfig -a
```and```
ping 192.168.1.1 -c3
```

---

### Post by raghavdeepak on 2010-08-25
ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1c:23:8e:21:b4  
          inet6 addr: fe80::21c:23ff:fe8e:21b4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18204 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16228 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16977469 (16.9 MB)  TX bytes:2804076 (2.8 MB)
          Interrupt:21 

eth1      Link encap:Ethernet  HWaddr 00:1c:26:3e:a2:ab  
          inet6 addr: fe80::21c:26ff:fe3e:a2ab/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:35
          TX packets:0 errors:12 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:680 (680.0 B)  TX bytes:680 (680.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:117.199.208.82  P-t-P:117.199.208.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:17967 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15987 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:16488711 (16.4 MB)  TX bytes:2372881 (2.3 MB)

jiya@jiya-laptop:~$ ping 192.168.1.1 -c3
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2014ms


when i tried with my modem ip.........

jiya@jiya-laptop:~$ ping 117.199.208.1 -c3
PING 117.199.208.1 (117.199.208.1) 56(84) bytes of data.
64 bytes from 117.199.208.1: icmp_seq=1 ttl=255 time=9.58 ms
64 bytes from 117.199.208.1: icmp_seq=2 ttl=255 time=8.55 ms
64 bytes from 117.199.208.1: icmp_seq=3 ttl=255 time=8.78 ms

--- 117.199.208.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 8.551/8.975/9.588/0.450 ms

---

### Post by dineshs on 2010-08-25
> when i tried with my modem ip.........
jiya@jiya-laptop:~$ ping 117.199.208.1 -c3
Your modem IP is 192.168.1.1 not 117.199.208.1.Pl follow these steps
First try the site I referred and download the configuration for your modem
Disconnect DSL connection via Network manager then try this command
```
sudo dhclient eth0
```
Now open firefox and proceed with the configuration

---

### Post by raghavdeepak on 2010-08-25
apologies for my ignorance!!!!!!   It worked!!.....I am able to connect wirelessly now!!! Just wanted to say Thanks to you, I am a newbie to obuntu and the kind of help you have given me is very  appreciable................I dont thnk microsoft can even give a help and that too free of cost!! Thats what you call is bonding..

Thanks and May god bless u Dinesh!!!

---

### Post by dineshs on 2010-08-25
Very happy to hear your problem is solved.Please post the result of ```
iwconfig
```
Thank you

---

### Post by raghavdeepak on 2010-08-25
jiya@jiya-laptop:~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:4  Signal level:196  Noise level:199
          Rx invalid nwid:0  invalid crypt:1  invalid misc:0

eth0      no wireless extensions.

---

### Post by dineshs on 2010-08-25
I think You are getting connection via wired.Remove the cable to confirm

---

### Post by raghavdeepak on 2010-08-25
It might sound strange, but it was through wifi.........no cables at all....

---

