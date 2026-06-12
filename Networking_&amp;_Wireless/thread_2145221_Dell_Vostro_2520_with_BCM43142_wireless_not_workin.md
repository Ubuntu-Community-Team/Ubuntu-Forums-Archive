---
title: "Dell Vostro 2520 with BCM43142 wireless not working after upgrade from 12.10 to 13.04"
date: 2013-05-14
forum: Networking &amp; Wireless
---

### Post by diablo75 on 2013-05-14
Edit:  Solved.  As I wrote below, I ran "sudo apt-get install bcmwl-kernel-source" and it installed with no errors, but didn't work.  After doing this with a Live CD, it still didn't work.  But then I tried the Fn-F2 keyboard combination.  Turns out the thing was soft-switched off.  Shortly after doing that I rebooted and wireless worked.  I could have sworn I tried this before, but I'll be it was after I tried the deb file and before I installed the source package with apt-get.

-------------

I have a Dell Vostro that originally came with Ubuntu 12.04 (or maybe it was 11.10, I can't remember) pre-installed by Dell.  I manually updated to 12.10 after getting it in the mail, formatting and reinstalling from disc.  Back then I had to use the steps in this thread to get wireless working:

[http://ubuntuforums.org/showthread.php?t=2094180](http://ubuntuforums.org/showthread.php?t=2094180)

I tried to repeat these steps to fix the problem after it reappeared with the upgrade to 13.04, downloading the [wireless-bcm43142-dkms_6.60.55.19-1_amd64.deb]("https://www.dropbox.com/s/jerkl6uqal5ylv3/wireless-bcm43142-dkms-6.20.55.19_amd64.deb") and using dpkg to install it but it would encounter an error (that I failed to document).  I then started trying to find threads dealing with this issue (with 13.04) to see if there was a new trick.  I found a post that said something like "bcmwl-kernel-source" had been updated, so I installed that, I didn't recall seeing any errors, the compile process looked similar to what happened when you run the deb file above but better... but wireless still doesn't work.  If I open up Software & Updates and check the Additional Drivers tab, it shows "Using Broadcom 802.11 Linux STA wireless driver source from bcmwl-kernel-source (proprietary)" is in use.  I tried running the deb file one more time but now it says something's in the way; something the bcmwl-kernel-source put in I think.  Sorry I sound like a laymen right now but this is stuff that happened late a couple of nights ago and all the details aren't clear.

Out of lazyness (if you didn't already get that I'm lazy) I decided, "Well if nothing else I can just backup, format and reinstall.  Shotgun approach that takes little interaction and some waiting but I'm not in a hurry.  But when the Live CD finished loading up I had noticed wireless didn't work with it out of the box and had a feeling I'd be back in the same situataion even after reinstalling and it wouldn't be worth the effort; at least not until I trying something else.

Thanks in advanced!

---

