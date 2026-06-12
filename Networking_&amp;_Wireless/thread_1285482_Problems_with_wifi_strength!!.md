---
title: "Problems with wifi strength!!"
date: 2009-10-07
forum: Networking &amp; Wireless
---

### Post by Predtech on 2009-10-07
Hi guys, i have a VERY strange problem that i need help with.
Currently i have a Dell Inspiron 1545 with an Atheros 9281 internal wifi card that i replaced the original crappy Broadcom card with.
The problem is this, i boot Karmic Koala beta but was using jaunty before and also had this problem. I am running Windows alongside Ubuntu.
When i am using wireless with ubuntu i only get 75%-95% when sitting DIRECTLY beside my Linksys WRT110 router, and needless to say when i move away from the router it drops DRAMATICALLY even at about 30ft away in my living room. I basically can't get even bare bones connection at 35%-40%, even google has a hard time coming on the screen.
The STRANGE thing is that when i boot into Windows on the very same laptop i can get 100% connectivity and speed throughout most of the house. If i don't get 5 bars on my wireless connection it only drops to 4 bars and that's at the farthest point from the router in my house.

Can anybody tell me why i have such much trouble with wireless in Ubuntu and not in Windows.
If it helps any, my Ubuntu installation is using the ath9k driver and in the network manager it says the speed is unknown.

I'm writing this from my windows installation because i can't even get to these forums with ubuntu at this small distance.

Any help is greatly appreciated.

---

### Post by Predtech on 2009-10-08
bump?

---

### Post by mclavey on 2009-10-08
I have a HP dv7 laptop and have a similar problem.  It has been getting worse with each update to the system.  I hope someone can help us.

I found the answer that worked for me.

sudo apt-get install linux-backports-modules-jaunty

I hope it will work for you

I am not sure if this will be overwritten by the next update of the Update Manager. 

I hope someone else will answer this question.

---

### Post by Predtech on 2009-10-09
Seriously, no help at all??????????

---

