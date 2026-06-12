---
title: "Non-broadcom adapter not working now."
date: 2006-06-03
forum: Networking &amp; Wireless
---

### Post by gizzmoe on 2006-06-03
After reading around all day long, I decided to post about this since it seems that all the answers i could find pertained to a broadcom issue, which doesn't pertain to me.

I have a gigafast USB wireless adapter, the driver inf file is named AWLGTNIC.inf

In breezy, I had it working via ndiswrapper just fine.

However, when i installed Dapper today, I noticed it 'said' that it recognized it and it was enabled. However, the output from iwconfig doesn't agree. The ESSID is correct, yet it says Access Point: Invalid. 

I'm not able to ping the router either (the output i get from ping is 'network unavailable').

Also unable to get an IP because after it tries for a while, dhclient is not able to get an IP from the dhcp server.

So, at this point, i installed ndiswrapper from the newest version's (1.16) source. I used this version instead of the one from the repository (1.8 ) because 1.16 is what i had installed on breezy so i knew that my adapter worked with it.

After installing ndiswrapper and loading the driver and doing 'modprobe ndiswrapper'. I'm still getting the same output...even though this exact same version of ndiswrapper worked flawlessly in Breezy...

One thing that i noticed while doing all this is that my wireless adapter is now called 'eth1' instead of 'wlan0' like it was in Breezy, if that should make any difference.

Any help would be greatly appreciated. Dapper detects all my other hardware where Breezy wouldn't, EXCEPT my wireless... so i really would like to get this working.

[edit] If there's more info that i can provide, please tell me.

[edit2] Just thought of these things: I tried going through channels 1-14 using iwconfig and it didn't help. Also, I tried to manually set the IP and that also didn't help any.

---

