---
title: "Linksys USB wifi dongle -- cannot see router"
date: 2005-12-17
forum: Networking &amp; Wireless
---

### Post by reuben on 2005-12-17
Hello, 

I am having trouble connecting to my router using my USB dongle. I have confirmed that the driver has loaded (although my model isn't listed - I have a USB 802.11B 2.8; however, lshw reports that I am using the atmel driver, like the v2.6 sibling of the dongle.)

I have tried scans using both wifi-rader and iwlist; both have the same results, in that the following message is printed to the console:

wlan0 : Failed to read scan data : Resource temporarily unavailable

Finally, in iwconfig, the router address is always 00:...00. 

I know my router is good, because I *can* use a wireless ethernet bridge with it; however, that is mains powered, so is not nearly as convenient.

Thanks in advance.

---

### Post by reuben on 2005-12-18
bump. ;)

---

### Post by Verbious on 2005-12-18
You might try doing some of the things in my post titled: [http://ubuntuforums.org/showthread.php?t=104298]("http://ubuntuforums.org/showthread.php?t=104298")

The first few times I tried, I had to reload Ubuntu because I wrecked the OS so bad. 

Bad hacker.

---

