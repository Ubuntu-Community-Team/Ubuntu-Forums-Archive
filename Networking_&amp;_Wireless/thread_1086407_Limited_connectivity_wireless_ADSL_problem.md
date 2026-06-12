---
title: "Limited connectivity wireless ADSL problem"
date: 2009-03-04
forum: Networking &amp; Wireless
---

### Post by KevNice on 2009-03-04
I had posted a similar thread about this, but due to strange wireless issues, I have re-installed Ubuntu and am now using Hardy 8.04 again.

Basically, my problem can be summed up on this thread, as the poster has basically the exact same problem as me:
[http://ubuntuforums.org/showthread.php?t=759815&highlight=connecting+wireless+limited+connectivity](http://ubuntuforums.org/showthread.php?t=759815&highlight=connecting+wireless+limited+connectivity)

In short, I am trying to connect to a limited connectivity wireless network, and then have to use PPPOE ADSL to get online. This works in Vista.

I followed the solution in the above thread. I used eth0 and not eth1, and the network name is CHTN_T07AW

I put the following into terminal:
```
sudo iwconfig eth0 essid CHTN_T07Aw
```

And it told me that it was an invalid argument.

Any solution? Perhaps it is an encrypted network and I need more information? It would make sense if it were encrypted, it is the network my workplace uses. If so, please tell me how to gather the information that I would need.

Thanks

---

### Post by N04h on 2009-03-04
I'll check the invalid argument when I get home, but your network wouldn't happen to be encrypted by chance?  If so that command won't work for ya!

---

### Post by KevNice on 2009-03-05
It probably is encrypted, as it's the network at my office. Is there a way to do it on an encrypted network, using a different command?

---

### Post by N04h on 2009-03-05
Same command, but you need to specify a key.  Do a google search and it should turn up what you're looking for.

---

### Post by KevNice on 2009-03-06
thanks but I am not quite sure what "key" I am searching for, or what it is supposed to do. What should I search for?

---

### Post by KevNice on 2009-03-06
Actually, after thinking on it, I am not sure it is encrypted. Under Windows, there is no password required for connecting to the wireless

---

### Post by KevNice on 2009-03-12
bump 

any ideas?

it would be great if I could Ubuntu at work, since that's where my Chinese/Japanese inputs are, and I need them for the occasional document

---

