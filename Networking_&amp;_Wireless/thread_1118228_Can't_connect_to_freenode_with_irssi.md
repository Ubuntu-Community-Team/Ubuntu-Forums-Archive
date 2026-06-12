---
title: "Can't connect to freenode with irssi"
date: 2009-04-06
forum: Networking &amp; Wireless
---

### Post by Devour on 2009-04-06
I'm having the exact same problem as this guy, [http://ubuntuforums.org/showthread.php?t=584494](http://ubuntuforums.org/showthread.php?t=584494)

I can connect to Freenode using XChat but when I try and connect using irssi I'm getting the same error as that guy in the other topic. Can anyone shine some light as to why this is happening? It doesn't make any sense that I can connect using XChat but not irssi.

---

### Post by Devour on 2009-04-08
I actually got this fixed. It seems I had the hostname set incorrectly. To fix this just type /set -clear hostname and then try connecting to the server again. Problem solved. :)

---

### Post by adcwoef on 2010-08-14
I have the same problem. However, your solution does no fix the problem for me.

Edit.
Guys on IRC found the problem: irssi was trying to use IPv6 apparently.

---

