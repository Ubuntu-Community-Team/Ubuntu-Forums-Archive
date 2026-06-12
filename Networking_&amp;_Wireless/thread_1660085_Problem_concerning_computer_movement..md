---
title: "Problem concerning computer movement."
date: 2011-01-04
forum: Networking &amp; Wireless
---

### Post by sansa90 on 2011-01-04
I have a Linux machine that I just inherited, and it used to be hooked up to the ethernet in my basement. I have a wireless connector that works just fine, and I'm using the same model on a different computer. The problem is that Linux won't connect to the internet using wireless. It used to be the computer with the ethernet plugged in, and it says it is the localhost (IP says 127.0.0.1). How would I change it so that it would work? Do I need another computer plugged into Ethernet? Thanks:confused:!

---

### Post by PatchesTheCaveman on 2011-01-04
Hi sansa90.  Happy New Year!

To figure out what's going on, we need to collect some diagnostic information.  To do that, go to Applications > Accessories > Terminal on your top panel, and type each of the following commands, pressing Enter after each one:
```
lspci -vnn
lshw -C network
ifconfig -a
sudo iwconfig
```
The last command will ask you for your password.  Enter it and press Enter.  It won't show stars or dots or anything, but it will work.

Once you've done all that, copy and paste the output to a reply to this thread.  With all that info, we should be able to figure out what's going on.

---

