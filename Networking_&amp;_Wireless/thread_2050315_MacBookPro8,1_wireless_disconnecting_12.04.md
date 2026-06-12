---
title: "MacBookPro8,1 wireless disconnecting 12.04"
date: 2012-08-30
forum: Networking &amp; Wireless
---

### Post by kerryhall on 2012-08-30
Wireless works from the instructions here:

[https://help.ubuntu.com/community/MacBookPro8-2/Oneiric#Wireless](https://help.ubuntu.com/community/MacBookPro8-2/Oneiric#Wireless) 

(Although I am using 12.04, not 11.10)

However my wireless connection appears to be dropping randomly, but I can't seem to locate the issue as dmesg is spammed with a lot of this sort of junk:

[90348.159499] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[90348.159502] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

Although I did find this:

[90997.177550] wlan0: deauthenticating from [MAC ADDRESS] by local choice (reason=3)

I am also continually prompted for my password. I know the issue is very likely not the access point, because I never had any wireless dropping issues when I was running OSX. (I also have this wireless dropping issue on three other Ubuntu 12.04 machines, with various wireless cards but that is a thread for another day)

What is also interesting to note is that I am not sure that my connection is actually being dropped, as my ssh sessions stay active (but can experience high latency during a drop)

Thanks a ton!

Edit:
I was connected via wired connection as well, (lol probably the reason my ssh sessions stayed up) but that shouldn't explain why the wireless connection is dropping randomly. Also, I cannot untick the "enable wireless" box...something is very wrong there. I try unticking the box and it stays ticked.

Also: clicking "Edit Connections..." and "Connection Information" does nothing. It looks like gnome network manager is seriously buggy.

---

