---
title: "My Netgear Wireless G Router is starting to flake out. What can I do?"
date: 2009-05-21
forum: Networking &amp; Wireless
---

### Post by diablo75 on 2009-05-21
I have a netgear WGT624 v3 Wireless G router. I run linux, and recently I started noticing that anytime I tried to download a large file (like a deb file which is similar to a setup.exe in some ways) would be corrupted. Running md5sum would confirm that each download attempt would be corrupted differently every time.

I ruled out the laptop by bypassing the router and going strait to the cable modem and with that connection I had zero errors. Otherwise, connecting to the router wirelessly causes problems (and this has been confirmed via a laptop, a PC and an iPhone which has also experienced download problems with installing apps).

The router is currently running the latest available firmware and it's been running this version for at least a year with no issues up until a couple days ago.

I've attempted to reset the router to it's factory defaults and work my way back up to a wireless WPA2 connection from scratch, but it didn't solve anything. Even disabling encryption entirely still produces the same problem. Some downloads just locks up for minutes before resuming and ultimately to no good end as the download is still corrupt.

So, does this sound like a hardware problem? Think it might be possible to fix it somehow? Perhaps blowing dust out of it maybe? Probably worth a shot but I've never heard of anyone doing that before.

Any other suggestions? Would it be worthwhile to attempt to reinstall the firmware? Or even revert to an older version to see if it helps?

Or does it sound like an irreparable hardware fault? I just want to take every step I can to avoid spending money on a new one as I'm a little short on money at the moment and need to be frugal.

---

### Post by diablo75 on 2009-05-22
Just a little update:

I don't think it's the cable modem. Everything I download via a direct connection to the router checks out per md5sum. For example I went to the Virtualbox homepage and download 6 different deb files for different versions of ubuntu (some 32-bit, some 64, 9.04, 8.10 and 8.04). All 6 files would check out. Subsequent checks have produced the same positive results with no errors.

However, when I connect the router to the modem and then the laptop to the router via an ethernet cable and attempt the same test, all 6 files fail the md5 integrity test. I've repeated the test with and without the router 3 times, and the same results occur every time.

To clarify, I purchased a new router in an attempt to solve this same problem I was having with my old one. The new one is a Netgear wgr614 v9 and I just finished updating it's firmware to the latest available version. The firmware upgrade did not provide better results at all.

I'm on the verge of taking the router back to walmart in exchange for another one to see and pray it makes a difference. It just seems strange for two routers (one of them brand spanking new) to exhibit data integrity issues over a hardline, not to mention the wireless. In fact, I disabled the wireless antenna on the new router when performing another download test through the routers ethernet ports, but it still didn't make a difference.

---

### Post by pricetech on 2009-05-22
Strange indeed.  One would not want to blame that on a router, especially since you had the same thing happen with a second one.

Go ahead and take the new one back and swap for a different brand.  As crazy as it sounds, some things just won't play well with one another.  I had issues with several netgear cable modems dying after service interruptions, with no explanation to be found.

Could the old router be new enough to be under warranty ??  Netgear's support people can be morons, but it's worth a try as long as you don't have to deal with customer service.  They are the reason I swore off netgear.  Register the product at the website before you call.  They'll do nothing if the product isn't registered.

Just to be sure;  can you borrow a cable modem  or a router from a friend to see if another hardware combination might work better ???

Best of luck.

---

### Post by diablo75 on 2009-05-22
I actually ended up swapping it for another netgear, a more expensive one.  It's a Netgear WPN824 v3.  Works GREAT!  I'm glad that's over with.

---

