---
title: "wlan0 connected to internet and eth0 for ssh - but no internet"
date: 2011-02-17
forum: Networking &amp; Wireless
---

### Post by juan234 on 2011-02-17
Hi All,

wlan0 is connected to a router with internet. 192.168.22.1
eth0 is connected to a router to lan 192.168.2.1

both my interface addresses are via DHCP

I am not sure what I have to do to get out on to the internet on 22.1 (wlan0) and ssh a box on 2.1 (eth0)

I have looked thur the networkmanger options, maybe i am missing something.

Many thanks,

Juan

---

### Post by mr_luksom on 2011-02-18
Is it possible to post the output of the following terminal commands:

```

ifconfig
iwconfig
cat /etc/network/interfaces

```

---

### Post by skief on 2011-03-01
Hi. I'm having a similar problem. Let me provide more detailed information for my case, and maybe we'll solve juan234's problem as well.

This came out of the blue. I didn't change anything in my /etc/network/interfaces. Yet all of sudden, while I seem to be connected to the Internet, I can't open any web page, or ssh anywhere.

I have my wired connection on eth2. In /etc/network/interfaces the only line relevant to eth2 is:
```
iface eth2 inet dhcp
```
In the output of ```
ifconfig
``` under eth2 I *have* an IP address (under inet addr).

I tried
```

sudo ifdown eth2
sudo ifup eth2

```
to restart things. No help.
The one anomaly is that at the end of ifup I get
```

 * Starting the Firestarter firewall...
   ...fail!

```
but frankly that's been there for a while. (Been meaning to remove Firestarter and switch to ufw. :P)

And yes, the problem is with my computer, not my ISP. My other computer connects to the Internet just fine, on the same ethernet cable.

Thanks for any help you can provide.

ps The computer is running Lucid Lynx.

---

### Post by skief on 2011-03-02
Okay folks,

My connection works again, but I didn't do anything. It just decided to work again.

I notice this person:

[http://ubuntuforums.org/showthread.php?t=1473794](http://ubuntuforums.org/showthread.php?t=1473794)

had the same experience.

It's all fine and well when these things clear themselves up on their own, but still I'd like to understand what happened, especially in case it happens again.

Therefore, quiz question: Can anyone say why this should happen on Ubuntu:
(1) One day you have an IP address but can't open a web page in firefox, and can't ssh anywhere.
(2) Your other computer works perfectly on the very same ethernet cable.
(3) The next day everything's back to normal.
(4) You didn't touch a thing during the whole process.

?????

Point (2) would suggest that the problem was within your computer, whereas point (4) would suggest that it was not. Can anyone figure this out?

---

