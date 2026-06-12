---
title: "nm-tool doesn't want to connect to found wireless network"
date: 2011-07-07
forum: Networking &amp; Wireless
---

### Post by jediayaddle on 2011-07-07
First, I will apologize if this issue is somewhere else, but I can't find it...

Just got a netbook and installed Ubuntu 11.04, and it doesn't connect to my wireless at home, but it connects to every other wireless network I've used. It picks up my home network, it just doesn't want to connect (it tries for ages, then times out asking for the WEP pass-phrase again). If I switch over to my windows partition, it connects just fine. I was fiddling around with my laptop to try and get the connection settings (it's running an older version of Ubuntu, i think 8 or 9), and I gave it a bogus password to see how long it took to realise, then when I switched it back it no longer works! My tower has Ubuntu 10.04 and it still connects (although I'm afraid to change anything incase it stops connecting). I'm guessing it has somethign to do with the router or the network itself, and not the drivers or anything (I've done all the appropriate driver installations and such for my Samsung NF210 which I've read). Any ideas on what I need to change (I'm guessing it is the nm-tool)? I've also tried resetting the router.

Let me know if you need any system information. I know the network card is connected and all set up (so I didn't include lspci, that all appears to check out), it's just this particular network...

Thanks!

---

### Post by jediayaddle on 2011-07-13
An update:

I decided to run nm-tool while attempting to connect to the described network. When the connecting process stalls, nm-tool says it was trying to configure the IP.

---

