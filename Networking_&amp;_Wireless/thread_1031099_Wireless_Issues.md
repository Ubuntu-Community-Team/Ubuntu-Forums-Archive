---
title: "Wireless Issues"
date: 2009-01-05
forum: Networking &amp; Wireless
---

### Post by RishabhBhatia on 2009-01-05
I installed Ubuntu 8.1 about a week back, and I had problems with my Atheros AR5007EG wireless card but I fixed that with the linux-backports fix. Now, I can connect to the internet but occasionally, about 30 minutes into usage, my wireless internet gets disconnected and I cannot reconnect in anyway. Sometimes it reconnects automatically but most of the time I have to restart to get it working. This is really getting annoying for me.

I am very new to Linux so I am not aware, or capable of using to complicated methods to fix this?

Are there any fixes for this problem, and if so can you run me through them step by step so I can understand it. Thanks.

Also, there is nothing wrong with my router or anything else, it has something to do with Ubuntu as it doesnt happen when I dual boot into my Vista.

Thanks again.

---

### Post by HuaiDan on 2009-01-05
you're lucky. I tried the backports fix, and this is the second time I've lost alll connectivity, AP's, etc, and it doesn't come back after rebooting. Last time it decided on its own when to come back, now I'm DITW again.

If you find a fix. let me know.

---

### Post by RishabhBhatia on 2009-01-05
Bump, anyone help?

---

### Post by stream303 on 2009-01-05
Do you need to be running at full speed - perhaps trying a lower speed with the linux drivers might help.  In fact, I just did this with my netgear usb wireless when it would randomly disconnect.

Since I don't need super high speeds on my local network, and my dsl isn't very fast anyway, I just dropped it back to 5.5M - can't even tell the difference but my random disconnects are gone.  I also changed my router's channel about 2 channels away from a neighbors, which helped.

All I did was edit **/etc/rc.local** and added this iwconfig line *before* exit 0 to slow the card down a bit:

(iwconfig wlan0 rate 5.5M fixed)

```

# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

iwconfig wlan1 rate 5.5M fixed

exit 0

```

And just rebooted.

You can try other speeds such as 24M, 11M, 5.5M, 2M, and 1M ...

---

