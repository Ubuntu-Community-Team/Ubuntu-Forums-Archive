---
title: "Firefox not loading some pages"
date: 2010-09-16
forum: Networking &amp; Wireless
---

### Post by silverstorm on 2010-09-16
Hello!

I have a problem! 
I am Using Ubuntu 10.04 fresh install connected to internet via VPN Network.
Internet works fine i can dowload mail and send. But for some reason i cant load some webpages like Facebook, Adobe and etc.
I install all the newest programs Java, Flash anything.
I'm runnung Firefox 3.6.9.
I tried everything disabled IPV6, Proxy. But nothing solved it.
Any Help?

---

### Post by dineshs on 2010-09-16
Run this ```
gksudo nautilus /etc/NetworkManager/system-connections
```
Do you see a file created by NM for your VPN connection?If yes open it and set ```
mtu=1492
```or 1452.Then close and save the file
You may go through [this]("http://ubuntuforums.org/showthread.php?t=872346") before setting an MTU.
> An easy way to figure out what your MTU should be is to use ping where you specify the payload size:
```
ping -s 1464 -c1 google.com
```

---

### Post by silverstorm on 2010-09-16
THX for your post.
But it did not solved it.
And i cannot ping to google, and acces to main server.
Facebook shows up but no pictures and it takes too long.
I had no problems 3weaks ago.
Maybe something was updated?

---

### Post by dineshs on 2010-09-17
what does```
sudo lshw -C network
```output

---

### Post by silverstorm on 2010-09-17
Something is wrong sudo lshw -C network did not show anything.
it seems like he is working but then nothing output.
What this meens?
I tried this at work there was everything fine.
Don't know what to do.
I have dual boot. Under windows everything works.

---

### Post by silverstorm on 2010-09-18
Any Help? Anyone?

---

