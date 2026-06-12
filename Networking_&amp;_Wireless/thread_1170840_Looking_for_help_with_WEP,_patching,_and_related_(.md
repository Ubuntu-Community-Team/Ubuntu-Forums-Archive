---
title: "Looking for help with WEP, patching, and related (Please)"
date: 2009-05-26
forum: Networking &amp; Wireless
---

### Post by phantom3113 on 2009-05-26
So, I've been trying to figure this out with no luck. I've been wanting to try and crack the WEP on my home network to test the security (and hopefully improve upon it) but have been running into some problems. I've used google and used some info from this thread "http://ubuntuforums.org/showthread.php?t=514723" and have the general idea of what I'm supposed to do. So far, I have aircrack-ng installed and have had some success with testing it, although based off the aircrack wiki (and test runs) I need to apply a patch for packet injection to work.

My card set is Realtek rtl8187b (notice it's the "b" set) and was directed to this patch "http://patches.aircrack-ng.org/rtl8187-mac80211-injection-speed-2.6.28-rc6.patch" that was said to be needed for injection. Following these instructions --> [http://aircrack-ng.org/doku.php?id=patching&s](http://aircrack-ng.org/doku.php?id=patching&s)[]=patching, I've gotten as far as downloading the patch to my home folder and attempting to patch it, but the command line asks me for the file that I want to patch. Unfortunately, I have no idea what file needs patched!

I've gotten so close to achieving this on my own, but sadly I can go no further with assistance. Could anyone give a few guiding steps?

---

### Post by shemhamforash on 2009-05-28
Same here, I tried to download the kernel itself and found the file in there. Patched it and compiled it, but it only gave me a lot of error during compilation.

Is there anyone who can help us out?

---

### Post by shemhamforash on 2009-05-30
Just download the latest release of compat-wireless, and it should work ;) No need to patch anything then!

---

### Post by phantom3113 on 2009-05-31
Great, I shall try it out. Thanks!

---

