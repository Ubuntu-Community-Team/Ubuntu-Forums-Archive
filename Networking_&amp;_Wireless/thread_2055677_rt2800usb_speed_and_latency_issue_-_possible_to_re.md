---
title: "rt2800usb speed and latency issue - possible to revert to rt2870sta driver?"
date: 2012-09-09
forum: Networking &amp; Wireless
---

### Post by etherealremnant on 2012-09-09
Hello, 

I am really racking my brains on this one...

I have a Rosewill RNX-N2X external USB card that I use to get WiFi. It runs on the rt2870 chipset and used to work just fine with the old STA driver.

Now that kernel 3 is out and has been migrated to the rt2800usb driver, my wireless speeds have shot WAY down. This is in both Qantal and in Mint 13 as well. In Windows I consistently get about 10 megabits per second. In any 3.x kernel variant, I am lucky to get 300KB/sec and usually average about 75KB/sec.

I tried to blacklist the 2800 and 2x00 and I compiled, installed, and modprobed the STA driver. It creates a network device called ra0 but it doesn't ever come up with any results on its scan and thus is useless.

Next I went looking around the internet for rt2870 XP drivers and tried ndiswrapper - kernel panics on the two I tried.

Finally I started swapping out firmware versions in lib/firmware thinking that might make a difference but it has made no difference whatsoever all the way up to Debian's latest binary.

I'm completely stumped as to what is going on here. It wouldn't be such a huge issue were it not for the fact that it makes it impossible to stream video, download files without the use of a download manager, and it loses packets constantly so I have to keep refreshing on websites at times.

Does anyone have any insight into this? I haven't tried putting an older version that had working STA on here because this is a new Core i5 laptop and I doubt the older distros would support the new hardware as well as the newer distros do.

---

### Post by Turies on 2012-09-25
I have DWA-125 with RT3070 chip. In 12.04 speed was VEERY SLOW but i was able to compile original ralink driver rt2870sta but in 12.10 it gives me KP. I tried to compile rt2800usb from 2.6 kernel but no luck - KP too. Something changed in kernel, i think. I'm thinking to downgrade my system to 12.04 back or thow this usb wifi to window. Not decided yet.
:-k

---

