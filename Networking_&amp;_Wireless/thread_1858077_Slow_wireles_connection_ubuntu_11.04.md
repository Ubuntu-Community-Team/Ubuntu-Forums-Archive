---
title: "Slow wireles connection ubuntu 11.04"
date: 2011-10-11
forum: Networking &amp; Wireless
---

### Post by fizdup on 2011-10-11
I recently installed Ubuntu 11.04 on a 4 year old ASUS laptop.
I am having problems with my wireless connection.

It finds the network, and connects to it with no problem. But the speed fluctuates a lot. Going from as good as wired through ethernet right down to pages timing out or not being able to connect at all.

Anyone got any ideas?

---

### Post by Serujisu on 2011-10-11
Out of curiosity, does it have the same issue when you have the laptop plugged into an outlet? I just posted a similar issue I'm having with an ASUS netbook.

If it /is/ a similar issue, try typing ```
ping -c 20 google.com
``` into the terminal. It should give you an idea as to what sort of packet loss you're getting. In my case it's pretty big.

---

### Post by fizdup on 2011-10-19
I have now plugged it in to the power and it is working, but I have also just turned it on, we shall see how that goes.

I pinged google, like you suggested and got 0% packet loss, so that's nice.

If the trouble returns, I shall also return...

---

