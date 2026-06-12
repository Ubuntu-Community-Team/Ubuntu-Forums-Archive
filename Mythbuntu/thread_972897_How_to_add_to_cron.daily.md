---
title: "How to add to cron.daily"
date: 2008-11-06
forum: Mythbuntu
---

### Post by moorsey on 2008-11-06
Hey guys, just started playing with Mythbuntu the other day, stuck an old analogue TV card in, picked up the channels, recorded a manual job I put in OK, brilliant!

Haven't been using Linux in general for that long, but am enjoying using and learning.  I have seen many posts saying "I just stuck it in cron.daily", but never an explanation as to how!

I am behind a proxy (here at work) and as I understand, Mythbuntu doesn't have any support for proxies, shame, because Ubuntu does!

So this page [http://www.mythtv.org/wiki/index.php/Proxy](http://www.mythtv.org/wiki/index.php/Proxy)
says I need to setup a cron job to manually update my TV listings, because of the proxy.  So I've made the script, but have no access to the cron.daily folder, I can't copy to it, create new files in there etc.  I have been messing with "su" but with no luck.

Maybe someone can point me in the right direction, must have missed something!

If and when this script runs, should it just update the program listings?  Do I need to do anything else first?  I guess it needs to be configured as to where I am etc!

Thanks very much, superb project!

---

### Post by amac777 on 2008-11-06
I have no idea about Mythbuntu or how to get the script working for your myth setup, but I can at least help you create the script in the cron.daily directory and make it exectuable.

You can use this command to create the script in that directory:

```
sudo nano /etc/cron.daily/mythtv-backend
```

Copy and paste (or edit) the script according to your needs. After you have saved the script, make it exectuable by the following command:

```
sudo chmod uga+x /etc/cron.daily/mythtv-backend
```

---

### Post by moorsey on 2008-11-06
thank you very much, worked a treat

I have other issues with Mythbuntu and proxies, but at least I can play with scripts to work round that

Thanks

---

