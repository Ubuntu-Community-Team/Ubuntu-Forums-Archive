---
title: "Network Routing Question"
date: 2010-01-24
forum: Networking &amp; Wireless
---

### Post by Belizeian on 2010-01-24
I live in Belize and my particular ISP blocks all forms of VOIP, which is kind of lame.  Anyway I setup a ssh tunnel and route traffic from skype, msn and what no through it so the blocking isn't an issue.

The ISP also does DNS hijacking which also sucks.


What my issue is when I use apt-get update it chokes on the skype ppt because of the DNS hijacking. 

What I would like to do is route all traffic to skype through my existing tunnel without haveing to route everything through there.  

Is this possible?  If so how?

The following is what I use to setup tunnel
sudo ssh -x -2 -D 1000 username@server

---

