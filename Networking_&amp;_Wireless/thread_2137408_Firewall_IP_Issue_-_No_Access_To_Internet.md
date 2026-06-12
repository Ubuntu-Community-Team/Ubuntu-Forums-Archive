---
title: "Firewall IP Issue - No Access To Internet"
date: 2013-04-20
forum: Networking &amp; Wireless
---

### Post by _user on 2013-04-20
Reference:[http://ubuntuforums.org/showthread.php?t=1496473](http://ubuntuforums.org/showthread.php?t=1496473)

I've been following the above thread to setup the firewall to only allow internet access via the VPN IP address.

I installed gufw and set the rules as follows: [http://i.imgur.com/eJhh5BV.png](http://i.imgur.com/eJhh5BV.png)

[COLOR=#000000]Allow In Both To IP_Address
[/COLOR][COLOR=#000000]Allow Out Both From IP_Address
[/COLOR]
I've verified my IP address is correct by checking Maxmind ([http://www.maxmind.com/en/locate_my_ip](http://www.maxmind.com/en/locate_my_ip))

When I enable the firewall I have no internet access.  Where am I going wrong?

(*I'm aware I need to add the range of IPs for the VPN provider - not just the current one in use.*)

---

### Post by sammiev on 2013-04-20
Post 52 and 54 may just help you of [this]("http://ubuntuforums.org/showthread.php?t=1876124&highlight=sammiev&page=6") thread.

A lot of good reading in the full thread as well.

---

### Post by _user on 2013-04-20
I read through it fully and tried the solution you linked to without success.

How about if I flush the rules from gufw and instead go with iptables.  Not that there should be a difference - just testing a different approach to debug the problem.

How would I allow all traffic only if my ip address is X and reject everything else.  In other words - allow normal use whilst on the VPN and reject/drop it should the VPN fail.

---

### Post by sammiev on 2013-04-20
What caused my problem was the data path, I knew everything else. I never played around with anything else as I wanted to keep my Deny In and Deny Out on my main settings as is if or when my VPN provider goes down or does maintenance, I would still be able to carry on with no issues.

I'm sure someone with more experience will be by shortly to shed more light on your problem. Wish I could have been more help.

---

### Post by _user on 2013-04-24
Anyone else know how to do this via iptables instead?

---

