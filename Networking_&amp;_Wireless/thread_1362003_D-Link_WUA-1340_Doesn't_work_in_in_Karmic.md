---
title: "D-Link WUA-1340 Doesn't work in in Karmic"
date: 2009-12-22
forum: Networking &amp; Wireless
---

### Post by skimpniff on 2009-12-22
I started with Jaunty and got a WUA-1340 for the purposes of using with the Aircrack-ng suite. I plugged it in, it worked, I installed the proper driver patch as described and all was well. I then upgraded to Karmic recently, and now the USB card is not recognized at all. The light on the device won't even turn on, it's as if the device doesn't exist at all. I then restored my PC back to an image I had with the previous Jaunty OS after exhaustively trying to trouble shoot the issue and thinking it may have been a hardware failure. Once restored, the device and drivers work flawlessly again. I chalked it up as an issue attributed to a new package release and figured it would work itself out. Then last night the newest kernel update for Jaunty was released (2.6.28-17 I think), so I installed it and encountered the same issue as with the Karmic upgrade. I would love to upgrade to Karmic as it has so many new and exciting advantages, however, I am not willing to sacrifice the use of my USB card/Aircrack-ng functionality.
 

I have tried repeating all of the driver installation steps as if it was a fresh install and this did not correct the problem. I have seen several posts regarding Wine and windows drivers, but these are not applicable as I am using the RT73 drivers specified on the Aircrack homepage ([http://www.aircrack-ng.org/doku.php?id=rt73](http://www.aircrack-ng.org/doku.php?id=rt73)) specifically and exclusively for use with the suite. I am assuming that the issue is either that something that was default within the 2.6.28-16 kernel is no longer default in the later kernel releases, or that something that is required to make the card work is being deleted in the upgrade process, I just don't know what it might be. I am baffled that the card won't even turn on in any of the newer kernels.
 

I have checked to make sure the proper files are stilled installed (regarding the rt73 driver patch) and checked that the blacklist is correct. All is as it should be, yet the card remains dark and undetected. If I run Karmic with the 2.6.28-16 kernel loaded it is fine, but with any kernel newer than that, ie 2.6.28-17 or 2.6.31, I am SOL.
 

How do I make the card and drivers work in the latest kernel releases?

---

