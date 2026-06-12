---
title: "Can I pass an ignore file to `sudo dhclient ath0`?"
date: 2009-04-14
forum: Networking &amp; Wireless
---

### Post by ubunny on 2009-04-14
If I want dhclient to ignore 192.168.0.113 for example, how do I go about telling sudo dhclient ath0 to ignore it?  Can I pass an ignore file?  

thx

---

### Post by chili555 on 2009-04-14
Are you trying to avoid a conflict with another machine on the network that has a static IP address of x.113? This is better done, in my opinion, in the router's administration pages. I suggest you allow the router to assign IP addresses by DHCP in the range from x.90 to x.100. Then any machines with static addresses should be set up with addresses from x.101 on up.

---

### Post by ubunny on 2009-04-14
no, all IPs are from DHCP.  For whatever reason though 113 really sucks whenever I'm assigned to it by kicking off every few minutes.  So I'd just prefer to ignore it.

I'm on a wireless connection for my building and I don't have access to the landlord's router.  Our MACs are accepted and IPs assigned dynamically via DHCP.  It doesn't have to be the same one everyday.  Some work better than others.  I've had IPs in the range of 192.168.0.101 to 125 and back.  There might be more but I'm not tracking it.

Better to just block IPs I don't like and have at the point of assignment a block list.  This is to say it doesn't have to be dhclient that does this, but since it makes the assignment from DHCP I was assuming that this would be where to do it.

The dreaded 113...
```

DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.0.113 from 192.168.0.1
DHCPREQUEST of 192.168.0.113 on ath0 to 255.255.255.255 port 67
DHCPACK of 192.168.0.113 from 192.168.0.1
bound to 192.168.0.113 -- renewal in 295386 seconds.

# test connection
~/bin$ host rogers.com
rogers.com has address 207.245.252.27
rogers.com mail is handled by 10 mx1.rog.mail.yahoo.com.
rogers.com mail is handled by 20 mx2.rog.mail.yahoo.com.

# a few minutes later
~/bin$ host rogers.com
;; connection timed out; no servers could be reached

# only happens with 192.168.0.113

```

any suggestions welcome!

---

### Post by chili555 on 2009-04-14
Have you tried a static IP of, say x.130?

---

### Post by ubunny on 2009-04-14
tried that now, and a few others, it just sits on DHCPDISCOVER.  Can't seem to get any except 113 today, that may be all that's available. :(

---

### Post by chili555 on 2009-04-14
> it just sits on DHCPDISCOVER.If you are using a static IP address, DHCP should not be used. How are you specifying the address? Through Network Manager?

---

