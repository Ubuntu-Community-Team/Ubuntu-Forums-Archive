---
title: "Atheros AR928X - Connection drops after a few minutes on Ubuntu 11.04"
date: 2011-07-02
forum: Networking &amp; Wireless
---

### Post by yoavbo on 2011-07-02
Hello,

I've just signed up for Virgin Media 30MBPS broadband in the UK. I connected the equipment and everything was working, but then the connection dropped to 0 kbps after a few minutes and I couldn't do anything - not even access the hub configuration on 192.168.0.1. I am able to connect again by disconnecting the hub from the power socket and then reconnecting it.

Virgin tech support won't help me because they don't provide support for linux.

My mobile phone (HTC Desire) seems to connect just fine. Actually better than that. Using my laptop's wireless connection I was able to download at 150kbps. Now I'm using the wireless connection trough my phone and speed is up to 1.2mbps.

So there is clearly something wrong with the wireless configuration, because my connection drops and when it does work, it works slowly.

How do I fix that? Would and firmware/driver upgrade help? And if so, how do I do that?

I've get Acer Aspire 1410 with Atheros Communications Inc. AR928X and Ubuntu 11.04 

Thanks in advance,
Yoav

---

### Post by MoebusNet on 2011-07-02
It looks like someone else had a similar problem:

[http://ubuntuforums.org/archive/index.php/t-1740056.html](http://ubuntuforums.org/archive/index.php/t-1740056.html)

---

### Post by yoavbo on 2011-07-02
> **MoebusNet said:**
> It looks like someone else had a similar problem:

[http://ubuntuforums.org/archive/index.php/t-1740056.html](http://ubuntuforums.org/archive/index.php/t-1740056.html)

Thank you. I have used the solution in the thread.
Now I do get faster speeds (more than 3M per second) but the connection drops after a few seconds and I have to restart the router to use it again.

---

### Post by yoavbo on 2011-07-02
One more detail - the router that I'm using is a "wireless N"

---

### Post by omns on 2011-07-04
> **yoavbo said:**
> One more detail - the router that I'm using is a "wireless N"

This appears to be the problem. I've read that you can get around it by switching off N (and just use G) but that doesn't seem like a satisfactory solution. I'm hoping the tips in the above link will provide me with a solution.

---

### Post by bmalek on 2012-02-22
I changed the settings on my CISCO router from WPA Personal TKIP to WPA Personal AES and it worked for me.

---

