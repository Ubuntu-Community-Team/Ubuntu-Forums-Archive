---
title: "Atheros 5007 wireless fix broke graphics card"
date: 2009-01-28
forum: Networking &amp; Wireless
---

### Post by Ketara on 2009-01-28
I upgraded from Hardy to Intrepid last weekend, and had my Atheros card running in Hardy using the madwifi fix.

The same fix did not work in Intrepid, so after some searching I found the backports solution. Installed backports modules via synaptic. This not only did not fix the wireless, it broke my nVidia driver, and Ubuntu will now only boot in "low graphics mode"

So I removed the backports modules, and that fixed the nVidia driver.

Decided to mess with it again today, and did what was described in the following two threads - 
[http://ubuntuforums.org/showthread.php?t=1052636](http://ubuntuforums.org/showthread.php?t=1052636)
[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

I have some output on the former thread of the errors I got trying to install the backports stuff through terminal.

Having done that, now the wireless still does not work, the nVidia driver does not work, and removing the backports module via synaptic did not fix the nVidia driver.

I am going out of town on Friday and will need to use my laptop wirelessly, and am wondering if there is a better solution here than just going back to Hardy.

Thanks.

---

### Post by Ketara on 2009-01-28
I really could use some help with this. I'll have to reinstall Hardy tonight probably if I can't find a better option.

---

