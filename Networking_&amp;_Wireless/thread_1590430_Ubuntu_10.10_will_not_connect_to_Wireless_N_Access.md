---
title: "Ubuntu 10.10 will not connect to Wireless N Access Points"
date: 2010-10-07
forum: Networking &amp; Wireless
---

### Post by apastuszak on 2010-10-07
I have wireless G and N access points in my house.  The N network is set to allow only N connections.  I have a Lenovo laptop with a Intel Wireless N chip in it, and after one of the 10.10 updates it stopped connecting to my N access point.  The G access point works just fine.

The logs for the Wireless N access point alway show "Bas Password."   I am having the same problem with either NetworkManager or wicd.

Anyone alse seen this or know of something that will get me back on the wireless N access point?

Andy

---

### Post by ironjaw33 on 2010-10-11
I'm having this problem too.  I've set my router to N only and I can't connect.

---

### Post by Mobidoy on 2010-10-11
Look at [this post]("http://ubuntuforums.org/showthread.php?t=1592846")

---

### Post by awm086 on 2012-12-04
I feel like I may be having a similar problem on Ubuntu 12.10. At home I can connect to the wireless with no problem. At work, I cannot connect to the access point with highest signal, which I find using nm-tool:
```
Infra, 00:24:6C:80:D7:40, Freq 2462 MHz, Rate 54 Mb/s, Strength 64
```

 I know that, because when I boot in Mac OS x, it connects just fine. I tried specifying the MAC address of the access point, but network manager refuses to connect to it. Here is the sys [log ]("http://pastebin.com/e5324Z0m"). 
My card is ```
Broadcom Corporation BCM4331 802.11a/b/g/n
```

Can anyone help?

---

### Post by wildmanne39 on 2012-12-05
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

