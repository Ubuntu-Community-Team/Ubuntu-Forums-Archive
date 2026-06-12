---
title: "network configuration error"
date: 2009-03-22
forum: Networking &amp; Wireless
---

### Post by AionVII on 2009-03-22
Hi all, I have a bit of a problem here.
I can't edit anything in my network configuration window; everytime I try to change something and click OK an error comes up and nothing changes. The error is: 
"Updating connection failed: nm-ifupdown.connection.c.82-connection update not supported (read only).."

What is that? and above all: how can I fix it?

thank you in advance for your help.
Aion

---

### Post by AionVII on 2009-03-22
bump

---

### Post by abyssius on 2009-03-22
> **AionVII said:**
> Hi all, I have a bit of a problem here.
I can't edit anything in my network configuration window; everytime I try to change something and click OK an error comes up and nothing changes. The error is: 
"Updating connection failed: nm-ifupdown.connection.c.82-connection update not supported (read only).."

What is that? and above all: how can I fix it?

thank you in advance for your help.
Aion

I'd start here...

[https://help.ubuntu.com/community/NetworkManager0.7]("https://help.ubuntu.com/community/NetworkManager0.7")

---

### Post by AionVII on 2009-03-23
Ok abyssius thank you very much for the link. 
Unfortunately it didn't solve the problem: I now know that I couldn't modify an auto connection but create a new one (which I did) and putting in all the info the the digicom support gave me. By the way, all I'm trying to do is installing a digicom router (michelangelo wave) which had a beautiful "Linux compatible" icon on the box and is giving me only headaches. 
The strangest thing is that the netmask should be 255.255.255.0 and when I reopen network configuration that value has changed in 24! 
If it can help I post my ifconfig values:

lilith@lilith-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:85:72:7b:f5  
          inet6 addr: fe80::221:85ff:fe72:7bf5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1273 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1174 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1274299 (1.2 MB)  TX bytes:244854 (244.8 KB)
          Interrupt:251 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:490 errors:0 dropped:0 overruns:0 frame:0
          TX packets:490 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30764 (30.7 KB)  TX bytes:30764 (30.7 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:79.20.5.58  P-t-P:192.168.100.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:1236 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1137 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:1244822 (1.2 MB)  TX bytes:212756 (212.7 KB)

when I ping the IP 192.168.1.254 it says "network unreachable" and I have to go back to my old router.

Any ideas?
Thank you in advance

---

### Post by Iowan on 2009-03-23
> **AionVII said:**
> 
The strangest thing is that the netmask should be 255.255.255.0 and when I reopen network configuration that value has changed in 24! 
If it can help I post my ifconfig values:Same thing - /24 is simply CIDR notation.

Do you have dial-up connection active? (I'm not used to seeing ppp0 settings).

---

### Post by AionVII on 2009-03-26
Hi, the only thing I did was "sudo pppoeconf" for my first DSL router and it worked fine...now I want to change router and nothing is working.
Don't understand how could I have screwed up so much.
thanks for all your help.
Aion

---

