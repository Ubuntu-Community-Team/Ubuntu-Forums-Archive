---
title: "Unable to ping own domain"
date: 2009-09-03
forum: Networking &amp; Wireless
---

### Post by w1z8it on 2009-09-03
I have been trying to setup a mail server for my forum that I'm hosting on my Ubuntu machine, however I am just unable to establish a connection.

my domain is chaotic-realms.com, I attempted to setup postfix with this domain, and tested with the following command:

```
telnet chaotic-realms.com 25

```Which results in the following:

```
Trying 81.236.166.248...
```And that's as far as it gets. I've also tried to ping my domain (and also my IP address directly without the domain) but basically the same thing happens it does't seem to be getting through for some reason, and my router firewall is completey disabled.

Any ideas?

---

### Post by stefangr1 on 2009-09-03
I think this is normal. If you want to test, you have to do it from a different domain. Normally, a reverse dns server is used to use a domain name from within the local network.

---

### Post by Barrucadu on 2009-09-03
Usually you can't connect to a local machine using an external IP or domain, most home routers can't do that IIRC.

---

### Post by w1z8it on 2009-09-03
> **stefangr1 said:**
> I think this is normal. If you want to test, you have to do it from a different domain.

I fixed the ping issue, it pings ok now using domain, but it still gets stuck with telnet on my ip so I'm unable to send mail, any ideas?

---

### Post by stefangr1 on 2009-09-03
The problem is that your dns server does not know what to do with requests from the internal network. You have to do some [extra configuration]("http://www.howtoforge.com/two_in_one_dns_bind9_views") to get that working. Without that, you can't telnet or mail or browse to your own domain from inside your internal network.

---

### Post by w1z8it on 2009-09-03
> **stefangr1 said:**
> The problem is that your dns server does not know what to do with requests from the internal network. You have to do some [extra configuration]("http://www.howtoforge.com/two_in_one_dns_bind9_views") to get that working. Without that, you can't telnet or mail or browse to your own domain from inside your internal network.

I attempted the guide in the link you sent and already I have an error on the very first section

[ Error writing /etc/bind/named.conf.local: No such file or directory ]

If the file doesn't even exist it can't have been used to begin with are you sure this is what I need to do just to send mail outbound? Doesn't make alot of sense

---

### Post by stefangr1 on 2009-09-03
I've never used that tutorial myself, just googled a sec for a tutorial and this one looks reasonable. [Here]("http://ubuntuforums.org/showthread.php?t=236093") is another one, from the Ubuntu forums. 

Just to be sure: I assume you have installed bind9 as a first step? Another thing: I'm not sure if an example configuration script is always included.

Are you an advanced user? Configuring your own dns server and mail server etc. is quiete complex when doing it for the first time.

---

### Post by stefangr1 on 2009-09-03
> **w1z8it said:**
> 
If the file doesn't even exist it can't have been used to begin with are you sure this is what I need to do just to send mail outbound? Doesn't make alot of sense

This is not needed to send mail outbound. Your question related to not being able to ping/telnet to your own ip and domain. Maybe you can be a bit more specific about what your goal is and what you have tried, because a mail server is not directly related to telnet.

---

### Post by w1z8it on 2009-09-03
> **stefangr1 said:**
> This is not needed to send mail outbound. Your question related to not being able to ping/telnet to your own ip and domain. Maybe you can be a bit more specific about what your goal is and what you have tried, because a mail server is not directly related to telnet.

 I explained in my initial post I'm trying to setup a mail server and that testing it through telnet didn't work, sorry for the confusion pinging was just to test my connection, telnet should work with postfix without all that stuff you've mentioned, it just doesn't seem to work for me so theres an issue somewhere my end, trying to get help on what it could be, any ideas?

---

### Post by hal10000 on 2009-09-03
did you enable telnet? It's disabled by default on linux systems.

---

### Post by w1z8it on 2009-09-03
> **hal10000 said:**
> did you enable telnet? It's disabled by default on linux systems.

 Hmmm I didn't manually enable it no, how would I do that?

---

### Post by hal10000 on 2009-09-03
First you have to install the package telnetd on your server machine. 
I haven' used telnet for years and i cant remember what to configure, i guess you have to start the telnet server with [COLOR="Red"]sudo /etc/init.d/telnetd start[/COLOR], but there might be other things to be done.
btw. why are you using telnet, which is a great security risk, instead of ssh daemon?

---

### Post by w1z8it on 2009-09-03
> **hal10000 said:**
> First you have to install the package telnetd on your server machine. 
I haven' used telnet for years and i cant remember what to configure, i guess you have to start the telnet server with [COLOR=Red]sudo /etc/init.d/telnetd start[/COLOR], but there might be other things to be done.
btw. why are you using telnet, which is a great security risk, instead of ssh daemon?

 It's just to test if postfix is working, I know absolutely nothing about email servers, I'm experienced in hosting game servers and C# that is all.  I have ssh setup, how would I test postfix with it?

---

### Post by w1z8it on 2009-09-03
I installed telnet and restarted I'm still stuck on:

$ telnet chaotic-realms.com 25
Trying 81.236.166.248...

However if I do:

$ telnet localhost 25
Trying ::1...
Connected to localhost.
Escape character is '^]'.
220 chaotic-realms.com ESMTP Postfix (Ubuntu)

As you can see it works, but I can't send outbound mail, nothing gets received.

---

### Post by hal10000 on 2009-09-03
> I installed telnet and restarted I'm still stuck on:
you don't have to install telnet on the server mashine , but telnetd, the difference is on the last character.

---

### Post by stefangr1 on 2009-09-03
I do understand that you're not using telnet for login on the server, but as a simple way to send mail.

However, it's important to know whether the computer with the server on it and the computer that you use for testing are on the same local network or not. If they are, you can try telnet with the local address of the server in stead of the outside address.

---

### Post by w1z8it on 2009-09-03
> **hal10000 said:**
> you don't have to install telnet on the server mashine , but telnetd, the difference is on the last character.

I don't understand what you're saying.

---

### Post by w1z8it on 2009-09-03
> **stefangr1 said:**
> I do understand that you're not using telnet for login on the server, but as a simple way to send mail.

However, it's important to know whether the computer with the server on it and the computer that you use for testing are on the same local network or not. If they are, you can try telnet with the local address of the server in stead of the outside address.

It's the same computer.

Maybe I'm not being clear... All I want is for my SMF 2.0 forum to send emails to registered users, for that I need to setup postfix which I've done, however it does not send emails out although I get no errors, so I'm trying to test this with telnet (from the server machine) to see if I can get to the root of the problem.

---

### Post by hal10000 on 2009-09-03
Can you see the difference between **telnet** and **telnetd** ?

---

### Post by w1z8it on 2009-09-03
> **hal10000 said:**
> Can you see the difference between **telnet** and **telnetd** ?

Yeah but what does that have to do with my issue?

---

### Post by hal10000 on 2009-09-03
> Yeah but what does that have to do with my issue?
You have to install the package **telnetd** instead of **telnet**. **telnetd** is the telnet daemon (the server program), **telnet** is the client to access the server.

---

### Post by w1z8it on 2009-09-03
> **hal10000 said:**
> You have to install the package **telnetd** instead of **telnet**

Done, still the same problem.

---

### Post by hal10000 on 2009-09-03
> Done, still the same problem.
ok. And then, did you start the daemon? I guess the command is [COLOR="Red"]sudo /etc/init.d/telnetd start[/COLOR]
I don't know if there is some configuration to be done to make telnetd to run together with your mailserver

---

### Post by w1z8it on 2009-09-03
> **hal10000 said:**
> ok. And then, did you start the daemon? I guess the command is [COLOR=Red]sudo /etc/init.d/telnetd start[/COLOR]

sudo: /etc/init.d/telnetd: command not found

---

### Post by hal10000 on 2009-09-03
> sudo: /etc/init.d/telnetd: command not found

sorry, the correct command to start is: [COLOR="Red"]sudo /etc/init.d/openbsd-inetd start[/COLOR]
Then you should be able to telnet

---

### Post by w1z8it on 2009-09-03
> **hal10000 said:**
> sorry, the correct command to start is: [COLOR=Red]sudo /etc/init.d/openbsd-inetd start[/COLOR]
Then you should be able to telnet

Ok still the same issue

$ telnet chaotic-realms.com 25
Trying 81.236.166.248...

---

