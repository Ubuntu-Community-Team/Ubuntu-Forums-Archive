---
title: "WiFi works for a while and then......"
date: 2012-02-04
forum: Networking &amp; Wireless
---

### Post by K-Sub on 2012-02-04
I have a Dell Mini 10V with the infamous Broadcom BCM4312 wireless  adapter.  WiFi seems to work fine on the computer, but then I turn on the computer a day or so later and WiFi no longer works, even  though there has been no change to the configuration.

The WiFi recently stopped working so I updated to 11.10.  After the update, I  restarted the computer and, boom, it connected immediately to WiFi.  This worked well for a few days, but then I turned on the computer and the WiFi  wouldn't connect.

So, I plugged in cable and went to the page that I always have open in Firefox:

 [FONT=&quot][https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)[/FONT]
  
I followed the procedure, restarted the computer and the WiFi worked fine.  I turned off the computer.  I turned it on the next day, the WiFi worked fine.  I turned off the computer.  I turned it on the next day, the WiFi worked fine.  I turned off the computer. I just started it again this morning, and it would not connect to WiFi even though it saw the network with a strong signal.  I've now tried this three times, and nothing.

Is there anything else I can do to make this work reliably?  I'm at a loss as to why it would stop working when there is no change in the Ubuntu configuration.  I swear this problem has been getting worse with the later versions of Ubuntu and it is getting very frustrating.  I cannot live with a netbook that cannot reliably connect to WiFi; in the field I will not have a hardwire connection to use to reload the driver.  At this point I'm thinking that my only solution is to install Windows.

Can any of you think of anything else.

---

### Post by K-Sub on 2012-02-04
...oh and I'm using the STA wireless driver.  I think when I first got this computer, I was running 8.04 and the b43 driver, which seemed to work better, but I'm not sure how to load that and see if it will work again.

---

### Post by K-Sub on 2012-02-05
OK, just to see what would happen, with the computer off-line I went to additional drivers and deactivated the STA driver, then activate it.  The first time I did this wireless cam up immediately.  Then, when I restarted the computer, no wireless.  I repeated the process, but this time the wireless did not come up until after a restart.  Then when I did another restart, again, no wireless.  This is all very weird.

---

