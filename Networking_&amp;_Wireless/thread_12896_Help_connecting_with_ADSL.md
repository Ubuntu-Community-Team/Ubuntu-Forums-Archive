---
title: "Help connecting with ADSL"
date: 2005-01-27
forum: Networking &amp; Wireless
---

### Post by Murador on 2005-01-27
Hi All!
I've successfully installed Ubuntu on my PC, but I have some problems getting my ADSL connection to work properly

I've got an adsl modem by Siemens connected to an ethernet card (based on realtek chip, I think 8139).
I've ran pppoeconf, setting up my account info properly and asking for the connection to be launched at boot time

the modem seems to connect properly at boot time, but when I try to ping or to surf the web or anything else, I just don't get any response.

the only way I can get my connection to work is to do:
[list]
[*]poff
[*]ifconfig eth0 down
[*]pon dsl-provider
[/list] 
each time that I want to get connected

How can I solve that and get the conection at boot-time work properly?
Is it a DHCP problem of some kind?

thanks in advance ;)

---

### Post by az on 2005-01-27
Look in /var/log/messages for what is happenening to your connection at boot (assuming you are connecting).

I found that pppoeconf works great the first time, but if you play around with the /etc/ppp/peers/dsl-provider file, pppeoconf gets confused.  If you remove that file and start over with pppoeconf, things work again.

---

### Post by Murador on 2005-01-27
[QUOTE=azz]Look in /var/log/messages for what is happenening to your connection at boot (assuming you are connecting).

I found that pppoeconf works great the first time, but if you play around with the /etc/ppp/peers/dsl-provider file, pppeoconf gets confused.  If you remove that file and start over with pppoeconf, things work again.[/QUOTE]
 I haven't modified dsl-provider after the first pppoeconf

what makes me think is that I have to close the connection, issue "ifconfig eth0 down" to reset eth0 and then lauch the connection...

this is not an ubuntu issue btw, I've experienced this many times with many linux distros...

---

### Post by az on 2005-01-27
Yes, what is in /etc/network/interfaces?

Do ifconfig, after you boot, but before you connect, look at the /var/log/messages and you should have an idea of what is going on.

---

### Post by m4ng0 on 2005-01-27
It is normal if you have configured your eth0 interface with an IP address before running pon.
From the pppoe man page:
> The interface should be "up" before you start pppoe, but should  _not_  be configured  to have an IP address.

---

### Post by az on 2005-01-27
My eth1 has address 192.168.1.1 and I still connect with pppoe...

---

### Post by m4ng0 on 2005-01-27
[QUOTE=azz]My eth1 has address 192.168.1.1 and I still connect with pppoe...[/QUOTE]
Hello azz,
  just because I'm curious, I try to expose my case: I have only one ethernet card (eth0) and my
adsl modem is connected to it. I start up my system and
"ifconfig eth0"
gives me no "inet addr" (I have not configured one, so it's OK).
If I call
"pon dsl-provider"
everything is fine, I can surf with no problem.
Then I go to Computer -> Network settings -> Add -> Ethernet -> Manual in order to assign an IP
address to my eth0 interface (say 192.168.0.2) and activate it.
Now "ifconfig eth0" shows:
inet addr:192.168.0.2
and that's OK. At this moment, if I try to do
"pon dsl-provider"
I get connected but I can't resolve (that's why I think this could be Murator's problem).
So I give "poff dsl-provider" and bring down eth0 interface... and now
"pon dsl-provider" works fine again!
"ifconfig eth0" still says "inet addr:192.168.0.2", but now the connection is
working properly. So I think this can be a default route problem.
Is this "normal" and reproducible in your case, or have I misconfigured something?
Thanks.

---

### Post by Murador on 2005-01-28
[QUOTE=m4ng0]Hello azz,
  just because I'm curious, I try to expose my case: I have only one ethernet card (eth0) and my
adsl modem is connected to it. I start up my system and
"ifconfig eth0"
gives me no "inet addr" (I have not configured one, so it's OK).
If I call
"pon dsl-provider"
everything is fine, I can surf with no problem.
Then I go to Computer -> Network settings -> Add -> Ethernet -> Manual in order to assign an IP
address to my eth0 interface (say 192.168.0.2) and activate it.
Now "ifconfig eth0" shows:
inet addr:192.168.0.2
and that's OK. At this moment, if I try to do
"pon dsl-provider"
I get connected but I can't resolve (that's why I think this could be Murator's problem).
So I give "poff dsl-provider" and bring down eth0 interface... and now
"pon dsl-provider" works fine again!
"ifconfig eth0" still says "inet addr:192.168.0.2", but now the connection is
working properly. So I think this can be a default route problem.
Is this "normal" and reproducible in your case, or have I misconfigured something?
Thanks.[/QUOTE]


that's exactly my problem!
so, how can I remove the inet addr? what config file should I edit?

---

### Post by Jad on 2005-01-28
If your Siemens modem have a Web cp, you will just need to configure it to Always on
I use [http://10.0.0.138/index.htm](http://10.0.0.138/index.htm) to configure my modem.

---

### Post by neville_lobo on 2005-02-05
I was facing the same problem as Murador. There is a fix but its not perfect. 

Steps:
1. Disable eth0 from activating at startup.
2. Activate ppp0 at startup via pppoeconf.
3. Profit!

This works because 'pon' activates eth0. The bad part is I cant log on to the windows share on my brothers PC. To do that I have to activate eth0 manually via its properties window. The problem is that activating eth0 manually causes problems with pppoe and you cant resolve any more. You will have to turn off ppp0 via 'poff', turn off eth0 via 'ifconfig eth0 down' and turn on ppp0 again via 'pon'.  But if all you need is to connect to the net at boot and not the local network, it seems like a reasonable fix. It is what I need. Hope this helps.

Neville

---

