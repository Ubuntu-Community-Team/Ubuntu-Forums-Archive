---
title: "How to disconnect?"
date: 2006-06-24
forum: Networking &amp; Wireless
---

### Post by sooqing on 2006-06-24
I am using PPP for my Internet usage. When I wanted to disconnect, I used:

'sudo ifconfig ppp0 down'

However, it seems to me that this just 'blocks' my connection since I can just execute:

'sudo ifconfig ppp0 up'

and my connection is back with the *SAME* IP. One interesting thing is I cannot access the Internet (ping, ftp, http) after doing this. What happened and how do I get a change of IP then a la Microsoft Windows style? Any way to 'really disconnect' my connection?

---

### Post by adwait on 2006-06-25
umm..how about
```
sudo poff
```

---

### Post by kimera99 on 2007-02-02
Really thanks a lot!
you saved my life!!!!
I needed this command to make kget autodisconnect after finishing the download!:lolflag:

---

