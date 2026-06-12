---
title: "Wireless hangs trying to connect"
date: 2010-04-17
forum: Networking &amp; Wireless
---

### Post by fallenashes on 2010-04-17
My wireless has worked at my house, which is unprotected (yeah yeah don't need a lecture on that) but at my friends house which is WPA/WPA2 protected, he enters the correct password (it says it on his mac), and it spins like it is connecting for a while, but it never connects and keeps on asking for my password periodically.

What is the problem, I know my wireless cards are supported and all.

---

### Post by RedSingularity on 2010-04-17
I had the same problem once.  Are you choosing the correct security encryption?

---

### Post by fallenashes on 2010-04-18
Well, it only let me choose WPA, didn't have much choice did I?

Edit: and WPA 2, it was bundled into one choice.

---

### Post by mrosenfe on 2010-04-19
I have the exact same problem and left a post last Saturday but it has had zero reponses.   It appears that Ubuntu 9.x has a problem whenver its using wpa or wpa2.   I was using 8.x with the exact same hardware and it connected and worked fine.   Mine now only works with encryption turned off.   Not good.   It appears that there is something wrong in the wpa handshake.   It tries multiple times and then times out.  I tried every combination of encryptions supported by my router but only no authentication works.   

Like I said, I know its not a hardware problem as mine worked right up to the time I upgraded from 8.x to 9.x and then it failed.   I also did a clean re-install but nothing helped.   I see from others in the forum this appears to be a fairly repeatable problem.  I hope a solutions is forthcoming.

---

### Post by bkratz on 2010-04-19
> **mrosenfe said:**
> I have the exact same problem and left a post last Saturday but it has had zero reponses.   It appears that Ubuntu 9.x has a problem whenver its using wpa or wpa2.   I was using 8.x with the exact same hardware and it connected and worked fine.   Mine now only works with encryption turned off.   Not good.   It appears that there is something wrong in the wpa handshake.   It tries multiple times and then times out.  I tried every combination of encryptions supported by my router but only no authentication works.   

Like I said, I know its not a hardware problem as mine worked right up to the time I upgraded from 8.x to 9.x and then it failed.   I also did a clean re-install but nothing helped.   I see from others in the forum this appears to be a fairly repeatable problem.  I hope a solutions is forthcoming.

Well I use wpa2 in both 9.04 and 9.10, but I did have to change the router settings to aes rather than tkip/aes for it to work, and I never did get wep working! No loss there!

---

### Post by yrhen on 2010-04-19
using network manager? I solved it by switching to what's it called: WICD - oh damned memory

---

