---
title: "cant see website from LAN"
date: 2009-08-18
forum: Networking &amp; Wireless
---

### Post by revenant138 on 2009-08-18
Hey all,

Can't see my website from the computer it's running on, which is my desktop. Browsing to localhost, 127.0.0.1, and its network IP all cause it to hang forever trying to load. If I unplug the computer from the netowrk, the site comes up right away.

Any ideas? I think it might be a router or apache problem, but I cant imagine what. 

Oh also, the site works fine from the WAN. Just don't want to have to go to starbucks to update my own friggin' blog.

---

### Post by superprash2003 on 2009-08-19
are you able to ping 127.0.0.1 in your terminal?

---

### Post by Iowan on 2009-08-19
What is in */etc/hosts*?

---

### Post by revenant138 on 2009-08-20
Can ping 127.0.0.1, also can ping 192.168.1.1xx which is my private IP.

Etc/hosts:

127.0.0.1       localhost
127.0.1.1       <compname>

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by revenant138 on 2009-09-07
Hey all, 

I've tried a few more things - I added a virtualhost on port 8000 and setup the private port to 8000 on my router hoping it would figure it out. Didn't help. 

What's really strange is that I'm actually getting it to pull down the website name in the top of the window, then it just hangs forever. I think it can actually see the site it just won't go get the site. Any ideas?

If I go to an IP that the site definitely isnt running on, it will tell me right away there's an error.

---

### Post by revenant138 on 2009-09-07
Oh yeah another thing is that this all worked great before I upgraded to Comcast Business class and they swapped their modem with a SMC one.

---

