---
title: "Library sharing through Banshee"
date: 2008-09-08
forum: Multimedia Software
---

### Post by snkngshps on 2008-09-08
I have two Ubuntu laptops on a local network running Banshee but for some reason we're not able to browse each others music. I checked and both of the plugins for DAAP sharing are enabled. We have even been able to browse each others files through OpenSSH so I don't think connection is the problem. Any ideas?

---

### Post by ukblacknight on 2008-11-08
I've got the same issue.  The only time banshee has shown a share whilst on the network I'm on, has been when my mate has been using Limewire, it shows up as a music share.  He just started using Ubuntu yesterday and we can't see each others Banshee library's, even though the plugins are enabled!

---

### Post by ukblacknight on 2008-11-15
I hate to bump threads, but this is annoying!

If I turn Rhythmbox (RB), my RB media shows up in Banshee, so Banshee is able to detect other DAAP shares, and it also shows up in my mates Banshee on the network too.  His RB shows up in my Banshee, however our Banshee libraries don't show up in RB.

Basically, it seems like Banshee is able to read DAAP shares, but it's not sharing it's own library.

---

### Post by commonlyUNIQU3 on 2008-12-05
Banshee hasn't had DAAP sharing since v1.0 - you can accomplish DAAP sharing with mt-daapd though if you still want to use Banshee instead of Rhythmbox.

Just do a: ```
sudo apt-get install mt-daapd
```

Then go configure it by browsing to [http://localhost:3689](http://localhost:3689) (the default password will be "mt-daapd" until you change it).

FYI: mt-daapd is now called Firefly media server: [http://www.fireflymediaserver.org/](http://www.fireflymediaserver.org/) 

Hope this helps...

---

