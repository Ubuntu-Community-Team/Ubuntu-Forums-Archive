---
title: "Internet not working with WICD network manager"
date: 2009-07-19
forum: Networking &amp; Wireless
---

### Post by getknk on 2009-07-19
Hello friends,
Sorry if this was posted before, but I couldn't see any with the search.
I installed 1.5.9version Wicd in my 9.04 jaunty.
Afterwards, i'm not able to connect to Internet via wired/wireless connection :(
I can login to my Router and all internet settings are working as my windows laptop is connected to the same router.

I'll try to put maximum details by typing it here..
thanks in advance

---

### Post by getknk on 2009-07-19
Details

1. As mentioned in WICD help page
made sure that the only entry in your /etc/network/interfaces file is 
auto lo
iface lo inet loopback

2. I can see WICD connected correctly and saying the status as connected

3. ifconfig -> shows eth0, lo, wlan0, wmaster0 . I tried connecting eth0 as its my wired connection

4. In Firefox its showing "Though the site seems valid, the Browser was unable to establish a connection" and its regular solution

5. I tried starting WICD, firefox in root user but still not connecting

6. No Static IP's used , and no Static DNS

Please let me know if more details are required. thanks again

---

