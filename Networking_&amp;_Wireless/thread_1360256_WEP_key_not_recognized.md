---
title: "WEP key not recognized"
date: 2009-12-20
forum: Networking &amp; Wireless
---

### Post by omcgill on 2009-12-20
I had two computers with 8.04 and functional wireless connections.

Recently I upgraded the two computers from 8.04 to 9.10, one of them did not upgrade successfully and I needed to download 9.10 from the web and do a direct install of 9.10 from a download that I burned on CD. 

The computer that successfully upgraded from 8.04 to 8.10, to 9.04, to 9.10 now has an operational wireless network connection. 

The computer that I had to install 9.10 from a download CD will see the wireless network , but does not authenticate my WEP key when I enter it.

It appears that the wireless driver from the 8.04 version brought forward from upgrades works and the wireless driver downloaded with the 9.10 version does not work.

---

### Post by lewisforlife on 2009-12-21
I am not positive, but I think this is a bug.  I think WEP quit working in 9.04 and has never been fixed.  My only suggestion is that if you have control over the router to upgrade to WPA or WPA2.  It should work fine for you then.

---

### Post by omcgill on 2009-12-22
Remember WEP works if the computer is brought forward throught incremental upgrades 8.10, 9.04, 9.10.

I think that a 8.04 driver for WEP wireless would fix the problem, can anybody tell me how to revert back to a wireless driver for 8.04???

---

### Post by mrgumby on 2010-01-14
How could something like this be passed over?

I know that this situation is not easy, but this problem is a deal breaker since the netbooks have to travel and will have to deal with wep regularly.

---

### Post by omcgill on 2010-01-14
I found a solution to the problem by doing a search on the model number of my Linksys Wireless USB model number, it was a WUSB11 with V2.6 firmware. How can we get UBUNTU to include this in the distribution?
It was in Version 6.6 and now it's broke in all versions after 8.4.  go figure.

---

