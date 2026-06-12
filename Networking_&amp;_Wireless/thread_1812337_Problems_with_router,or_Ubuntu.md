---
title: "Problems with router,or Ubuntu?"
date: 2011-07-26
forum: Networking &amp; Wireless
---

### Post by cbrrizzi on 2011-07-26
Recently Installed Ubuntu on my laptop, a Toshiba T135-S1305.  Before this was running Windows 7 and had no problems with my internet at all.  Now however I have a couple of problems.

1.  The internet will randomly stop working.  My laptop wont disconnect from my router, it just wont load pages.  I then have to diconnect and reconnect to my router and everything is fine and dandy.  It gives me a DNS issue (I believe, I'll get a screenshot next time it happens).
2.  Youtube wont come up, it sends me to a website, called youtube.com, but its one of those pages that states that youtube is "currently under construction - coming soon".  This in includes inbedded youtube videos and links for youtube.

I dont have these problems on my Iphone, or PS3.  And I am yet to have anyone come by running Windows, however like I said I did not have any of these problems until Ubuntu.  The solutions I have tried include:

1.  Resetting the router (multiple times)
2.  Reducing the "RTS Threshhold"
3.  Reinstalling Ubuntu 11.04, trying 10.10 and Fedora
4.  Disabling IPV6.
5. Tried the IP for youtube with no name and the http://

Any thoughts, possible solutions??

Please and thank you for any ideas you might have

---

### Post by elliotbeken on 2011-07-26
I have a similar problem, have you tried changing your DNS server from a local IP address such as 192.168.0.1 or 192.168.2.1 to a public one like 8.8.8.8 or 208.67.222.222

I am not sure why this made a difference as the router was pointing me to 8.8.8.8.

Hope this helps

---

### Post by cbrrizzi on 2011-07-26
Tried it, the youtube thing still happens and I am currently trying to replicate the loading problem, to see if it still happens.

---

### Post by cbrrizzi on 2011-07-26
Ok, I figured it out.  It was my DNS server like you suggested, I just had to change the DNS settings under my Network Icon.  Then I just had to "edit connections" and set it to "Automatic (DHCP) address only and put the new DNS names.  I also changed it under my routers settings, which I did manual set up.  Thanks alot, much appreciated.

---

### Post by cbrrizzi on 2011-07-26
P.S.
How do I set this thread as solved?

---

