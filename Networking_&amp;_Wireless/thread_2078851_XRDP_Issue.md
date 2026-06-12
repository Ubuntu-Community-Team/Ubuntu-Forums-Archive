---
title: "XRDP Issue"
date: 2012-10-31
forum: Networking &amp; Wireless
---

### Post by 1971 on 2012-10-31
Hi

I have clean install of Lubuntu 12.10. No other OS or anything like that just the Lubuntu OS. The first thing I wanted to do was install XRDP so I can log into it in a remote session from a WIndows 8 PC. 

I used Synaptic to install XRDP. Went without a hitch and installed two dependencies. I located the IP address in ifconfig. I try to connect but get this error

[IMG]http://http://hillclimbnsw.org.au/im.jpg[/IMG][IMG]http://hillclimbnsw.org.au/im.jpg[/IMG]

All other networking stuff works fine.

ANy help appreciated

---

### Post by steeldriver on 2012-10-31
Do you have a ~/.xsession (or ~/.Xsession)? if so what are its contents?

I have got it to work from 12.04 to Win7 - but I had to play with things (seems to only work with a 2d session)

Don't have access to Win8 unfortunately

---

### Post by 1971 on 2012-10-31
> **steeldriver said:**
> Do you have a ~/.xsession (or ~/.Xsession)? if so what are its contents?

I have got it to work from 12.04 to Win7 - but I had to play with things (seems to only work with a 2d session)

Don't have access to Win8 unfortunately

Do you have a ~/.xsession (or ~/.Xsession)? if so what are its contents?

I don't know what that is?

ifconfig output

p@p-G31M-S2L:~$ sudo ifconfig
[sudo] password for p: 
eth0      Link encap:Ethernet  HWaddr 00:1f:d0:1e:ae:3c  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:d0ff:fe1e:ae3c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:142 errors:0 dropped:0 overruns:0 frame:0
          TX packets:140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13639 (13.6 KB)  TX bytes:12662 (12.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:288 errors:0 dropped:0 overruns:0 frame:0
          TX packets:288 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:23052 (23.0 KB)  TX bytes:23052 (23.0 KB)

I also tried using RDP session from my Win 7 Laptop to connect to the lubuntu box and got the same problem.

When I try to connect now I get the following added to what is in the image on the original post

tcp connected
security level is 2 (1 = none, 2 = standard)
password OK
sending share flag
receiving server init
error - problem connecting


CHeers

---

### Post by Slim Odds on 2012-10-31
> **1971 said:**
> Hi

I have clean install of Lubuntu 12.10. No other OS or anything like that just the Lubuntu OS. The first thing I wanted to do was install XRDP so I can log into it in a remote session from a WIndows 8 PC. 

I used Synaptic to install XRDP. Went without a hitch and installed two dependencies. I located the IP address in ifconfig. I try to connect but get this error

[IMG]http://http://hillclimbnsw.org.au/im.jpg[/IMG][IMG]http://hillclimbnsw.org.au/im.jpg[/IMG]

All other networking stuff works fine.

ANy help appreciated
What IP address are you talking about?
127.0.0.1 is localhost, which would be inappropriate for this connection.

It looks like you  want 192.168.0.5

---

### Post by steeldriver on 2012-10-31
^^^ we looked at that in a previous thread - it seems like the xrdp sesman reports the localhost IP even though the correct LAN IP is given (I tried it and I get the same thing) 

1971 can you please try the following terminal commands:

```
sudo ufw status
``````
ls ~/.{x,X}session
```

---

### Post by 1971 on 2012-10-31
> **Slim Odds said:**
> What IP address are you talking about?
127.0.0.1 is localhost, which would be inappropriate for this connection.

It looks like you  want 192.168.0.5
  No I have always being trying to connect to 192.168.0.5

Cheers

---

### Post by 1971 on 2012-10-31
> **steeldriver said:**
> ^^^ we looked at that in a previous thread - it seems like the xrdp sesman reports the localhost IP even though the correct LAN IP is given (I tried it and I get the same thing) 

1971 can you please try the following terminal commands:

```
sudo ufw status
``````
ls ~/.{x,X}session
```

p@p-G31M-S2L:~$ sudo ufw status
[sudo] password for p: 
Status: inactive

p@p-G31M-S2L:~$ sudo ls ~/.{x,X}session
ls: cannot access /home/p/.xsession: No such file or directory
ls: cannot access /home/p/.Xsession: No such file or directory

It is using vnc4server as installed with XRDP. 
Added my username to XRDP group --> No change

Added another User --> No change

Enabled vnc4server and set password --> No change

Tried all the different colour depth settings in the Windows RDP Client --> No Change

---

### Post by ysandhu on 2012-12-06
I have same problem.

Trying hard to make it work. Any update ??

---

### Post by joelseeley on 2013-03-06
this fix is for Lubuntu 12.10 xrdp
I was able to fix mine by doing the following from home directory:

the file i edited was located /home/jon/.xsession

i added:

startlubuntu

after this it worked!! and that was after several hours of trying to figure it out. so do the following at the prompt to fix:

"gedit .xsession"
add the line "startlubuntu"
save and exit
restart and it works.

---

