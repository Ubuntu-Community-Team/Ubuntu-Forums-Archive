---
title: "Eciadsl and pppoe"
date: 2005-03-11
forum: Networking &amp; Wireless
---

### Post by occy8 on 2005-03-11
I just installed Hoary on my computer and everything went smooth.

Now I need to install my usb modem and pppoe

I got the following files

eciadsl_0.10-1_i386.deb
pppoe_3.5-4ubuntu1_i386.deb

When I do aptitude install I get this message

Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package

I must say don't know much about linux, please help

---

### Post by Swab on 2005-03-11
When do you receive this error message?  And where did you get the deb files from?

---

### Post by occy8 on 2005-03-11
Those files came from the Ubuntu universe.
 And the messages are coming straight after typing aptitude install and the file name

---

### Post by Swab on 2005-03-11
try:  dpkg -i filename

---

### Post by occy8 on 2005-03-11
O.k. that worked. great!!
I will try to get it running now. just got the tutorial from eciadsl. 
Didn't find much on pppoe though, any idea where to find info or if its easy enough tellme here.

---

### Post by occy8 on 2005-03-11
no just tried to follow that intruction and I can't figure it out its written for mandrake  and seems everything is different 
any ideas ??

---

### Post by Swab on 2005-03-11
I don't really know much about that, I use a router so never had to configure pppoe... but if you type pppoeconf it opens up a configuration program.  You might also want to search to forums for other posts.

---

### Post by occy8 on 2005-03-11
Hi thanks for trying I got a little bit further. The files at the ubuntu universe, it seems are not working. I got a file from eciadsl    eciadsl-usermode-nortek-0.10_alpha.ebuild

it installed o.k. and I was able to configure it.
eciadsl-config-tk
But still it doesn't find the modem. Instead the USB flash doesn't work now.
I will see if the guys at eciadsl have an idea

---

### Post by occy8 on 2005-03-12
Just an update.
it works now, almost
don't know why it didn't yesterday. Booted this morning and it worked fine but didn't syncronise. The guys a eciadsl told me to download other synch_bin files and I quickly found one that worked (number 06).

So now I'm here last problem is the pppoe configuration 

so if someone could help me wowould be great.

[EciAdsl 1/5] Setting up USB support...

Preliminary USB device filesystem is OK

[EciAdsl 2/5] Uploading firmware...

Process skipped .. no more needed
firmware loaded successfully

[EciAdsl 3/5] Synchronization...

OK eciadsl-synch: success 
Synchronization successful

[EciAdsl 4/5] Connecting to provider...

Connection successful

[EciAdsl 5/5] Setting up route table...

Waiting for tap0...
ERROR: couldn't set your static IP or your external gateway
If you don't use PPPoE, please check your configuration

---

### Post by occy8 on 2005-03-13
another update and a new question

I am connected !!!!!!!!!!!
I found a great webpage where it explains how to read all the settings in Windows and Mac      [http://kb.indiana.edu/data/ajfx.help](http://kb.indiana.edu/data/ajfx.help)

BUT

when I type [www.google.com](www.google.com) or something else the browser looks up the address but nothing happens just the firefox dots in the right corner are rotating.

Do I have to do something else?? Firewall?? I'm having a standard Hoary installation

---

### Post by occy8 on 2005-03-14
I'm just wondering...
this is what I get doing ifconfig
Iahve no idea what it means but I think at least some communication is going on 
but if I ping someome I get can't reach ....as reply
can somone see where the problem could be 


root@ubuntu:~ # ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0A:48:05:22:F0
          inet6 addr: fe80::20a:48ff:fe05:22f0/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:450 (450.0 b)
          Interrupt:22 Base address:0x8000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2769 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2769 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:735285 (718.0 KiB)  TX bytes:735285 (718.0 KiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:220.240.35.61  P-t-P:203.194.30.234  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:54 (54.0 b)  TX bytes:54 (54.0 b)

tap0      Link encap:Ethernet  HWaddr 00:FF:0C:EC:F5:66
          inet addr:220.240.35.61  Bcast:220.240.35.255  Mask:255.255.255.0
          inet6 addr: fe80::2ff:cff:feec:f566/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25 errors:0 dropped:0 overruns:0 frame:0
          TX packets:155 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1519 (1.4 KiB)  TX bytes:6556 (6.4 KiB)

---

### Post by occy8 on 2005-03-15
Hello again...
now the problem seems to be the MTU setting being too high (1500)
how do I change the default setting?
I tried ifconfig tap0 mtu 1460 but after boot its 1500 again

and for mru as well?



> Mar 15 20:52:04 localhost pppd[7994]: Plugin rp-pppoe.so loaded.
> Mar 15 20:52:04 localhost pppd[7994]: RP-PPPoE plugin version 3.3 compiled against pppd 2.4.2
> Mar 15 20:52:04 localhost pppd[7996]: pppd 2.4.2 started by root, uid 0
> Mar 15 20:52:05 localhost pppd[7996]: PPP session is 3040
> Mar 15 20:52:05 localhost pppd[7996]: Using interface ppp0
> Mar 15 20:52:05 localhost pppd[7996]: Connect: ppp0 <--> tap0
> Mar 15 20:52:05 localhost pppd[7996]: Couldn't increase MTU to 1500
> Mar 15 20:52:05 localhost pppd[7996]: Couldn't increase MRU to 1500

---

### Post by occy8 on 2005-03-16
I just found a comment somewhere saying the default mtu / mru is 1500 in Ubuntu

Unfortunately no comment on how to change it 

So how or where can I change that

---

### Post by occy8 on 2005-03-16
Now I'm writing this from Ubuntu,

Yeehaa it works, what a relief

For anybody who is interested

I changed the mtu setting in the eciadsl-start script
I received the tip from the guys at eciadsl

but then it still didn't work immediately 
I ran the eciadsl-config-tk again removed the static setting (it seemed I need it earlier ) 
and I ran pppoeconf again as well
I don't think I did anything else but now I'm happy

---

