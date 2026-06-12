---
title: "Disable 'internet' connection on eth0"
date: 2010-10-15
forum: Networking &amp; Wireless
---

### Post by fepple on 2010-10-15
Hello,

I have two connections for my PC, my Ethernet which is on the corporate network and my smart phone on 'usb0'.  Both have full internet access.

I want to stop my PC from connecting to the internet over the Eth0 while still connecting to internal servers then just have internet over usb0.

If I go to the settings of 'Auth Ethernet' in the tray area, under IPv4 there is the routings section - I've tried enabling "use this connection only for resources on its network" but it doesnt work.

Any ideas?

Cheers!

---

### Post by neomod on 2010-10-15
What about removing/changing DNS for eth0 connection? you might leave only those you use for your internal network ( if needed... ).
[ just a stupid idea, maybe...]

---

### Post by SeijiSensei on 2010-10-15
Maybe this will help: [http://ubuntuforums.org/showpost.php?p=9976398&postcount=6](http://ubuntuforums.org/showpost.php?p=9976398&postcount=6)

---

### Post by fepple on 2010-10-17
> **neomod said:**
> What about removing/changing DNS for eth0 connection? you might leave only those you use for your internal network ( if needed... ).
[ just a stupid idea, maybe...]

I did think about that - main reason i think it wouldnt work for me is I need the internal DNS servers that also (i think) do external DNS resolves

> **SeijiSensei said:**
> Maybe this will help: [http://ubuntuforums.org/showpost.php?p=9976398&postcount=6](http://ubuntuforums.org/showpost.php?p=9976398&postcount=6)

That looks ideal - will give it a bash tomorrow!

---

