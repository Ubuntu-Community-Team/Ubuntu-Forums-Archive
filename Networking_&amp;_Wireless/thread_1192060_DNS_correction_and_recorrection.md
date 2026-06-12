---
title: "DNS correction and recorrection"
date: 2009-06-19
forum: Networking &amp; Wireless
---

### Post by lucio.santos on 2009-06-19
I have 8.04 and 7.04 running on an ASUS A6000U. One problem is that the DNS setting allways get a wrong value. I correct the DNS setting, it works for a while, and after some time it falls back to another value (always the same primary and alternative DNS servers). I suspect I have an intrudder in my computer. How can I check that? Is there anybody who already had such a problem? The problem started just today and occurs in both distributions.

Thanks!

Lúcio

---

### Post by papangul on 2009-06-20
Don't worry, this is a common problem in Ubuntu and intruders don't mess with DNS settings generally.;)

You may either try to "prepend" DNS addresses in the /etc/dhcp3/dhclient.conf (you have to restart networking to make it effective), or you may use WICD network manager and set your dns through it:
[http://ubuntuforums.org/showthread.php?t=1150797](http://ubuntuforums.org/showthread.php?t=1150797)

---

### Post by lucio.santos on 2009-06-20
Thank you, papangul! It worked. I've set the DNS server at dhclient.conf . It now keeps the server address I've entered, but adds automatically the old servers IPs. 
Also I downloaded and installed wicd and set the DNS servers there.  
I can't see the alternative DNS server working: when I invoke System>Administration>Network, I see the one I set at dhclient.conf and the other 2 IPs that are always misteriously there...! So, there are 3 DNS servers, but not the second that I added by wicd. 
Oops, at dhclient.conf I don't know how to set more than one DNS address. Shoud I use a colon, semicolon or just a space?
 Anyway, your reply was very successful! Thanks a lot! And I guess wicd will also help me get my wireless working!

Best greetings,

Lúcio

---

### Post by papangul on 2009-06-20
It's like this:
> prepend domain-name-servers 208.67.222.222, 208.67.220.220;
Also there are two other parameters in the dhclient - "require" and "request". One of them fetches the dns from the gateway and appends it after the ones that it is supposed to "prepend".
Hope I am able to get the message accross.:)

---

