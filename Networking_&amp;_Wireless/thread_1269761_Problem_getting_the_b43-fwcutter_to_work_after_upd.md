---
title: "Problem getting the b43-fwcutter to work after update"
date: 2009-09-18
forum: Networking &amp; Wireless
---

### Post by Fenrisulfr on 2009-09-18
When I first reinstalled Ubuntu 9.04, I installed b43-fwcutter and let it fetch its firmware and it worked just fine, I could access networks and whatnot, but after a somewhat recent update, nothing seems to work anymore with the WLAN, I can't detect any of the wireless routers, and when I disable and reenable wireless networking (in the the network manager in the top right corner) the wireless will say "device not ready"

I'm using NDISwrapper, it works, but at a reduced reception (as in NDISwrapper drivers get 60%-70% where as the other gets 80-90%)

Am I doomed to keep using NDISwrapper, or did something like an update break the fwcutter?

Is there SOME way to fix this?

If you need any additional info, tell me how to get it and I'll try to get it.

---

### Post by FearfulJesuit on 2009-10-19
Fenrisulfr,
I don't know if this will help after a month. You probably already solved it. But mine mysteriously stopped working as well recently. The strange thing was that the driver was somehow disabled. 

Did you try going to 'System' -> 'Admin..' -> 'Hardware Drivers'? Check if it's enabled there. If it is, try removing it from there. Restart your computer and re-install it. Then re-enable it from the 'System' menu again. 

-- Apuervo

---

### Post by motang on 2009-10-20
Mine doesn't work. I tried reinstalling it many times. :'(

It used to work, but after an update no more.

Took off WEP authentication on my router end and it works now...go figure. Need to see if WPA will yield the same result.

---

