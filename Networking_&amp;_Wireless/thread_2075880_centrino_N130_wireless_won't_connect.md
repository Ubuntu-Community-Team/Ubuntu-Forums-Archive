---
title: "centrino N130 wireless won't connect"
date: 2012-10-24
forum: Networking &amp; Wireless
---

### Post by leisure01 on 2012-10-24
Recently installed Ubuntu 10.04.3 with CAELinux on Samsung NP300E5A laptop. Have been unable to connect to the internet. Wireless card is Intel Centrino N130, This website [http://www.intellinuxwireless.org/?n=Info](http://www.intellinuxwireless.org/?n=Info) seemed to indicate that card was compatible with Ubuntu. I have no experience with Ubuntu or linux and would be grateful for any assistance.
Attached file gives some information on system.

---

### Post by ahallubuntu on 2012-10-24
Ubuntu 10.04.3 is an older release that is unlikely to work out of the box with a newer laptop like yours.  I recommend using the newer Ubuntu 12.04 LTS instead to start.

---

### Post by leisure01 on 2012-10-24
Ahallubuntu,  thanks for your response.  Unfortunately the later version of Ubuntu is not compatiblewith the other software on the CAELinux distro so updating isn't an option.

---

### Post by ahallubuntu on 2012-10-24
What kernel are you using?  In a terminal, type

```
sudo uname -a
```


According to this:

[http://intellinuxwireless.org/](http://intellinuxwireless.org/)

Your wireless card should be supported in the kernel automatically after kernel 2.6.24 .  I'm using Ubuntu 10.04 on my laptop, and my kernel is 2.6.32 .  (I'm using an Intel wireless card that worked automatically, but it's an older one than yours.)  Have you done all of the updates (with say a wired connection)?  If not, that may update your kernel and may give you the support you need for that wireless card.

---

### Post by ahallubuntu on 2012-10-24
Oh, wait, I read that page more carefully and saw this:

*Intel® Centrino® Wireless-N 130 (2.6.37)*

which means your card didn't get kernel support until the 2.6.37 kernel - newer than mine.  You could build a newer kernel (or just the kernel headers) 2.6.37 or and that should fix it.  I don't know how to do this off the top of my head, but these instructions may work exactly:

[http://ubuntuforums.org/showthread.php?t=1940468](http://ubuntuforums.org/showthread.php?t=1940468)

---

### Post by leisure01 on 2012-10-25
Thanks for the suggestion, I will check out the thread this evening when I get back from work.

---

### Post by leisure01 on 2012-10-25
I had a look at the threads but the instructions were beyond my newbie level!
Still looking for a solution.

---

### Post by leisure01 on 2012-10-28
I had another look at this, found some courage from somewhere and used the thread referenced by ahallubuntu to install the wireless driver from a later version of ubuntu.  It all went smoothly up to the point where the wget and tar commands were required.  For some reason a not found error occurred.  However this was overcome by going direct to the http address, downloading and extracting the required files to my machine and then carrying on with the rest of the steps.
The wireless is now working perfectly and I didn't need to upgrade to the latest version of ubuntu which would have caused problems for some of the applications on the CAELinux distribution.
Thanks to all who have helped.

---

