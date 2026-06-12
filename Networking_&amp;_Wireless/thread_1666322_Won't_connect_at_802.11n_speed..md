---
title: "Won't connect at 802.11n speed."
date: 2011-01-13
forum: Networking &amp; Wireless
---

### Post by an4rew on 2011-01-13
Hardware
Edimax Wireless N Card (RT2860 Chipset)
Ubuntu 10.10 x64

Works out of the box when connected it idles around 1mb/s to 54mb/s when surfing/downloading etc.

It looks like i'm getting Wireless G speed so i installed the ralink driver, blacklisted the default ones.

Now i'm getting a constant 54mb/s but not the 270mb/s i get in Windows.

Have i missed something simple?

Edit: My Router is on the 2.4Ghz Band.

Thanks.

---

### Post by blakep2 on 2011-01-13
Is this a different computer than the one with windows.  Are they in different locations?

---

### Post by dbsjunk on 2011-01-26
I have the same problem with my rt3390. With the stock 10.10 driver (rt2800pci) I get a maximum of 2.5MB/s. This is connecting to an n-only network. My OS X 10.6 machine gets 9MB/s from the same router, in the same physical location. If I install the Ralink driver then I can not connect to an n-only network, and get similar speeds (up to 3.6MB/s) but can not even connect to an n-only network. (The syslog says it fails to find a BSSID that matches the one it is looking for, but iwlist reports the base station at the correct speed.)


It seems like the Ralink driver does not support n operation for some reason. 

Has anyone been able to get the Ralink rt3390 to actually run under ubuntu 10.10 at 802.11n speeds? I've seen lots of people saying "it works", but they're just testing loading web pages which isn't a great test of throughput.

---

### Post by copycat on 2011-02-05
> **dbsjunk said:**
> I have the same problem with my rt3390. With the stock 10.10 driver (rt2800pci) I get a maximum of 2.5MB/s. This is connecting to an n-only network. My OS X 10.6 machine gets 9MB/s from the same router, in the same physical location. If I install the Ralink driver then I can not connect to an n-only network, and get similar speeds (up to 3.6MB/s) but can not even connect to an n-only network. (The syslog says it fails to find a BSSID that matches the one it is looking for, but iwlist reports the base station at the correct speed.)


It seems like the Ralink driver does not support n operation for some reason. 

Has anyone been able to get the Ralink rt3390 to actually run under ubuntu 10.10 at 802.11n speeds? I've seen lots of people saying "it works", but they're just testing loading web pages which isn't a great test of throughput.

Same here.  I have only 54mb on my rt2800pci wih Maverick(Msi U100).  It is 802.11n compliant.

---

### Post by ilna on 2011-02-08
I'm next here. Having two rt2870 adapters (and 802.11n-capable router(s)) can connect at 54Mb/s only. Ubuntu 10.10 has very outdated rt2870sta driver (three years old, v.2.1.0). While Ralink suggests version 2.4 (mid. 2010). I have looked at 11.04 alpha - it has that ancient v.2.1.0 rt2870sta driver also... :mad:

---

### Post by annoyingrob on 2011-02-10
Modify /etc/modprobe.d/iwlagn and add the following line:

options iwlagn 11n_disable=0 11n_disable50=0

---

### Post by Jove on 2011-02-24
Similar issue here - have a rt3072 chipset adapter which loads the rt2870sta driver. However, only getting 54 Mbps connection. Added the "options iwlagn 11n_disable=0 11n_disable50=0" line to iwlagn as suggested, but doesn't appear to change anything. Using the rt3070sta driver from the ralink website allows 300 Mbps connection but WPA2 is very flaky. Connection drops every few hours then it's incredibly difficult to reconnect. Only way I've found to allow reconnection is to set my router to WPA, attempt connection (which usually fails) THEN reset back to WPA2 at which point the adapter will usually connect. Weird.

---

### Post by foxem2001 on 2011-02-24
i have the same issue,

i have posted in this thread
[http://ubuntuforums.org/showthread.php?t=1692377]("http://ubuntuforums.org/showthread.php?t=1692377")

i have had no reply as yet though

very frustrating

---

