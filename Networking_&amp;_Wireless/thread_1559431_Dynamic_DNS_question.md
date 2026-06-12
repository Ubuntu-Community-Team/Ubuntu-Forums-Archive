---
title: "Dynamic DNS question"
date: 2010-08-23
forum: Networking &amp; Wireless
---

### Post by Zbor on 2010-08-23
First I'd like to say I hope this thread is in the right section.

I'm new to the Linux/Ubuntu community so please pardon any beginner ignorance.

I've just installed Ubuntu 10.04 on my system and I love it! I want to play with linux more while I'm at work. The reason for this post is I'm trying to get Dynamic DNS installed on my computer and as you can imagine I'm not having any luck.

I went to the website, created my account, but every time I try to access my url it takes me straight to my DSL modem. I see two different options in my modem that I'm not sure which to configure. IP Passthrough or NAT. I can't enable my IP Passthrough because I have NAT configured. I don't have any issue disabling my NAT configuration but I'm not really sure if I should be using IPP or NAT for port forwarding.

My DSL modem (motorola netopia 2210) is connected to my linksys wireless router and my computer connects to the router using wireless.

I'm curious if anyone else has experience something similar. I did a forum search and didn't find this exact issue. A friend of mine said I need to get a Static IP from ATT but wouldn't DynDNS be a solution for that?

Thanks in advance for your help!

---

### Post by Zbor on 2010-08-23
I forgot to mention my router has the option for DDNS which I have setup. Its able to access the address but I feel its still pointing to my modem.

---

### Post by pricetech on 2010-08-23
You'll need to set up port forwarding in both your DSL modem and your Router.  After that, DDNS should work for you.

---

### Post by Zbor on 2010-08-23
Ubuntu uses port 5900 for remote control access correct?

---

### Post by Charlietje on 2010-08-23
Use dyndns using ddclient (sudo apt-get install ddclient)
If you wanna access your ubuntu use ssh.
It's secure shell, meaning, it makes an encrypted connection using port 22.
install ssh by sudo apt-get install openssh-server.


regards

---

### Post by Zbor on 2010-08-23
Wouldn't the DDNS configuration within my router be the same at ddclient?

---

### Post by Mykle87 on 2010-08-23
> **Zbor said:**
> Wouldn't the DDNS configuration within my router be the same at ddclient?

Yes it is the same. I think it is much easier to setup on the router. 

> **Zbor said:**
> Ubuntu uses port 5900 for remote control access correct?

Yes that is correct. You just have to make sure port forwarding is setup to your linux computer. You probably want to give your linux machine a static IP address on your network if you haven't already.

---

### Post by pricetech on 2010-08-23
> **Zbor said:**
> Ubuntu uses port 5900 for remote control access correct?

That's VNC, inherently insecure, don't use it.

Use SSH instead.

---

### Post by Zbor on 2010-08-23
Perfect. Looks like I have some things to try when I get home. I will post again around 8pm CST whether it worked or not. Thanks everyone!

---

### Post by Zbor on 2010-08-23
Still isn't working... I'll have to check some more things tomorrow. I made sure I turned on my firewall and I have enabled port 22. I also setup NAT to enable port 22.

---

### Post by Mykle87 on 2010-08-23
Networking is always a complicated situation. Maybe [http://portforward.com/]("http://portforward.com/") can help you. Start by selecting your router and then what service you want to portfoward which in your case is SSH. Good luck.

---

### Post by Charlietje on 2010-08-24
Did you install ssh?

---

### Post by Mykle87 on 2010-08-24
In Ubuntu Software Center search ssh and install.

OR

In terminal run
```
sudo apt-get install ssh
```

---

### Post by pricetech on 2010-08-24
In Synaptic openssh-server.

But I think the OP is past that point.

---

### Post by Zbor on 2010-08-26
Yes I did get SSH installed. I also configured the firewall to allow traffic on port 22

---

### Post by pricetech on 2010-08-26
Can you test it locally, on the same subnet, to make sure it's working internally ??

---

### Post by Zbor on 2010-08-28
am I supposed to type my address in the web browser or in a terminal services client?

---

### Post by Charlietje on 2010-08-29
Did you test it localy?
from the command line:

```
ssh localhost
```

It will ask for your password.

---

### Post by Zbor on 2010-08-29
Ok, does this look right?

micah@ubuntu:~$ ssh localhost
The authenticity of host 'localhost (::1)' can't be established.
RSA key fingerprint is 45:c1:20:a4:bf:b9:b6:1a:fb:cd:3b:3c:c9:69:39:bf.
Are you sure you want to continue connecting (yes/no)? y
Please type 'yes' or 'no': yes
Warning: Permanently added 'localhost' (RSA) to the list of known hosts.

micah@localhost's password: 

Linux ubuntu 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:12:52 UTC 2010 i686 GNU/Linux
Ubuntu 10.04.1 LTS

Welcome to Ubuntu!
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

17 packages can be updated.
0 updates are security updates.


The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

---

### Post by Zbor on 2010-08-30
I've also enabled port 22, 80, and 5900 on my modem(via NAT), router(via port forward utility), and firewall (ufw).

When I go to the DynDNS port checker 22 and 5900 are open but 80 is refused. the site says it could be refused by the ISP...

Should I be connecting to my site via firefox or MSTSC (when I'm at work)?

Would I help If I posted my ddclient.conf settings and my ssh.conf settings?

---

### Post by capn.hector on 2010-08-30
you will connect via the ssh client.  your ssh login is correct.  from work you will use ssh *ddns.host.name*:*user*  or a space instead of a colon depending on the client.  if its windows use putty ssh and put the : version in the host or ip box

---

### Post by Zbor on 2010-09-01
I'm in with Putty. Its not the GUI I was hoping for but its better than nothing!
Thanks everyone for your help!!!

---

### Post by e.m.fields on 2010-10-07
> **Zbor said:**
> I've also enabled port 22, 80, and 5900 on my modem(via NAT), router(via port forward utility), and firewall (ufw).

When I go to the DynDNS port checker 22 and 5900 are open but 80 is refused. the site says it could be refused by the ISP...

Should I be connecting to my site via firefox or MSTSC (when I'm at work)?

Would I help If I posted my ddclient.conf settings and my ssh.conf settings?

THANK YOU! THANK YOU THANK YOU THANK YOU. 
Good grief. This finally answered it. 

So I now have dyndns.org URL forwarding to my home server behind an AT&T DSL router, which they wanted me to pay an extra $15 a month on top of my already-$39 just to have a static IP address. And now, I have, for free, my own linux server box sitting at home, thanks to your tip-off about the forwarding ports 22,80, and 59000.

:KS Thank you thank you thank you. :KS

---

