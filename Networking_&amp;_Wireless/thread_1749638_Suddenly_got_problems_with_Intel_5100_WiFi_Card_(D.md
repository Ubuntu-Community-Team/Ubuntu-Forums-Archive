---
title: "Suddenly got problems with Intel 5100 WiFi Card (Dell Latitude E6400)"
date: 2011-05-04
forum: Networking &amp; Wireless
---

### Post by tincup on 2011-05-04
Hi folks.

I am running (K)Ubuntu Lucid 10.04 64bit on a Dell Latitude E6400, WiFi Card Intel 5100. Never had any problems with networking. Up to about 2 weeks ago. I do realize there have been quite a few posts with this network adaptor, but non really described the problem I have here.

What happens is that suddenly the WiFi LED on the computer stops blinking, the WiFi connection gets disrupted, and the device is not recognized anymore when checking ifconfig. Only cold restarting the machine helps then... it will work for a while (between 1 and 20 minutes) and then crash again.

On Windows 7 the card works perfectly fine. With Ubuntu 11.04 in Live CD mode I have the same effects (connection crashes after a while). Also tried booting an older kernel, no success.

My exact hardware:
```

$ lspci | grep -i network
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
0c:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100

```

I notived the following problems in /var/log/kern.log

```

May  4 23:52:04 tinbook kernel: [ 1393.540342] No probe response from AP 00:1e:e5:45:fa:4d after 500ms, disconnecting.
May  4 23:52:05 tinbook kernel: [ 1394.040187] iwlagn 0000:0c:00.0: Error sending REPLY_RXON: time out after 500ms.
May  4 23:52:05 tinbook kernel: [ 1394.040201] iwlagn 0000:0c:00.0: Error setting new RXON (-110)
May  4 23:52:05 tinbook kernel: [ 1394.570277] iwlagn 0000:0c:00.0: Error sending REPLY_RXON: time out after 500ms.
May  4 23:52:05 tinbook kernel: [ 1394.570289] iwlagn 0000:0c:00.0: Error setting new RXON (-110)
May  4 23:52:05 tinbook kernel: [ 1394.590398] cfg80211: All devices are disconnected, going to restore regulatory settings
May  4 23:52:05 tinbook kernel: [ 1394.590410] cfg80211: Restoring regulatory settings
May  4 23:52:05 tinbook kernel: [ 1394.590418] cfg80211: Calling CRDA to update world regulatory domain
May  4 23:52:05 tinbook kernel: [ 1394.595304] cfg80211: World regulatory domain updated:
May  4 23:52:05 tinbook kernel: [ 1394.595311]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
May  4 23:52:05 tinbook kernel: [ 1394.595318]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May  4 23:52:05 tinbook kernel: [ 1394.595325]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
May  4 23:52:05 tinbook kernel: [ 1394.595332]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
May  4 23:52:05 tinbook kernel: [ 1394.595338]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May  4 23:52:05 tinbook kernel: [ 1394.595345]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May  4 23:52:06 tinbook kernel: [ 1395.192647] iwlagn 0000:0c:00.0: Error sending REPLY_RXON: time out after 500ms.
May  4 23:52:06 tinbook kernel: [ 1395.192658] iwlagn 0000:0c:00.0: Error setting new RXON (-110)
...
...
May  4 23:52:21 tinbook kernel: last message repeated 11 times
May  4 23:52:21 tinbook kernel: [ 1410.395136] iwlagn 0000:0c:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May  4 23:52:21 tinbook kernel: [ 1410.416045] iwlagn 0000:0c:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May  4 23:52:21 tinbook kernel: last message repeated 3 times

```

and hundreds more of the 'deep sleep' lines.


Any help is highly appreciated!

Thanks,
 tin

---

### Post by tincup on 2011-05-06
bump. one more try.

No one has ever experienced something like this before?

---

### Post by evil23666 on 2011-05-12
hi, were you able to find out what was happening. i just ditched windows on this e6400 & started getting the same problem.

[http://ubuntuforums.org/showthread.php?t=1525780](http://ubuntuforums.org/showthread.php?t=1525780)

 i have tried the steps here & will have to see if it resolves anything for my issue. 

altho my problem was slightly different (no deep sleep messages). i was able to enable then disable the wireless to get it back on & working.

 i've only just ran the steps, so not sure if it really has helped my issue...

---

### Post by theteju on 2011-05-13
Your network card is same series as mine. See it this thread helps you at all !!

[http://ubuntuforums.org/showthread.php?t=1756096](http://ubuntuforums.org/showthread.php?t=1756096)

just to note, my system is 32 bit and its ubuntu 10.04. So if you are about to install new driver mentioned in that thread find yours accordingly.

hope that helps.

---

### Post by evil23666 on 2011-07-12
> **theteju said:**
> Your network card is same series as mine. See it this thread helps you at all !!

[http://ubuntuforums.org/showthread.php?t=1756096](http://ubuntuforums.org/showthread.php?t=1756096)

just to note, my system is 32 bit and its ubuntu 10.04. So if you are about to install new driver mentioned in that thread find yours accordingly.

hope that helps.


Thanks, I had upgraded to 10.10 & just recently to 11.4 & am lead to believe i still have the same issue... kinda forgot all about this post/issue & community help. it's a work laptop that i'm normally on the work desktop (@ work)... :) I'm going to give this a try when i can, hopefully sooner than my reply to this!! i shoul dbe able to get to it either tonight or tomorrow.

 thanks again!!

---

