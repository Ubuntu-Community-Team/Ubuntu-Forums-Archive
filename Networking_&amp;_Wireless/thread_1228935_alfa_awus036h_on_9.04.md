---
title: "alfa awus036h on 9.04"
date: 2009-08-01
forum: Networking &amp; Wireless
---

### Post by vze57gc8 on 2009-08-01
alfa awus036h shows very low signal in ubuntu 9.04 (14%). the patched aircrack driver doesnt work (the card is undetected under this driver). has any1 been experiencing such problems?

---

### Post by Rog3236 on 2009-08-13
Yes. I am using it on a Dell notebook and am experiencing the same low signal. My router is less than 10 feet from the adapter so I can't understand what's going on. My Trendnet adapter shows max signal when I use it.

Notice your post was last week with no replies so guess no one appears to have a clue as to how to correct the problem.

---

### Post by alfal on 2009-08-14
Install Wicd

and

 	Code:
 	sudo apt-get install linux-backports-modules-jaunty

---

### Post by nuchdog on 2010-03-17
For me the problem in ubntu 9.10 is that the new rtl drivers and the old legacy drivers were both loading. I blacklisted one. In general, try this tutorial to switch between the two and see which works for you.

[http://forum.aircrack-ng.org/index.php?topic=5755.0](http://forum.aircrack-ng.org/index.php?topic=5755.0)

---

