---
title: "Slow DNS Lookup times in 11.04"
date: 2011-06-04
forum: Networking &amp; Wireless
---

### Post by Wayne Thomas on 2011-06-04
Hello everyone! This is my first post so please bear with me if I dig up material already covered :)

I just installed Ubuntu 11.04 in a dual boot environment on a spare laptop( Dell Inspiron 6000 )
I have other machines using older distro's of Ubuntu but do not have them all on line... utility costs are ridiculous here..anyway....  I found some optimization tips for Firefox and those have been done and I did find earlier information about this or a very similar problem but all the suggestions mentioned there are already in place here  network wide..  Basically what is happening is this: When a web site is opened from the browser in the lower left hand of the screen it displays "Looking up www.google.com" or what ever url was entered.

I know Win is not a good comparison and I haven't gotten any additional Ubuntu boxes on line yet but Win seem unaffected by this.

Any recommendations as to what I should try next??  I have DNS server information stored in the router using Google Public DNS and Open DNS as a backup and uPNP is disabled.  Seems like the program (Ubuntu) is plenty fast even on this Celeron based machine but the time taken to look up DNS data is a lot slower than anticipated.

Any ideas, suggestions and help in General  Greatly appreciated!!!




Regards,

Wayne

---

### Post by Michel Boaventura on 2011-06-04
This is an old issue. Seems related with libdns and some routers which doesn't support ipv6. As far as I remember, there is only workarounds for this. You can use google's dns servers (8.8.8.8 and 8.8.4.4) or install bind in your machine and use it as your dns server.

---

### Post by Wayne Thomas on 2011-06-04
Thanks so much! My router is a Linksys/Cisco WRT 110 and to be honest I am not sure that it supports IPV6. So since I am not sure on that subject maybe the best approach is to use a hard coded DNS.

Which approach seems to be the quickest to implement and if there is a supporting thread let me know and I will be sure to look at that as well...

Thanks again for the help!


Regards,

Wayne

---

### Post by Wayne Thomas on 2011-06-04
Update to the problem:
I thought I would bypass the router almost totally as far as DNS was concerned by manually configuring the connection(wireless and wired) using 8.8.8.8 and 8.8.4.4 for name servers and it seems that has helped the process considerably.  I'll play along with this a day or so and see how it reacts overall and report back.



Regards,

Wayne

---

