---
title: "TiVo USB card."
date: 2009-04-12
forum: Networking &amp; Wireless
---

### Post by MrVining on 2009-04-12
So I've been Googleing and searching, but not finding a lot of help.  I'm sure part of the issue is that I'm soo new to Linux and proly not searching for the right terms or tools.  Anyway I have just started to use MythTV I bought parts to build a few frontends, and a backend.  Two of the frontends need wifi, I hate it, but this place is a rental and I hope to be out of here in a few months anyway.  I have two of the "[TiVo Wireless G USB Network Adapter]("https://www3.tivo.com/store/accessories.do")" that I would like to get working.

I just can't figure out where to even start.:confused:

I have found enough searching to do lsusb here is what I get:
Bus 001 Device 002: ID 0a5c:bd11 Broadcom Corp.

Any would be great, but extra help for a newb would be even better. =)

---

### Post by kudzu74 on 2009-09-21
"I have two of the "[TiVo Wireless G USB Network Adapter]("https://www3.tivo.com/store/accessories.do")" that I would like to get working."

------------------------------------------------------------------------------------------------------------------------------

Well, I wish you the best of luck with this one...using these adapters in Linux isn't supposed to be possible as far as I have found, but I am working on this problem presently. I've been at it for hours; the consensus appears to be that they won't work with windows or Linux, I found:

[http://sourceforge.net/projects/tivousbwifi/](http://sourceforge.net/projects/tivousbwifi/)

which appears to offer a basic driver for this adapter, I believe. However, I've had no luck getting it to work; first it said it couldn't retrieve the firmware, so I went to their cvs tree and tracked the firmware binary down and called the load script with the '-f' option to specify firmware location and it completed successfully, however, all that I can see that changed is the output from lsusb, while dmesg showed that the device gained a more proper appearing id than "00000000001"--no functionality though. That's as far as I got with that. Gonna try the Linux Wireless package's rndis_wlan module and see what I can do with it. 

I wouldn't be going at this so tenaciously were it not that I know *for a fact* that I have had this very same adapter working under some version of Linux in the past (and the range/signal quality was extreeemly good, almost on par with something like a Hawkins Technology dish). I just wish I remember what distro (it was a live cd) that I was using...I thought it was BackTrack3 but I tried that already without any luck.

I will bookmark this post; if I have any success I'll drop a line on how I pulled it off.

---

