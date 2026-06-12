---
title: "Help with network problem."
date: 2010-08-28
forum: Networking &amp; Wireless
---

### Post by hiko2 on 2010-08-28
Hi, i got a bit of a interesting thing. Tonight, the internet was a bit slow, and i thought someone might be stealing the signal. So i pop up etherape, so i can check it out, and i found out the most weird screen in there. I cant really describe it so i just gonna post a screenie. If someone can tell me something about this i would really appreciate. :(

[http://bit.ly/9KSwT0](http://bit.ly/9KSwT0)

[http://bit.ly/cgspQ9](http://bit.ly/cgspQ9)

Thanks in advance.

---

### Post by BkkBonanza on 2010-08-28
Wow, that's a lot of connections, if it's all at once.
It would appear to indicate network scanning since so many ips appear consecutive.

I would run **sudo netstat -ntp** to see what connections are active and what process is doing it. If it appears to be something you're not intending, ie. some weird process, then I'd kill that process, and then try to figure out how that came about.

---

### Post by hiko2 on 2010-08-28
Thank for the response. The connections went back to normal once I did a reboot to the router and until now has stayed normal. The netstat shows the applications i have running. I posted this because of the curiosity it gave to huge amounts of connectios. 

Also, i dual boot, and i first noticed the lag while playing online games in windows 7 and then booted into linux and run the etherape, so i dont think is some native application of mine. It's possible it has something to do with my ISP? Or someone leeching my internet?:(

---

### Post by ex_isp on 2010-08-28
Is this on a wireless router?  I'm assuming so if you feel you have a leech in your presence...  If so, better safe than sorry.  Do reset on router, give stuffer key with best encrypt model your router will support.

---

### Post by hiko2 on 2010-08-28
> **ex_isp said:**
> Is this on a wireless router?  I'm assuming so if you feel you have a leech in your presence...  If so, better safe than sorry.  Do reset on router, give stuffer key with best encrypt model your router will support.

Yes is a wireless router. It's encrypted using WEP and has the option for a WAP but i cant change it because i dont have password for the administration page of the router. Guess I should call my ISP and ask for it. I am assuming a leech 'cause that's the most common thing that comes to my mind, but it could be something else.

---

### Post by BkkBonanza on 2010-08-28
The password may still be the default password. Google your make/model# and "default password". There's websites with lists of them. You'll likely find out what it is and can login.

WEP is useless nowadays as far as keeping others out. So it is a good idea to change to WPA or WPA2.

---

### Post by fyrmedic on 2010-08-29
Are you running any torrents when you opened Etherape. The first time that I looked at the ape and had a torrent file running I FREAKED!!!! 

An app like that may be running that opens a lot of connections to other IP's.

Good luck,

---

### Post by hiko2 on 2010-08-29
> **fyrmedic said:**
> Are you running any torrents when you opened Etherape. The first time that I looked at the ape and had a torrent file running I FREAKED!!!! 

An app like that may be running that opens a lot of connections to other IP's.

Good luck,

No, there wasn't any app running. Later I found out that maybe it was the online game i was playing but it's weird 'cause it doesn't supposed to have that many connections and that they stick after I reboot the PC right?

---

