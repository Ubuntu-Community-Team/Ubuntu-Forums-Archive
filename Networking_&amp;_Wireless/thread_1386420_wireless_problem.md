---
title: "wireless problem"
date: 2010-01-20
forum: Networking &amp; Wireless
---

### Post by stevenroose on 2010-01-20
I just installed Ubuntu 9.10. Had running Ubuntu 8.04 LTS without wireless or other network problems. Now the following is happening:

My wireless network is shown and i can connect properly. But, when connected, most websites can't load, either FF or Chrome. The connection (Connecting with...) is made, but the loading (Waiting for...) doesn't seem to work. With times, it succeeds so i can open some webpages, but other time i can't. After 3th try, the update manager could download the packages, and i tried Evolution, which had some problems too.
When testing chat, my Google Talk contact could load, but a chat wasn't possible. My MSN contact didn't load at all.

I don't know what the problem. Can be, because my internet works partially, and partially fails.

Any ideas?


Thanks!

Steven

---

### Post by PartsMan on 2010-01-20
Have you loaded flash?.

---

### Post by stevenroose on 2010-01-21
Hmm, I don't think any of the websites that could load had flash in it, so no, I didn't.

---

### Post by djchandler on 2010-01-21
Can you link your ethernet cable between the router and computer and see if your hardwired connection is having problems?

This sounds like a WLAN hardware driver problem to me. You're not getting a good connection to the wireless router. How many bars do you see in the network manager applet? You should get at least 3, or there will be problems.

My Atheros WLAN had similar problems until the last couple of kernels (driver is a "blob" in the kernel).

What WLAN chipset are we talking about, and how far away are you from the router? If you bring the router and computer closer together, does the situation improve?

---

### Post by stevenroose on 2010-01-21
I couldn't check for a wired connection, but I think that one would work.

I'm not that sure but Yes, I think I got an Atheros network card. Using a Toshiba Satellite A100 or something similar.

The only thing I can give is the error message Chrome produces:

Error 324 (net::ERR_EMPTY_RESPONSE): Unknown error.


Maybe we can chat a second so I can respond directly?


Grts

---

### Post by stevenroose on 2010-01-21
Got detailed information about my network drivers.

Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

I really need my internet to work properly!
Does anybody recognises this issue? I can't even name it, so I can't search for solutions. :/

---

### Post by djchandler on 2010-01-21
I have a Toshiba laptop that had this problem too. Get rid of madwifi, then make sure the ath5k driver isn't blacklisted.

The Atheros driver is a "blob" (ath5k) in the kernel. You shouldn't need to install any other driver. We had problems with Jockey blacklisting ath5k after installing and uninstalling the proprietary (madwifi) driver in 9.04. Although the bug has been triaged as low priority, it remains a bug.

See this Launchpad discussion.
[https://bugs.launchpad.net/ubuntu/+s...ey/+bug/413781]("https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/413781")

Also see these threads.
[http://ubuntuforums.org/showthread.php?t=1238766](http://ubuntuforums.org/showthread.php?t=1238766)
[http://ubuntuforums.org/showthread.php?t=1234678](http://ubuntuforums.org/showthread.php?t=1234678)

---

