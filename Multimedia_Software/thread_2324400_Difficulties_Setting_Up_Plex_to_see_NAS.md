---
title: "Difficulties Setting Up Plex to see NAS"
date: 2016-05-13
forum: Multimedia Software
---

### Post by Robert_Billard on 2016-05-13
Hey folks,

I've been using Ubuntu off and on ever since Dapper Drake but there's always something that simply doesn't work, which pushes me back to OSX/Windows. There have been a ton of improvements over the years and a lot more things work out of the box, which is great. However, one thing that I've been struggling with recently, is getting Plex Media Server to work.

**Hardware:**
[Intel NUC 3rd Generation Core i3 Mini-PC]("http://www.intel.com/content/www/us/en/nuc/nuc-kit-dc3217iye-board-d33217gke.html")
[Netgear Nighthawk 1900 Router]("http://www.netgear.com/home/products/networking/wifi-routers/R7000.aspx?cid=gwmng")
[WD Elements 500gb Portable HD]("http://www.newegg.ca/Product/Product.aspx?Item=N82E16822136994")

**Software:**
Ubuntu 16.04 LTS Desktop 64-bit
Plex Media Server 64-bit (Version 0.9.16.6.1993-5089475)

I'm able to install Plex without any difficulty but I'm unable to browse to any of my media folders. I currently have all of my media stored on the WD Elements HD, connected to my Nighthawk router via USB 3.0. The computer I'm running Plex on is the Intel NUC and it's connected to the Nighthawk wirelessly (I plan to connect hard-wired once I can drill some holes and run ethernet).

I've done my due diligence with google searches and forum searches, but the scenarios are either different than my own setup, or the solutions are above my head and I don't know what to replace in the fstab edits. I've tried adding the plex user to the computer's admin usergroup, as well as vice-versa.

Any assistance or insight would be greatly appreciated.

Thanks,
Rob

---

### Post by TheFu on 2016-05-13
For plex to see the storage, it needs the permissions to be setup to allow that.  Which file system does the WD disk have?  EXT4 would be best.  NTFS would be the worst choice for a few reasons, IMHO.  If you mount NTFS under Linux, then you need to make the permissions what is required at mount time.  The only ways to do that are through the fstab options or autofs options.  No GUI mount will make this work. You **MUST** use to options above.

With Linux file systems, you can correct the permissions at any point after mount.

Adding plex to admin groups is a really, really, really, really, really bad idea. Put it back the way it was, is my best advice about that.

Many plex issues come down to file and directory permissions (a few are subnet related). BTW, OSX uses those same permissions, so, in theory, those shouldn't be new. Do you have a good handle on standard Unix file and directory permissions? If not, ask for help.

BTW, I run plex, but don't have the guts to try it on 16.04. Perhaps in 6 more months. For now, I'm staying on 14.04.  Binary apps that aren't F/LOSS need time to move to the next release. I'd rather NOT be an early adopter - let others, like you, find all the bugs.

Wired ethernet is much better than wifi.  Wifi might seem stable, but if you've ever watched the bandwidth for any wifi connection, you'll have seen wide fluctuations. Humans don't really notice those, but computers and streaming protocols do. Wired is so much better - stable, consistent, bandwidth.

---

