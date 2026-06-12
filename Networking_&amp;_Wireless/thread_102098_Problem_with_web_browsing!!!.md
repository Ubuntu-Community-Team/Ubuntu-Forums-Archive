---
title: "Problem with web browsing!!!"
date: 2005-12-11
forum: Networking &amp; Wireless
---

### Post by spacifique1 on 2005-12-11
It seems to be a common problem with Ubuntu.

Ok, here`s the situation:
I have a DSL modem.
It is connected to the PC through the onboard ethernet card.
Power is on.
DSL is on.
ETH is on.
PPP is on.

I can enter the IP of my ISP and connect to the modem config. interface. 
I can ping any [www.xxxxxxxx.com](www.xxxxxxxx.com) websites with 100% send and receive.
But i can`t open any [www.xfghdfgd.com](www.xfghdfgd.com) pages!!!

I have a pppoa type connection.
I can see my IP address on the modem config. interface.

Is DHCP ok or do i need to use static IP?
Does my ISP assign me a new IP at each new connection or do I always have the same? 

Any help would be welcome.
I`ve got only one PC and i have to install/uninstall Windows each time to search info on the web...any definite solution would be much appreciated. I tried        sudo pppoeconf, no results...

Thanks.

---

### Post by Lambert on 2005-12-11
Are you using firefox? 

If you can ping then network is ok. Something else is wrong and I've seen posts about ipv6 solving this. If using firefox then do this.

[LIST]
[*] In the address bar type about:config*. Find this line **network.dns.disableIPv6** and double click on it to change the value to *true*.*
[/LIST]Then see if you can browse site.

---

### Post by mips on 2005-12-11
[http://ubuntuforums.org/showthread.php?t=95350&highlight=ip](http://ubuntuforums.org/showthread.php?t=95350&highlight=ip)

---

