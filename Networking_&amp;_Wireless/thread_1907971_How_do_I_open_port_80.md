---
title: "How do I open port 80"
date: 2012-01-12
forum: Networking &amp; Wireless
---

### Post by Fertech on 2012-01-12
I had my website working yesterday, fwd port 80 until I reboot my computer this morning. Port 80 is close, I have no clue what happen. does any body has any idea what happen and how to fix it.

---

### Post by MG&amp;TL on 2012-01-12
you tag your thread Lubuntu-but what are you actually running? (reason I ask is because lots of people mistake Lubuntu for Ubuntu in the tags list)

---

### Post by haqking on 2012-01-12
There is no such thing as a closed port as such, it is either a service is listening on a port or not, a port doesnt become closed really.

So are you running apache ? and now you cannot access the website running on that machine you mean ?

if it is on a machine in your LAN and you trying to access it externally then the port needs to be forwarded on your router to the machine running a web service, and you need something like dynamic DNS or your external IP may have changed so you cant access it etc ?

We need more network information

---

### Post by imachavel on 2012-01-12
yes seriously dynamic dns should be set up with dynamic i.p. addresses. It is more secure but it is also liable to slow things down.

back to your port, open up your router by logging in via i.p. address. How did you have port 80 (htp) opened the first time? You need to open it, verify if it's a udp or tcp port(I don't really know off hand) and add the i.p. address of the computer you are trying to open the port to connect to. Yes they are either listening or not, of course if it's not listening then it's more secure, but out of curiosity isn't port 80 opened by default do you connect to an entirely seperate router like i.s.p. modem to access the internet, and a seperate router hard wired to connect to your internal network? More network info is needed, otherwise it's kind of hard to answer your question

e.g..:" I have a dell pc and a mac, guys, I need to set up clustering in one sector of the building, and load balancing in the other, umm, need some i.p.'s and dns's, also I have two routers one is cisco and another is vlan I think or something, please help do you need password to log on?"

wouldn't that be hard to answer? Hhaha

---

### Post by jonobr on 2012-01-12
Hello


ON your webserver open a terminal window or use CLI to
type the following command

```
sudo tcpdump -i any port 80
```

Leave the thing open and then do webstuff externally to your server.

If you get a line pop in on your cli, then its receiving packets and is a config issue on your webserver.
If you see nothing in that window, then your issue is not on the port or the webserver, it would mean packets are not getting to the NIC on your webserver.

---

### Post by Fertech on 2012-01-12
I'm running ubuntu, I don't know how it's under lubuntu, but anyways I had it running yesterday. From what I know firewalls can block the port, but that was the whole reason why I deleted my firewall cause I been having problems with my website. All I know is that, yesterday it was working fine. I had one of my friends look at my server and she said it was up.
All I did was reboot the computer and I did turn off my modem and router. 
so this morning I update my ip in dyndns.

I could see my server on my lan, 127.0.0.1  or 192.168.0.101 or localhost

This is all I got from sudo tcpdump -i any port 80

tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on any, link-type LINUX_SLL (Linux cooked), capture size 96 bytes

---

### Post by Fertech on 2012-01-12
Here is a screenshot of my ports

---

### Post by jonobr on 2012-01-12
Hello

If tcpdump only gave you this

```
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on any, link-type LINUX_SLL (Linux cooked), capture size 96 bytes
```


Then no web (port 80) traffic is making it from your router to the ubuntu server.

---

### Post by haqking on 2012-01-13
> **Fertech said:**
> I'm running ubuntu, I don't know how it's under lubuntu, but anyways I had it running yesterday. From what I know firewalls can block the port, but that was the whole reason why I deleted my firewall cause I been having problems with my website. All I know is that, yesterday it was working fine. I had one of my friends look at my server and she said it was up.
All I did was reboot the computer and I did turn off my modem and router. 
so this morning I update my ip in dyndns.

I could see my server on my lan, 127.0.0.1  or 192.168.0.101 or localhost

This is all I got from sudo tcpdump -i any port 80

tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on any, link-type LINUX_SLL (Linux cooked), capture size 96 bytes

You cant delete your firewall, any firewall interface you use such as UFW/GUFW etc uses netfilter which is the firewall built into the Linux kernel usually controlled with IPTables.

I expect you have still have a rule blocking traffic from whatever you deleted.

---

### Post by Fertech on 2012-01-13
I just found out that when I reboot my system, my internal ip change from 192.168.0.102 to 192.168.0.101  I guess I had another system on the router before I restarted my system again.

I just port fwd 80 from 192.168.0.101 and that resolved my problem.

---

### Post by haqking on 2012-01-13
> **Fertech said:**
> I just found out that when I reboot my system, my internal ip change from 192.168.0.102 to 192.168.0.101  I guess I had another system on the router before I restarted my system again.

I just port fwd 80 from 192.168.0.101 and that resolved my problem.

Cool glad you got it sorted.  I would suggest assigning a static IP to prevent that from happening.

Cheers

---

### Post by jonobr on 2012-01-13
Also, the tcpdump I gave you is really useful for seeing what hits the interface of your machine.

Tcpdump works for all sorts of ports such as ssh, ftp, dns and so on.

---

### Post by Fertech on 2012-01-13
Static ip  sounds like a good idea.

I did try that tcpdump code after I fix it, it's very useful.

thank you for your  support.

---

