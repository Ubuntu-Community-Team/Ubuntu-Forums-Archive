---
title: "use ubuntu machine as wireless router"
date: 2011-06-10
forum: Networking &amp; Wireless
---

### Post by rsn13 on 2011-06-10
i did googled for that for a while now, but didn't found anything relevant so far, or did i missed something?
i need to share a pppoe connection, using an infrastructure wifi network, how can i do that in ubuntu?

forgot to mention, ad-hoc just won't do it for me, the other devices, either dosen't support it, either get a password error.

also, i would need some help for establishing the pppoe, i previously did that on another machine, but that was long ago, and it was a big head ache, it would only dial on startup, and no redial or disconnect posibilities whatsoever.

any help will be much apreciated, sorry for my bad spelling, and tnx in advice :D

---

### Post by rsn13 on 2011-06-10
well, i did came across this [http://johnlewis.ie/ubuntu-as-a-wireless-80211n-access-point-router/](http://johnlewis.ie/ubuntu-as-a-wireless-80211n-access-point-router/) but i'm not qite sure what ip's go into that config file, can someone tell me what should these be? are they just the ones that the "virual router" will use? or are the reffering to the actual internet connection?

---

### Post by jpl888 on 2011-06-11
The first IP is the IP address you want Ubuntu machine come wireless router to have.

You may not have to specify the network and netmask, I expect Ubuntu/kernel will come up with sane values on it's own.

The gateway is the LAN side address of your internet router.

Do you understand?

---

