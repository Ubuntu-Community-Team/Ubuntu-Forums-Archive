---
title: "My Mythbuntu 8.04 has a virus..."
date: 2008-05-07
forum: Mythbuntu
---

### Post by rkand on 2008-05-07
... at least according to my ISP.  I'm still not good enough with linux to go out tracking a problem like this down, can someone point me in the right direction?  This is what my ISP has given me:

IP Add, Errors, Queries
99.236.XXX.XXX,  513, 517

Date Time, Src, Query, Query type
2008-05-05 2008-05-05 08:00:02.17273, 99.236.XXX.XXX, rob-myth.someisp.com., Addr
2008-05-05 2008-05-05 08:00:13.13683, 99.236.XXX.XXX, rob-myth.someisp.com., Addr
2008-05-05 2008-05-05 08:00:01.68468, 99.236.XXX.XXX, rob-myth.someisp.com., Addr
2008-05-05 2008-05-05 08:00:01.80683, 99.236.XXX.XXX, rob-myth.someisp.com., Addr
2008-05-05 2008-05-05 08:00:12.89437, 99.236.XXX.XXX, rob-myth.someisp.com., Addr

Date Time,Dst,Query,Response
2008-05-05 2008-05-05 08:00:02.17319,99.236.XXX.XXX,Error:,3(Name Error)
2008-05-05 2008-05-05 08:00:13.13697,99.236.XXX.XXX,Error:,3(Name Error)
2008-05-05 2008-05-05 08:00:01.68479,99.236.XXX.XXX,Error:,3(Name Error)
2008-05-05 2008-05-05 08:00:01.80695,99.236.XXX.XXX,Error:,3(Name Error)
2008-05-05 2008-05-05 08:00:12.89450,99.236.XXX.XXX,Error:,3(Name Error)

---

### Post by superm1 on 2008-05-07
Do you have this box opened up to the world without putting it behind a firewall?

I'd be a little careful with that as it leaves you more open to attacks.

---

### Post by howlingmadhowie on 2008-05-07
i don't see how this suggests that you have a virus. if the XXX are the same in all cases, it seems to be asking for an address and receiving a name error.

if you're worried about the network packets you may or may not be sending, you can install ethereal and monitor these.

---

### Post by uopjohnson on 2008-05-07
Go to the store and buy a $20 Router.  It will probably take care of this. (and maybe do a fresh install to be sure) It is hard to tell exactly what the problem is from those really limited logs, but sometimes the automated scanning at the ISP picks up regular Linux services as windows viruses.

---

### Post by rkand on 2008-05-07
> **howlingmadhowie said:**
> i don't see how this suggests that you have a virus. if the XXX are the same in all cases, it seems to be asking for an address and receiving a name error.

if you're worried about the network packets you may or may not be sending, you can install ethereal and monitor these.

The source IP addresses are all the same - they're my router's WAN IP address.  However rob-myth is my backend's computer name.

I will check out ethereal, thanks.

---

### Post by ian dobson on 2008-05-07
Hi,

Maybe try adding the name of your backend server to your hosts file.

It looks as if the frontend is sending DNS queries for the IP of your backend to the ISP.

Regards
Ian Dobson

---

### Post by prosonik on 2008-05-08
Hi there,

From your partial ip address, It looks like you are on rogers cable in Canada.. the best isp in Canada! :) 

I had a quick Google of what rogers was sending you. If you do a bit a research, it looks like your pc is hammering the rogers dns server,
which makes rogers, well; Unhappy. A quick read of the topic over at the EhMac forums, it most likely caused by either a)bit torrent application like azerues, or b)some app that is doing dns lookups on the roger dns, instead of say your local machine or router. It's doing a reverse lookup on your ip, to get your mythbox name, probably from your router. I can't remember how this happens, but i know it's possible. I wish i was up more on my DNS. 

That all said, thinking about it off the top of my head, hardy brought us increased support for avahi.. It's a zero-conf network discovery application.. It may use DNS.  Maybe that's whats doing it.

I'm not sure where to point you other then, have a look
at your DNS settings on your mythbox, or your router.. you could always use the openDNS server instead of rogers. Also, somebody's suggestion of ethereal isn't a bad one either. watch for the dns requests, if it looks like it's hammering the rogers dns server, then try shutting down services until it goes away.. 


Here is the link to ehMac:
[http://www.ehmac.ca/mac-ipod-help-troubleshooting/47517-rogers-abuse.html](http://www.ehmac.ca/mac-ipod-help-troubleshooting/47517-rogers-abuse.html)

hope this helps.

prosonik

ps: format your system. Pff!! if your /var/log/messages showed something REALLY funky going on, or if there way maybe crazy network activity, or something to to indicate a virus or worse compromise, then I'd reformat. 
----


[QUOTE=rkand;4900000]... at least according to my ISP.  I'm still not good enough with linux to go out tracking a problem like this down, can someone point me in the right direction?  This is what my ISP has given me:

IP Add, Errors, Queries
99.236.XXX.XXX,  513, 517

Date Time, Src, Query, Query type

Date Time,Dst,Query,Response
2008-05-05 2008-05-05 08:00:02.17319,99.236.XXX.XXX,Error:,3(Name Error)
2008-05-05 2008-05-05 08:00:13.13697,99.236.XXX.XXX,Error:,3(Name Error)
2008-05-05 2008-05-05 08:00:01.68479,99.236.XXX.XXX,Error:,3(Name Error)

---

### Post by agim on 2008-05-08
everybody want to be the one to find a linux virus. lol.

---

