---
title: "pppd problem?"
date: 2009-10-29
forum: Networking &amp; Wireless
---

### Post by HMH362 on 2009-10-29
Ok I did some digging around and found this old post 
**[COLOR=#980101][B][ubuntu]**[/COLOR] [SOLVED] GNOME PPP Check permissions  
This seems to be my trouble also.Now I only have 1 question before I mess up my system for the 12th time....lol. I didn't see any dip group in the permissions thingy.So I just add that? 
I added myself to every thing already but can only connect under a sudo wvdial command. I'm confused about what my main group should be.It took me 6 weeks to figure out how to get my modem to work...lol. Downloaded a bunch of stuff and installed it all and found out later didn't even need 80% of it.
 Oh btw I posted this here bcause I wasn't sure if it was ok to add to a old post.
[/B]

---

### Post by _duncan_ on 2009-10-30
Just open a terminal and enter the following:

```
sudo adduser [COLOR="Blue"]yourUserID[/COLOR] dip
```

where [COLOR="Blue"]yourUserID[/COLOR] is the actual user ID you are using.


logout and login again for the changes to take effect.

---

### Post by HMH362 on 2009-10-31
cool thanks that fixed that...lol.

---

