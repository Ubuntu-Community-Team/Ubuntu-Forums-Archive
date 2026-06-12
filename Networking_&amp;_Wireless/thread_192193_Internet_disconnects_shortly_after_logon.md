---
title: "Internet disconnects shortly after logon"
date: 2006-06-08
forum: Networking &amp; Wireless
---

### Post by SSB on 2006-06-08
Repost:

On the live CD my internet worked perfectly so I have no idea what could be causing this...

My internet disconnects about 15 seconds after i log on to the system. Meaning it is connected for the 15 seconds prior to that. I can do anything normally, then it just dies out.

I'm VERY new to Linux so I may be missing something.. I've checked my eth0 connection and it said I had a few error'd packets. None of the networking tools gave me any results (I tried to ping 192.168.1.1 and I got nothing)

Any ideas? Remember that I'm new so the more technical answers I will need some help with. A lot of different things from windows here :O

---

### Post by SSB on 2006-06-08
I should mention I'm using DHCP.

---

### Post by DougC on 2006-06-09
See if any of this looks familiar:

[http://www.ubuntuforums.org/showthread.php?t=191231](http://www.ubuntuforums.org/showthread.php?t=191231)

---

### Post by thejoeandchip on 2006-06-11
i also have the exact same issue.  i am running a netgear router and i have tried to ping it also. i have enabled my ethernet connection and told it to use dhcp, i really need help.  if anyone has found an answer to this problem then please inform me.

---

### Post by jvictor on 2006-06-11
Disable IPV6
Use a static IP
Use ur ISPs DNS server add in /etc/resolv.conf

If that doesnt solve the prob
post the output of the following commands 

less /etc/hosts
route -n
less /etc/resolv.conf

---

