---
title: "Please disable the Wireless KILL switch"
date: 2008-12-12
forum: Networking &amp; Wireless
---

### Post by FountainDew on 2008-12-12
Hi, I own an Acer Aspire One with a Wireless Kill Switch. Actually in Linpus Lite it will turn the wireless On/Off, but in Unbuntu it will only turn it Off, and permanently stay off. I know because I've reinstalled the OS 3 times thinking my problem was madwifi (which works great with Atheros actually).

So since Wireless is DO or DIE for netbooks, this is a very serious issue. The switch can be easily moved from a slip, bump or sheer curiousity. Is there a way to Disable it? Or even better, is there a way to make it _WORK LIKE IT SHOULD_?

---

### Post by cometa2k7 on 2009-01-07
I have this problem with my Acer 5920.

The solution I used is here [http://ubuntuforums.org/showthread.php?t=980603]("http://ubuntuforums.org/showthread.php?t=980603")

Please not that it is necessary to hit the wireless switch again before running that code, as otherwise, the wireless is still off, and will not come back.

You can, if you want, put ```
sudo ifconfig wlan0 up
``` into a launcher, but you will need to set it to run in terminal (this just brings up a terminal which will go away again as soon as you enter the password). If you don't run it in terminal, it can't get your sudo password, and so can't run.

---

