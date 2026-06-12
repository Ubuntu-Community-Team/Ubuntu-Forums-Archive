---
title: "Internet Sharing - I hit a snag"
date: 2010-08-01
forum: Networking &amp; Wireless
---

### Post by JNied on 2010-08-01
I was following this tutorial:
[http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html](http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html)

And got to this part:
[FONT="Courier New"]# /etc/init.d/dnsmasq restart[/FONT]
And got the following:```
root@Jason-Lin:/# /etc/init.d/dnsmasq restart
 * Restarting DNS forwarder and DHCP server dnsmasq                             
dnsmasq: failed to create listening socket: Address already in use
                                                                         [fail]
```

I don't know what address it's referring to.  I thought it might have meant that my IP address is already being used on the network, but I made sure that wasn't the case.

Any help would be greatly appreciated.

---

### Post by sikander3786 on 2010-08-01
Hi.

Why are you getting too complex sharing the Internet? Do you want to cache?

Why don't you use Firestarter? It will do everthing for you like a charm. It will do all the NAT and iptables thing itself. Just a few clicks away.

Regards.

---

### Post by Iowan on 2010-08-01
Thought a Firestarter [bug]("https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/258863") made [UFW]("https://help.ubuntu.com/community/UFW") a better choice, but I see a fairly current help page for [Firestarter]("https://help.ubuntu.com/community/Firestarter").

As far as **dnsmasq**, I use it on my network - *might* need to see your config file.

---

### Post by JNied on 2010-08-02
> **sikander3786 said:**
> Hi.

Why are you getting too complex sharing the Internet? Do you want to cache?

Why don't you use Firestarter? It will do everthing for you like a charm. It will do all the NAT and iptables thing itself. Just a few clicks away.

Regards.To answer your "why" question: because I didn't know that was an option.  Whenever I googled "internet sharing in linux" or "ubuntu version of ics" or the likes, all I ever got was that IP masquerading tutorial.  This is the first I've heard of firestarter.  I downloaded that and it works perfectly.  Thanks.

---

### Post by JNied on 2010-08-03
Alright, well it worked perfectly at first.  Now when I run it I get: > Failed to start the firewall

An unknown error occurred.

Please check your network device settings and make sure your Internet connection is active.However, despite this error, the firewall status still shows "Active", and my other network devices can connect to the Internet.  However, I have no Internet (the computer that's actually connected to the Internet cannot connect to the Internet).  If I disable the firewall, the opposite happens; I have Internet and the other devices on my network do not.

---

### Post by dansang on 2010-08-24
Having the same problem with firestarter. It's as if network manager 0.7 is only allowing one connection to internet, sharing is not allowed. I tried using gadmin to set up dhcp server. But still having problems with that. Going to try again..i really need to get my mobile broadband connection shared.

---

### Post by Iowan on 2010-08-24
I presume you've seen [this]("https://help.ubuntu.com/community/Internet/ConnectionSharing") help page?

---

