---
title: "ICS Windows Mobile"
date: 2009-06-04
forum: Networking &amp; Wireless
---

### Post by markvdm on 2009-06-04
Hi Guys
 
I'm having a weird problem with ICS in Ubuntu 9.04. I know there are tons of threads around this issue, but I seem to be having a slightly different problem, so please bear with me.
 
I've tried all the fixes in the different threads, but so far everything has the same result.
 
If I boot straight from the LiveCD, activate ICS on my mobile and connect via USB, I get eth1 activated and get all the correct settings. I can browse [www.google.com]("http://www.google.com") and [www.news24.com]("http://www.news24.com") I can do searches on Google so I don't think it's just a cache on my mobile. I can't browse most other sites, Firefox stays at "waiting for reply" and only after quite a few minutes does it time out with a "Connection to server was reset" Even when installing and making all the changes in the various threads here, I get exactly the same result.
 
I'm dual booting between Vista and 9.04, with 9.04 installed inside Vista on the same NTFS partition. I'm running a HP Compaq nx7400 with a Centrino Duo 1.8GHz and 1.5GB RAM. Mobile is a Sony Ericsson X1i runnings WM6.1
 
Any ideas guys? I'll post any additional information required.

---

### Post by markvdm on 2009-06-04
No ideas guys?

---

### Post by markvdm on 2009-06-05
Ok, last bump for any random ideas?? I'm pretty desperate for anything right now. :(

---

### Post by markvdm on 2009-06-08
Ok, so I had a suggestion from a friend. I changed my MTU from automatic to 1400, still nothing, went down a little further, and all of a sudden everything works great. Ended up with it on 1394 now. Even 1 higher, and I cannot browse most sites. Any ideas why it should be so low?

---

### Post by Iowan on 2009-06-08
I'm not familiar with your setup (especially the Sony Ericsson X1i), so can't offer much advice... but didn't want you to be the only one posting in your thread. :-|
I'd have thought at least ONE of the threads would have mentioned MTU, but (again) dunno what the mobile is capable of using.

---

### Post by markvdm on 2009-06-09
From what I read most of the threads suggested checking the MTU in Windows and using the same value in Ubuntu. I had tried that but still no luck. My friend then suggested dropping the value to 1300, and moving up from there.

And yeah, I noticed I was the only one here... lol... but I figured I may as well post my findings and solution as someone searching the forums may be having the same problem.

---

