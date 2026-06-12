---
title: "Internet sharing between users on one computer"
date: 2009-08-23
forum: Networking &amp; Wireless
---

### Post by RabbitWho on 2009-08-23
So at the moment to connect to the internet I need to type in sudo wvdial in the terminal and of course i don't have sudo privileges on my other user.

GerogeVita told me to use these codes:
```

sudo adduser USERNAME dip
``````

sudo adduser USERNAME dialout
```And i did but the new problem is it says i don't have permission while it attempts to "handshake" 


Rabbit@penguincounter:~$ wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.                    
--> Sending: ATZ                           
ATZ                                        
OK                                         
--> Sending: AT&F E1 V1 X1 &D2 &C1 S0=0    
AT&F E1 V1 X1 &D2 &C1 S0=0                 
OK                                         
--> Sending: AT+CGDCONT=1,"IP","3ireland.ie"
AT+CGDCONT=1,"IP","3ireland.ie"             
OK                                          
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT 3600000
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sun Aug 23 15:10:31 2009
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 6472
--> Using interface ppp0
--> pppd: &#65533;&#65533;&#65533;[08]&#65533;&#65533;&#65533;[08]
--> pppd: &#65533;&#65533;[08]&#65533;&#65533;&#65533;[08]
--> pppd: &#65533;&#65533;&#65533;[08]&#65533;&#65533;&#65533;[08]
--> pppd: &#65533;&#65533;&#65533;[08]&#65533;&#65533;&#65533;[08]
--> pppd: &#65533;&#65533;[08]&#65533;&#65533;[08]
--> pppd: &#65533;&#65533;[08]&#65533;&#65533;[08]
--> local  IP address 10.206.33.60
--> pppd: &#65533;&#65533;[08]&#65533;&#65533;[08]
--> remote IP address 10.64.64.64
--> pppd: &#65533;&#65533;[08]&#65533;&#65533;[08]
--> primary   DNS address 172.31.140.69
--> pppd: &#65533;&#65533;[08]&#65533;&#65533;[08]
--> secondary DNS address 172.30.140.69
--> pppd: &#65533;&#65533;[08]&#65533;&#65533;[08]
^CCaught signal 2:  Attempting to exit gracefully...
--> Terminating on signal 15
--> pppd: &#65533;&#65533;[08]&#65533;&#65533;[08]
--> Connect time 1.4 minutes.
--> pppd: &#65533;&#65533;[08]&#65533;&#65533;[08]
--> pppd: &#65533;&#65533;[08]&#65533;&#65533;[08]
--> pppd: &#65533;&#65533;[08]&#65533;&#65533;[08]

---

### Post by dmizer on 2009-08-23
But you had a connection and an IP address.

I run wvdial as user and get those two errors all the time, but the internet works just fine anyway.

---

### Post by eldragon on 2009-08-23
run 
```

sudo visudo

```
and add at the end of the file

```

%users   ALL=NOPASSWD:wvdial

```

that should allow your other accounts to tun wvdial with sudo, and not to enter a password.

im not sure if what editor will pop up, but if its vi

once in the file, type 'i' to enter in insert mode.
navigate to the end of the file, add the line
press 'esc' and type ':wq' to save.

---

### Post by RabbitWho on 2009-08-23
> **eldragon said:**
> run 
```

sudo visudo

```and add at the end of the file

```

%users   ALL=NOPASSWD:wvdial

```that should allow your other accounts to tun wvdial with sudo, and not to enter a password.

im not sure if what editor will pop up, but if its vi

once in the file, type 'i' to enter in insert mode.
navigate to the end of the file, add the line
press 'esc' and type ':wq' to save.

it just says visduo at the top and it's still in the konsole 
when I press escape nothing happens?
Not sure how to save because of this. 

> **dmizer said:**
> But you had a connection and an IP address.

I run wvdial as user and get those two errors all the time, but the internet works just fine anyway.
I'll try it again now so, i have a dodgy dongel. Ha ha. Don't say that to a stranger on a bus. Anyway maybe the first time I tried the internet just happened to be in a nasty mood. (I did remember to disconnect from the internet as the other user, don't worry)

Update: Nope, tried it again twice, same message about CHAP and it didn't connect. On this user there's none of that and it connects instantly.

---

### Post by dmizer on 2009-08-23
> **RabbitWho said:**
> Update: Nope, tried it again twice, same message about CHAP and it didn't connect. On this user there's none of that and it connects instantly.

Can you post the output again, as well as the output of ifconfig

Also, go into your "users and groups" settings to make sure your unprivileged user has the right to use the internet.

---

### Post by RabbitWho on 2009-08-23
> **dmizer said:**
> Can you post the output again, as well as the output of ifconfig

Also, go into your "users and groups" settings to make sure your unprivileged user has the right to use the internet.

I''m not sure how to do that, remember I'm using KDE, so I can get as far as User Management, settings, but then I can't find anything about user rights. 


Here we go: 

Rabbit@penguincounter:~$ wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.                    
--> Sending: ATZ                           
ATZ
OK
--> Sending: AT&F E1 V1 X1 &D2 &C1 S0=0
AT&F E1 V1 X1 &D2 &C1 S0=0
OK
--> Sending: AT+CGDCONT=1,"IP","3ireland.ie"
AT+CGDCONT=1,"IP","3ireland.ie"
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT 3600000
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sun Aug 23 17:34:15 2009
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 21313
--> Using interface ppp0
--> pppd: &#65533;q5[08]&#65533;g5[08]
--> pppd: &#65533;q5[08]&#65533;g5[08]
--> pppd: &#65533;q5[08]&#65533;g5[08]
--> pppd: &#65533;q5[08]&#65533;g5[08]
--> pppd: &#65533;q5[08]&#65533;g5[08]
--> pppd: &#65533;q5[08]&#65533;g5[08]
--> local  IP address 10.206.21.127
--> pppd: &#65533;q5[08]&#65533;g5[08]
--> remote IP address 10.64.64.64
--> pppd: &#65533;q5[08]&#65533;g5[08]
--> primary   DNS address 172.31.140.69
--> pppd: &#65533;q5[08]&#65533;g5[08]
--> secondary DNS address 172.30.140.69
--> pppd: &#65533;q5[08]&#65533;g5[08]





Rabbit@penguincounter:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:25:64:4d:59:17
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18

eth1      Link encap:Ethernet  HWaddr 00:26:5e:54:55:bb
          inet6 addr: fe80::226:5eff:fe54:55bb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:464 errors:0 dropped:0 overruns:0 frame:0
          TX packets:464 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:22632 (22.6 KB)  TX bytes:22632 (22.6 KB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:10.206.21.127  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1440  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:130 (130.0 B)  TX bytes:181 (181.0 B)

---

### Post by dmizer on 2009-08-23
You have an IP address, can you ping something?

Try pinging by both IP address and hostname:
```
ping www.google.com
```
```
ping 66.249.89.99
```

---

### Post by dmizer on 2009-08-23
> **RabbitWho said:**
> I''m not sure how to do that, remember I'm using KDE, so I can get as far as User Management, settings, but then I can't find anything about user rights.

I had to boot my Kubuntu virtual machine to figure it out.

In KDE, it's under > applications > system > user manager.

---

### Post by RabbitWho on 2009-08-23
> **dmizer said:**
> You have an IP address, can you ping something?

Try pinging by both IP address and hostname:
```
ping www.google.com
``````
ping 66.249.89.99
```

So that seems to do something:


Rabbit@penguincounter:~$ ping [www.google.com]("http://www.google.com")
PING [www.l.google.com]("http://www.l.google.com") (209.85.227.103) 56(84) bytes of data.
64 bytes from wy-in-f103.google.com (209.85.227.103): icmp_seq=1 ttl=53 time=129 ms            
(and it went on like that)

And now google opens in firefox.. and i can search for things, but uber-slowly, and then I can't click any links or get into other sites.

---

### Post by RabbitWho on 2009-08-23
> **dmizer said:**
> I had to boot my Kubuntu virtual machine to figure it out.

In KDE, it's under > applications > system > user manager.


Aye i was able to find it allright but then I can't find anything about user rights.

Thanks for going to so much trouble for me!

---

### Post by dmizer on 2009-08-23
No problem.

Try this:

Type about:config in your address entry bar (in firefox)
Type "ipv6" in the filter
Change the value of "network.dns.disableIPv6" to true

Also, you may have more luck with different DNS servers: [https://www.opendns.com/start/device/ubuntu](https://www.opendns.com/start/device/ubuntu)

---

### Post by RabbitWho on 2009-08-23
Wheyhey! You did it! Thank you! :)

Can I just ask one more thing? Is there any tutorial or explanation available anywhere about some of the things we just did? I'd like to understand it better.

---

### Post by dmizer on 2009-08-23
> **RabbitWho said:**
> Wheyhey! You did it! Thank you! :)

Can I just ask one more thing? Is there any tutorial or explanation available anywhere about some of the things we just did? I'd like to understand it better.

It was basic troubleshooting.

1) Despite the fact that you had errors in wvdial, it still completed and showed that it gave you both an IP address and DNS servers which means the connection was successful. (you had to hit <ctrl> c to cancel wvdial)
2) The ifconfig command confirms that you have an IP address. That means you are most certainly connected.
3) You can ping by both IP and hostname but you can't browse. That means that your connection is passing traffic to the internet, so something else is blocking it.
4) That means you have either a problem with IPv6 addressing (a common problem in Ubuntu), a possible firewall problem (unlikely), or you have DNS issues.

Remember, just because you see errors doesn't mean that it failed.

---

### Post by RabbitWho on 2009-08-23
> **dmizer said:**
> It was basic troubleshooting.

1) Despite the fact that you had errors in wvdial, it still completed and showed that it gave you both an IP address and DNS servers which means the connection was successful. (you had to hit <ctrl> c to cancel wvdial)
2) The ifconfig command confirms that you have an IP address. That means you are most certainly connected.
3) You can ping by both IP and hostname but you can't browse. That means that your connection is passing traffic to the internet, so something else is blocking it.
4) That means you have either a problem with IPv6 addressing (a common problem in Ubuntu), a possible firewall problem (unlikely), or you have DNS issues.

Remember, just because you see errors doesn't mean that it failed.

I see! Great! thanks so much for your help and advice :)

---

