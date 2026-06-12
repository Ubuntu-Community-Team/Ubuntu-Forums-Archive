---
title: "Custom Router"
date: 2010-02-04
forum: Networking &amp; Wireless
---

### Post by thecoshman on 2010-02-04
I have spent about three days more or less solid (even reading at work;)) slowly getting this closer and closer to being set up correctly.

I have my old laptop, which I have installed 9.10, yes I used the desktop version but I can trim that fat once I have got this running.

I brought my self a bargain of a wireless n card, a Linksys /athero card. I was able to set up an ad-hoc network and use my other laptop to 'see' the outside world, long enough to tweet about it :P will post a link btw if people want one whilst its cheap. Not sure on rules, so playing it safe.

however, that was only an ad-hoc network, so I kept looking and found hostapd which let me use my wireless card as an Access point. This I have managed to get working. I know this works as I can use the other laptop to get into webmin on the router.

at the moment, I am just manually starting hostapd from a console, but not as a daemon so I could see what's going on as I access it, this also lets you see when anybody else tries to log onto your AP... if they don't spoof the MAC. I am fairly sure how to add the command to start hostapd when the computer starts up, but if someone could just tell me quickly that would be nice and handy.

The problem is, I can't get a laptop to go 'through' the router to the out side Internet. using webmin, the only rule I have set up in iptables (after resetting iptables to accept everything, I know, but I will lock down once it works) is under NAT, to masquerade if output is eth0, which is the routers interface to the outside world.

currently in work, and realised that I never tried manually entering the IP rather then just 'google.com' for example. So I am thinking that I may need to set up a DNS server. But, seeming as when on the router I can use a DNS server that already exists, and the router 'should' be set up to rout all packets through it, should not the laptop connecting to my Access point/router be able to see that DNS as well?

As a final thing, the guides I found for setting up hostapd seemed to all mention setting up a bridge between the wireless and the wired connections. Correct me if I am wrong, but I shouldn't need to do this should I? should not the router side of things read the packets from the wireless, notice that they need to go out the wired and thus chuck them that way?

End of very long explanation. Once I have worked out how this is all going, I do plan to fill the seemingly missing gap of explanation for this set up with 9.10 as all the stuff I could find was from about 2004 to 2008 

Thanks for any help

---

### Post by superprash2003 on 2010-02-04
from your whole post i think what you are trying to achieve is internet connection sharing?

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

firestarter could also do this for you

---

### Post by thecoshman on 2010-02-04
From reading that link you gave me, and where I have got to so far, I believe that I just need to set up DNS, which I will attempt when I get a chance. I do wan't to do more then just share the internet connection, I am wanting to also set up some bandwidth monitoring/limiting/balancing as well as apt-cache (I belie that's the one). Their's also the side of me that just wants to prove I can do this now :P

---

