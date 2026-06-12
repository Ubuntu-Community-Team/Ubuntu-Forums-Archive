---
title: "Why would a perfect LiveCD connection fail after install?"
date: 2006-06-07
forum: Networking &amp; Wireless
---

### Post by jcc on 2006-06-07
That's a rather crushing experience, considering one of the major purposes of trying a LiveCD.

In my case, I can't try looking at DHCP config, etc. because according to Xubuntu I have no network card attached at all.  All I can get from /var/log/messages when ejecting/reinserting is "card ejected" and "unable to map card memory."

I've not had networking trouble on this setup with several diverse Linuxes over the years.  I'm ready and able to do some footwork to figure this out, but I don't have a clue where to begin.  Given that the LiveCD connected without intervention, this should be easy, shouldn't it?

This is a Linksys Etherfast PCMLM56 in an Inspiron 3800.  I'm running a fresh install of Xubuntu 6.06.

---

### Post by jcc on 2006-06-07
/proc/devices is empty.  "lsmod | grep pcmcia" gives me:

```
pcmcia        40508   0
pcmcia_core   42640   3 pcmcia,yenta_socket,rsrc_nonstatic
```

---

### Post by zxee on 2006-06-08
Hi, I don't suppose that I'll be much help, but that is a good question. I have my own internet problems with dapper ( on dial up ) but this network forum is filled with many, many ethernet, broadband problems and questions. I would recomend going on irc ( freenode, #ubuntu ) and asking the developers that hang out there. And for that matter why is there such a dramatic shift for the worst from breezy which recognized and set up most networking surberbly to this situation? I really like ubuntu so it's a shame.
Added: Don't if you've already seen this thread,
[http://www.ubuntuforums.org/showthread.php?t=189947](http://www.ubuntuforums.org/showthread.php?t=189947)

---

