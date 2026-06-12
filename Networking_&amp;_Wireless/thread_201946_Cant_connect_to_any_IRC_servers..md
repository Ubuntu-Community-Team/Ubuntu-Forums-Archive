---
title: "Cant connect to any IRC servers."
date: 2006-06-22
forum: Networking &amp; Wireless
---

### Post by black math on 2006-06-22
Using XChat and im unable to connect to any irc servers. It resolves the domain and everything then just sits there and eventually times out. Im behind a router where a windows box can access the servers so I do not think its the router.

---

### Post by linuxgeekery on 2006-06-22
There are a few things that could be issues.

[LIST=1]
[*]Are you behind a software firewall in addition to the hardware firewall on the router?
[*]Check the router - it's always possible ;)
[*]Are there any error messages?
[/LIST]

---

### Post by black math on 2006-06-22
I do not believe there is a software firewall. Its a pretty vanilla install of dapper. There are no other error messages. No matter what the server is I get the same time out error.

---

### Post by void_false on 2006-06-23
So XChat says something like that:
> Connecting to chat.freenode.net (213.92.8.4) port 6667...
And after few minutes times out?

---

### Post by black math on 2006-06-23
Yes thats exactly it.

---

### Post by void_false on 2006-06-24
I've got the same problem. So I too would like to see the solution. ;)

---

### Post by black math on 2006-06-25
I havent been able to come up with anything to fix this.

---

### Post by void_false on 2006-06-26
Same here. Double checked that firewall is disabled, opened/forwarded ports, etc. Nothing helps. BTW do you have IPv6 disabled?

---

### Post by black math on 2006-06-26
No I havent disabled that but I dont see how that would make a difference. I guess  I could try though. How do you disable it?

---

### Post by void_false on 2006-06-26
I dont think you need to disable IPv6 for IRC. I've disabled it because my hardware dont work with IPv6.

---

### Post by senfnase on 2006-06-27
Same here. tested several different irc clients already (bitch-x, kvirc, xchat) with and without ssl support. no connect to any irc server with any of them. checked firewall a hundret of times nothing works. would be glad if anyone could help!!!

---

### Post by drkknight on 2006-07-22
I too am having the same problem using any irc client (although Xchat is my goal). It times out using any of the typical irc ports. I did install the Kubuntu desktop as well and Konversation worked once, and then stopped working for some reason. IPv6 is disabled, I have no firewall running, my DSL  modem doesn't have a firewall, I don't connect through a proxy, and I'm not on a network. I haven't been able to find any sort of fix to this and it's definatly a Ubuntu problem because Windows and other versions of Linux work with IRC. Any help would be really appreciated before I decide to get rid of Ubuntu.

---

### Post by genreviam on 2006-07-26
One more to add... Same exact problem. Ipv6 disabled, all other net access and ports work fine. Router forwarded 6667 to Ubuntu client IP.

Help is appreciated!

---

### Post by katon on 2007-06-07
hi, so what did you do with this problem???? i also have it

---

### Post by tbooher on 2007-11-18
I have this problem as well. I have a Westell DSL model/router D90-327W15-06. My ISP is verizon DSL. My security is set to work with custom NAT services and I have forwarded port 6667 (UDP) and also tried 8001 (TCP).

Using xchat I can not connect to any irc servers ( irc.accessirc.net,  chat.freenode.net, etc)

a good diagnostic is:
>$ telnet chat.freenode.net 8001
Trying 207.158.1.150...
Trying 204.11.244.21...
Trying 209.177.146.34...
Trying 208.71.169.36...
Trying 216.165.191.52...
Trying 140.211.166.4...
Trying 140.211.166.3...
 and
$ telnet irc.freenode.net 6667
Trying 204.11.244.21...

all without resolution

any ideas?

best,

tim

---

