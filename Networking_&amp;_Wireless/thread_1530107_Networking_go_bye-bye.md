---
title: "Networking go bye-bye"
date: 2010-07-13
forum: Networking &amp; Wireless
---

### Post by JNied on 2010-07-13
I've completely switched over to Linux, except that the only feature I *can't* get to work in Linux is Internet Sharing.  I followed the IP Masquerading tutorial here:
[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)
And now I have no networking.  I can still connect to my wireless router using automatic configuration (DHCP), and I get the same settings as the other computers on my network.  However, when I actually try to go to a website, I get a network error.  I try to ping my gateway and DNS from the terminal and I get an error stating I'm not allowed to ping.

I'm sure you're all aware how terrible it is to be stuck in Windows, so any help would be greatly appreciated.

---

### Post by Iowan on 2010-07-13
Have you seen [this]("https://help.ubuntu.com/community/Internet/ConnectionSharing") ICS help page?

The ping error kinda sounds like an firewalling (iptables) problem...

---

### Post by JNied on 2010-07-14
When I originally tried to get the Internet Sharing to work, I was connected to a log-in type Internet service via my Ethernet cable, and other computers were to connect to me using the wireless card.  For the next couple of weeks, however, I don't have to worry about that.  I simply need to connect to a wireless router with DHCP.  I can connect to the router just fine, but when I try to pull up a website, I get this:

[img]http://img.gcnation.net/screenshots/temp/network/internet.png[/img]

And when I try to ping my gateway, I get "operation not permitted".

All I'm worried about right now is getting my wireless to work properly so that I have Internet where I'm at now, I'll worry about sharing later.

---

### Post by Iowan on 2010-07-14
There's that note about "proxy server" that might be worth checking...
Check **iptables -L** (post if possible) to see what firewalling rules are in place.

---

### Post by JNied on 2010-07-15
```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            
LOG        all  --  127.0.0.0/8          anywhere            LOG level warning 
DROP       all  --  127.0.0.0/8          anywhere            
LOG        all  --  anywhere             anywhere            LOG level warning 
DROP       all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level warning 
DROP       all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level warning 
DROP       all  --  anywhere             anywhere
```

---

### Post by Iowan on 2010-07-15
I'm looking at [this]("https://help.ubuntu.com/community/IptablesHowTo") How-To... trying to learn more about **iptables**. For more details, check **iptables -L -v** - otherwise, it looks like everything should be accepted. As you might have guessed, I'm a real rookie in **iptables**...

---

