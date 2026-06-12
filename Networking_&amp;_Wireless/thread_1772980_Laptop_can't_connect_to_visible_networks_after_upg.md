---
title: "Laptop can't connect to visible networks after upgrading from 10.10 to 11.04,5100 AGN"
date: 2011-06-01
forum: Networking &amp; Wireless
---

### Post by bluplr on 2011-06-01
After upgrading from 10.10 to 11.04 and running an update ubuntu can't connect to any wifi networks, although it can see them perfectly (and potentially unrelated, the windows partition is having major dns issues with the wifi too).

I've looked around and can't find an obvious fix, just a bunch of posts from people with the same problem that wasn't solved. I got frustrated and was about to install 10.10 again but I noticed I couldn't connect to the wifi on the liveCD either. I then tried the 10.04 liveCD, and the internet worked aswell as when I installed it. However before when I upgraded from 10.04 to 10.10 I had no problems with the wifi, so it leads me to suspect that there was something installed/some setting in 10.04 that is missing from the latter version.

I've attached the outputs from the wireless device script I found on these forums. I've attached the outputs for 10.04 (the one that worked) and 11.04. Hopefully someone here can help me spot the difference to find out why it's not working. Thanks!

---

### Post by ivanovnegro on 2011-06-01
I have experienced this problem with the 10.10 edition and now on the new one.
It shows the Wireless but it refuses to connect, was in the terminal also to see if something was blocked but everything was alright and the driver is an open Intel one.
First thing I had to do to get it working was to type many times my password for the wireless then it worked, on a second occasion I had to delete my network and to set it up again, then it worked and yesterday I had the weirdest option to go. I installed 11.04 on another machine and had the same problem could never get the wireless to work but it showed up, I was so frustrated and then I tried this, I disabled the Wireless on my laptop with the button it has for and then enabled it again and voilà, it worked, I could connect normally. This is somehow a weird thing since the 10.10 release for me.

---

### Post by bluplr on 2011-06-01
That's a lucky find, but it doesn't seem to work for me. What laptop do you have?

---

### Post by ivanovnegro on 2011-06-02
I have an HP Compaq 6730s.

---

