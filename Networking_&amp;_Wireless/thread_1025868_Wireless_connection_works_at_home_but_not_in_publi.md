---
title: "Wireless connection works at home but not in public"
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by alphatrak on 2008-12-30
I can connect and get access to internet at home just fine (secured wireless), but when I go to Kansas City International airport, Ubuntu says it is connected with 100% signal strength but i can't get to web pages. I've tried sudo dhclient eth1 but that still didn't work. Any ideas?

---

### Post by Rohan Kapoor on 2008-12-30
> **alphatrak said:**
> I can connect and get access to internet at home just fine (secured wireless), but when I go to Kansas City International airport, Ubuntu says it is connected with 100% signal strength but i can't get to web pages. I've tried sudo dhclient eth1 but that still didn't work. Any ideas?
At any airport's wifi, it should connect then load a webpage asking for a credit card or login credentials.

---

### Post by alphatrak on 2008-12-31
At KCI (Kansas City International), their wifi doesn't have any security. I can connect using Vista just fine on the same laptop (dual booted with Ubuntu) (There's no custom webpage), so I'm not sure why Ubuntu has a problem. When I try browsing with Ubuntu, it doesn't even get that far.

Below is the result of "sudo dhclient eth1" (eth1 is my wifi device). It doesn't look right. "renewal in 345 seconds" seems a tad short. :) Is there something I'm missing? I haven't had a chance to try connecting to another wifi with no security yet, as I'm on vacation (in Vegas for New Years woohooo!)

I'm also unable to ping anything

Thanks!


$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:1a:73:f7:cd:f8
Sending on   LPF/eth1/00:1a:73:f7:cd:f8
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPOFFER of 10.203.62.210 from 10.203.63.254
DHCPREQUEST of 10.203.62.210 on eth1 to 255.255.255.255 port 67
DHCPACK of 10.203.62.210 from 10.203.63.254
SIOCADDRT: No such process
bound to 10.203.62.210 -- renewal in 345 seconds.

---

### Post by treesurf on 2009-03-21
I have had the exact same problem at the San Francisco and San Diego airports recently.  These airports do have a custom login webpage, but it won't even load that page in Ubuntu although I have a strong wireless signal.  Vista has no problem.  Any suggestions?

---

### Post by Rohan Kapoor on 2009-03-21
You know... Strangely I've had several problems myself recently regarding this. My school has several AP's across campus that are unsecured and then login from the web-browser. The connection times out on 4/7 but works on the 3/7 others. Since I'm friends with the IT guy, I just had him reset all of them and now Ubuntu works with all. You could ask the guys at the airports to do that but you know...

---

### Post by treesurf on 2009-03-22
Yeah, I don't the airport network admins will be too cooperative about that...

Really, I figure if Vista can access the network, then Ubuntu should be able to also.  Just need to figure out what the problem is.

---

### Post by Rohan Kapoor on 2009-03-25
> **treesurf said:**
> Yeah, I don't the airport network admins will be too cooperative about that...

Really, I figure if Vista can access the network, then Ubuntu should be able to also.  Just need to figure out what the problem is.
Hmmn. I see but it sounds like a standard network time out error to me.

---

### Post by PhilipGanchev on 2011-05-07
I can't connect to any networks at any airports I've tried: Pittsburgh, Chicago, Atlanta, San Francisco, Raleigh and Seattle. They are all unprotected networks.  This older thread is no help either: 
[http://ubuntuforums.org/showthread.php?t=518522](http://ubuntuforums.org/showthread.php?t=518522)

Nor is this old blog post:
[http://tips.webdesign10.com/configuring-wireless-on-ubuntu-linux](http://tips.webdesign10.com/configuring-wireless-on-ubuntu-linux)

---

