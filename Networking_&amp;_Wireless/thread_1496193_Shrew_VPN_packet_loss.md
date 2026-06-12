---
title: "Shrew VPN packet loss"
date: 2010-05-29
forum: Networking &amp; Wireless
---

### Post by smurfs_of_war on 2010-05-29
I am just starting my adventure into Ubuntu. After installing and configuring Shrew Soft in Ubuntu 10.04 64Bit, I am having some serious packet loss issues. The LAN is wireless, however the only packet loss I experience is over the tunnels. I have tried different algorithms, and it seems as I fiddle with the MTU client side, it clears a bit, but the best I have managed is 23% loss average. Any one else have this issue? I am wondering if it is a WLAN issue at this point, so I am looking for similar experiences.

---

### Post by unterfuhrer on 2010-06-07
I have the exact same problem and are not able to find any solution.

---

### Post by ghbarratt on 2011-04-21
I too am having the exact same problem or at least it seems the same. 

When the VPN tunnel is enabled Some symptoms I am seeing are:
- Firefox often pulls up the "Server not found" page upon first load attempt but loads the page if I refresh
- When and if a page loads, most elements on a web page will load up but almost always, some will not. On subsequent reloads, different elements will be the "unloaded" ones.
- Often I can't open email messages (in Evolution)

All these symptoms clear the second I turn off Shrew Soft VPN.

I tried building Shrew VPN deamon and client from the source and although I was able to do this and upgrade from the Software Center ("repo" ) version of 2.1.5 to the latest available version 2.1.7, my problems have remained the same.

Also, I previously was using Ubuntu 10.10 32bit but switched to 10.10 64bit since I knew that my system supported 64bit. I don't know why I was using the 32bit version earlier, BUT the thing is that Shrew Soft VPN was working way better in 32bit than in 64bit. Nothing else was changed on the machine. I am tempted to switch my OS back to 32bit just to have the Shrew Soft VPN cooperate. I need it for work.

---

