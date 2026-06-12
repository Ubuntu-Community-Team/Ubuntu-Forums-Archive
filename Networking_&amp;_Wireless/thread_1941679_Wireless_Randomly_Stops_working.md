---
title: "Wireless Randomly Stops working"
date: 2012-03-16
forum: Networking &amp; Wireless
---

### Post by davedaverson on 2012-03-16
I cannot figure out why the wireless just randomly stops working.
I have no clue where to even begin troubleshooting. I've been using Kubuntu for the last month and have finally gotten things up and running, so of course out of the blue this random problem popped up...completely at random and now is the bane of my existence.

I can see all of my network connections, when I click on them I get no response. I've tried "sudo /etc/init.d/networking restart" and I get " * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...  "

I rebooted before to resolve the issue but now it's back. Its so RANDOM.

I searched high and low, and I can find thousands of different instances. Almost all of which are on other versions of Kubuntu. I can't find anything on this, please help.

---

### Post by Zorael on 2012-03-17
Could you run this in a terminal and paste the output here? (inbetween ```
 tags for legibility)
[code]$ lshw -c network
```
You may need to install the **[lshw](apt://lshw)** package, but I think it's there by default.

Also, please provide the output of **dmesg**. Save it to a file and attach it here.
```
$ dmesg > ~/dmesg.log   *# saves it to dmesg.log in your home directory*
```
Naturally this last log is only of interest if your wireless has died at least once during the current boot, so give it a good provoking.

---

