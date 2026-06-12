---
title: "Ethernet/firefox problem."
date: 2006-01-08
forum: Networking &amp; Wireless
---

### Post by aum11 on 2006-01-08
I have this weird problem where I can use ethernet successfully under windows xp, but not under Ubuntu.  When I am under Ubuntu gmail notifier is able to check the email status successfully,but thunderbird and firefox 1.5 cannot return data. There are no error messages. Eth0 seems to be working fine but no data is returned.  
  
I have turned off firestarter just in case it was the culprit.

It appears that it is just firefox and thunderbird that are being blocked.

Any suggestions?

---

### Post by cwaldbieser on 2006-01-08
[QUOTE=aum11]I have this weird problem where I can use ethernet successfully under windows xp, but not under Ubuntu.  When I am under Ubuntu gmail notifier is able to check the email status successfully,but thunderbird and firefox 1.5 cannot return data. There are no error messages. Eth0 seems to be working fine but no data is returned.  
  
I have turned off firestarter just in case it was the culprit.

It appears that it is just firefox and thunderbird that are being blocked.

Any suggestions?[/QUOTE]

You will need to provide more information about how you connect to the Internet (direct connect vs. through a router, dialup or broadband, wired or wireless, etc.).  Router/modem model numbers are good too.

Can you ping a website you want to browse in Firefox?  If you open a terminal and use "wget", can it fetch the page you try to get with Firefox?

---

### Post by aum11 on 2006-01-08
Have just checked using wget and the url is resolved successfully but connecting to the web page just hangs.

At the same time gmail notify reported a new email delivered, so some connection is happening but not for ffox or thunderbird.

I am connecting through a dlink dsl-502t.

---

### Post by bunced on 2006-01-08
I have come across a similar issue before - I believe you're using an IPv6 protocol and Firefox on Ubuntu seems unable to handle such a protocol. Could you try seeing if you can browse with Konqueror (install it if it's not there) or turn of IPv6 on your router.

---

### Post by aum11 on 2006-01-08
Thanks bunced, IPv6 was the problem.

You guys are great...I have been hounding this problem for hours!!!

---

### Post by rgs on 2006-01-08
Thanks from me too.  I've been fighting this for _WEEKS_.  I could not find where to disable it in my router but you can in the ffox config file.

rgs

---

### Post by oliwally on 2006-01-14
Hi there, 

> turn of IPv6 on your router

I have the same problem with my DSL-502T and I'm not sure how to turn off the IPv6 on it. I have the modem connected through a little hub. Please tell me how to turn off the IPv6 on the modem / hub. 

I had no such problems with my previous modem (DSL-302G) which broke and got replaced under warranty.

---

### Post by mips on 2006-01-15
[http://ubuntuforums.org/showthread.php?t=78337](http://ubuntuforums.org/showthread.php?t=78337)

---

### Post by oliwally on 2006-01-17
[QUOTE=mips][http://ubuntuforums.org/showthread.php?t=78337](http://ubuntuforums.org/showthread.php?t=78337)[/QUOTE]

Thanks so much for helping out mips. Most of that was a bit too curley for me (Options 1 & 2).

However, I found that python's Option 3 on the link you provided solved my problem. (If others want to shortcut to it - Option 3 was : [http://www.ubuntuforums.org/showthread.php?t=11544&highlight=d-link+adsl+router](http://www.ubuntuforums.org/showthread.php?t=11544&highlight=d-link+adsl+router))

---

