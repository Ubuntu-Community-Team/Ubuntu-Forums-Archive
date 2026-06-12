---
title: "how to list ip and mac address of users on a network??"
date: 2010-06-15
forum: Networking &amp; Wireless
---

### Post by kenjush on 2010-06-15
hi
I want to find out ip addresses and also mac addressed of users connected to the same wifi router as me! 
how can I do that?!

---

### Post by DGortze380 on 2010-06-15
> **kenjush said:**
> hi
I want to find out ip addresses and also mac addressed of users connected to the same wifi router as me! 
how can I do that?!

It's possible.. but we're going to need some more information. 

Do you have a legitimate reason to do this? What is it? Do you own the network these machines are one? Do you own the other clients? 

If not, you're not going to get much help here (rightly so).

---

### Post by cj.surrusco on 2010-06-15
I don't know if it possible to do that from a computer connected to the network. I can do it by opening up my router in a web browser and it tells me there.

---

### Post by bigmojo74 on 2010-06-15
@DGortze: Honestly in most cases that's broadcasted information, Windows machines are especially chatty and easy to see. You wouldn't need to own the equipment or attached devices to look at what their IPs are, public info at that point. However I do agree that it would fall under network recon - and could be viewed as a precursor to hostile activity - but not everyone who's curious is hostile.

Like CJ said the easiest way to do this is to log in to the network device/DHCP server to see what leases it has. If you don't have access to that you should consider what exactly you want this information for.

Finding this information uses the well known protocol arp, read up on it, and you'll figure this out fairly quickly I'm sure. You'll get more satisfaction learning on your own than getting quick answers on a forum.

On a personal note, if you're seriously just that curious set up test equipment at home, playing around on someone elses' equipment is like kicking a hornets nest. You maybe curious what will happen, but it's totally not worth it in the long run.

Edit: If this isn't your gear but you want to work on this at home, set up a DHCP server and a client. There's a ton of ways to do this sort of thing, all good to know for troubleshooting, doing it with your own gear will make you learn all of the processes involved.

---

### Post by Bucky Ball on 2010-06-15
If your router is running as a DHCP server, yes, you are going to get MAC addresses, etc. BUT, if you're running three machines set to static IPs on the local machine (not setup in the router) and the DHCP server on the router is switched OFF, then the router shows no sign of the machines connected whatever.

---

### Post by kenjush on 2010-06-16
I searched a little bit and finally found something great! :guitar:
"tuxcut" 
also you can use "netcut" in windows os!

this software does exactly what I wanted! :lolflag: when u join a wireless network it shows you ip addresses and mac addresses of the clients!


tuxcut website:
```
http://bitbucket.org/a_atalla/tuxcut/wiki/Home
```

---

