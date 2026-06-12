---
title: "Need a way to bar internet access for a user"
date: 2009-05-13
forum: Networking &amp; Wireless
---

### Post by BattlePanic on 2009-05-13
This isn't really an OS specific question but I'm hoping some network experts here might be able to help me out.  I'm looking for a way to prevent specific user from accessing the internet while still permitting him access to our local network.  I'm guessing the easiest way to do this is to not specify the default gateway address when configuring he machine's network adapter.  Is this a feasbile way to bar internet access for a specific user?  Am I overlooking anything here?  Thanks in advance.

---

### Post by kryptikos on 2009-05-13
The best way to do this is actually at the router/switch level or utilize a firewall between your local network and the router/switch to the outside world. You would code in access rules to drop/ignore packets sent from a specific IP address or range of IP addresses destined for port 80, 8080 or any other particular port you do not wish to have them access. 

If you drop the default gateway the box itself will have trouble knowing where to send traffic (ie the local network). 

That's a limited suggestion without knowing the network layout and such.

---

### Post by BattlePanic on 2009-05-13
This particular machine will be configured for both users with internet access and those without.  I'm assuming this would prohibit any means of configuring a router/switch to handle such access restrictions.  Any ideas?

---

### Post by gtr32 on 2009-05-13
Would this work on the firewall side?

```
iptables -A OUTPUT -o $ADAPTER -m owner --uid-owner $USER_ID -j DROP
iptables -A OUTPUT -d $LOCAL_ADDRESS_RANGE -o $ADAPTER -m owner --uid-owner $USER_ID -j ACCEPT
```

---

### Post by kryptikos on 2009-05-13
You'd have to modify your setup a little bit. You'd have to configure a box to act as a web proxy and stick that in front of the router/firewall. Then on the router/firewall only allow web based traffic to/from the proxy and ignore the rest. 

Forgive the crude ascii art but basically you are looking for something like this:


                                     OUTSIDE WORLD
                                          |
                                     ROUTER/FIREWALL
                                          |
                                    ____PROXY_____             
                                    |     |       |
                                   PC     PC     LAPTOP

You could then use firewall rules and proxy rules to drop unauthorized web requests based on time, IP address, network, or users. 

Check out Squid proxy. Here is a little leisure reading:

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch32_:_Controlling_Web_Access_with_Squid]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch32_:_Controlling_Web_Access_with_Squid")

---

### Post by Carl Hamlin on 2009-05-13
Why are you trying to bar someone's internet access, in particular?

---

### Post by kryptikos on 2009-05-13
> **gtr32 said:**
> Would this work on the firewall side?

```
iptables -A OUTPUT -o $ADAPTER -m owner --uid-owner $USER_ID -j DROP
iptables -A OUTPUT -d $LOCAL_ADDRESS_RANGE -o $ADAPTER -m owner --uid-owner $USER_ID -j ACCEPT
```

Depends on his particular type of router/firewall but yeah...that's the jist of it. 

He could also just directly link that to the computer the person is using and coding that into /etc/network/interfaces.

"pre-up iptables -A OUTPUT -p tcp -m owner –uid-owner username -j DROP"

---

### Post by mozkill on 2009-05-13
Evidently, there is a way in windows if the computer is part of a domain:  [http://windowsitpro.com/article/articleid/85079/jsi-tip-10092-how-can-i-block-internet-access-for-a-specific-user-account.html](http://windowsitpro.com/article/articleid/85079/jsi-tip-10092-how-can-i-block-internet-access-for-a-specific-user-account.html)

---

