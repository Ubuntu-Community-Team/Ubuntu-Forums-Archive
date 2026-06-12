---
title: "Network manager won't connect to WEP in 9.04"
date: 2009-09-15
forum: Networking &amp; Wireless
---

### Post by Murdoc_of_puts on 2009-09-15
Hello,
This is kind of a new problem for me.  Network manager won't establish a wireless connection to my wireless modem.  The modem is protected by a wep key (40/128) wep index 1 /shared key.  My room mate can connect with her windows laptop to the same network-using the same key.  So...it's not the key being incorrect.  I don't really know what to do here.  I recently tried to try out the aircrack-ng suite to see how secure our modem was.  I used [this guide]("http://ubuntuforums.org/showthread.php?p=6934824#post6934824")to try to get it working.  Which I suppose packet injection doesn't work on 9.04.  Sorry for the ramble, just trying to get the details out of the way.  So here's the short Questions.

> 1.Would patching drivers for packet injection have a negative effect on Network Manager so that it wouldn't be able to connect to a wirelesss network?
> 2. Is there something else that could be wrong with network manager that it would not accept a wep key?

Note: I can connect to non-encrypted networks with no problems, also I can connect via a eth0 connection no problems.
Wireless card=Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
Thanks for any help, and sorry this was a little long winded.

---

### Post by webdevelopment on 2009-09-16
having a similar problem

works fine in windows xp and vista but not on my ubuntu 9.04

i also don't know how to select "plain old normal" WEP from ubuntu...

---

### Post by Murdoc_of_puts on 2009-09-30
Alright, so I installed 8.10 on another partition. It worked.  So....I think I'm going to look at how to make a patch.....or just wit for koala to come out and hopefully it will be magically fixed.  I think option A is more likely.

---

