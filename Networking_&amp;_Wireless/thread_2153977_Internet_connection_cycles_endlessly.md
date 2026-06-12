---
title: "Internet connection cycles endlessly"
date: 2013-06-13
forum: Networking &amp; Wireless
---

### Post by AGNKim on 2013-06-13
After being away from Ubuntu for a year or so, I returned last night. I upgraded to 12.04 from 10.04. Now, my internet connection just cycles constantly, as if it continuously tries to connect wired, then wireless, then wired, then wireless... I am online (via a wired connection), but sometimes I will lose connection momentarily during one of the "cycles". The wireless symbol (the upward pulsating arcs) will flicker as if it is trying to connect wirelessly, then settle on the two arrows, which I assume to be a wired connection.

I'm sure I'm not giving all pertinent information, but sure would appreciate some assistance.

Thank you!

---

### Post by newbie-user on 2013-06-13
Check the easy stuff first. Make sure your network cable is properly seated in the socket, and make sure it's not cut somewhere along the way. Swap cables, if possible, to verify if the cable is still good.

Next, check your DHCP server to see that there are no IP address conflicts on your network. Also check your /etc/network/interfaces file if you set up a static IP for your computer. Of course, also verify that your router/switches are all functioning correctly.

After that, try using a different network card. There are so many things that can contribute to the problem...

---

### Post by AGNKim on 2013-06-13
Just in case anyone else has this problem.

I had two wired connections on my PC. When checking my settings, both had "Connect automatically" checked. i unchecked the one that is not used, and Ubuntu quit cycling and stayed with one.

---

