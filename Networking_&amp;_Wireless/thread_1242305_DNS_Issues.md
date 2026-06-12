---
title: "DNS Issues"
date: 2009-08-17
forum: Networking &amp; Wireless
---

### Post by adambot on 2009-08-17
Greetings,

I am currently having dns resolution issues on one of my boxes.  Dig works, nslookup/ping/everything else does not resolve anything.  I have 5 other boxes that are connected and have no issues with the DNS servers in question.  I can ping by IP address but not DNS name.  I have already tried changing my nsswitch.conf file to be files dns.  I am running Ubuntu 9.04 server with xubuntu-desktop installed.

thanks!
Adam

---

### Post by Brandon Williams on 2009-08-17
dig will always go directly to a name server. It never uses other methods. That said, the same is true of nslookup, so I would expect nslookup to work if dig is working. Other utilities/applications will use gethostbyname, and so will check /etc/hosts before going to name resolution.

Try running tcpdump in a terminal window when you are performing a name lookup.
```
sudo tcpdump -n -vv -i any port 53
```
With tcpdump running, resolve the name once successfully with dig and then once unsuccessfully with each of the other methods (nslookup, ping, and some other program). You're looking for differences in the tcpdumps. Do you see tcpdump output in all cases? Are the source and destination IP addresses the same? Keep in mind that dig may produce more output, since it issues both 'A?' and 'PTR?' requests. What's important is to see outgoing 'A?' requests and incoming 'A?' responses.

---

### Post by adambot on 2009-08-17
THANK YOU SO MUCH FOR THE TCPDUMP TIP!!!!!

I was able to solve the problem by seeing that for some reason dig was using the proper gateway, but nslookup was not...  apparently because i have 2 network cards setup in my system the default gw was not being selected properly (both were added)

So after adding this to my /etc/network/interfaces:
```
up route del default gw 10.10.10.1 eth1
```

my system is now behaving like it should.  not sure why the problem started, however, i have a feeling it was one of the updates i did recently...

Thanks again!!

---

