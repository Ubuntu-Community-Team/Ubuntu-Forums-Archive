---
title: "No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219."
date: 2010-07-22
forum: Networking &amp; Wireless
---

### Post by rlinsurf on 2010-07-22
I'm trying to install a BCM4328 (rev 03) 14e4:4328 (rev 03) by using this page:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

But when I get to this step:

[B]
Step 3: All BCM43xx - Configure NDISWrapper (and WPA Supplicant)[/B]

 sudo ndiswrapper -i bcmwl5.inf


I keep getting:

jeffrey@jeffrey-desktop:~/bcm43xx$ sudo ndiswrapper -i bcmwl5.inf
couldn't open bcmwl5.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.

What am I doing wrong?

Thanks.

---

### Post by rlinsurf on 2010-07-23
I've made progress. It turns out the instructions just put me in the wring directory. I did a search for the file, and found it in Downloads/DRIVER. I ran the full set of commands from there, and got through all of them.

However, no wireless is showing up under Network.

So can someone tell me what I'm doing wrong here?

---

