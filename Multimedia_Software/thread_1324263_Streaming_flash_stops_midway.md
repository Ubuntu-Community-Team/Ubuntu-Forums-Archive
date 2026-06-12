---
title: "Streaming flash stops midway"
date: 2009-11-12
forum: Multimedia Software
---

### Post by A Traveller on 2009-11-12
Hi All.

I recently upgraded to the latest 9.10 version and installed Adobe flash to view streaming video on YouTube, etc. It was working fine, however, now it just stops in the middle of playing and shows a blank screen. On my computer, the blank screen is light blue, but that may be due to personal settings.

I have not installed anything else or made any other changes to the system at all. The only thing I have done is accepted all the updates that automatically suggest themselves.

Is it possible that one of those updates has caused the problem? If so, does anyone have any idea which one(s) and what can be done to rectify the problem?

Thanks.

---

### Post by beastrace91 on 2009-11-12
Try removing and reinstalling the flash plugin. I know on my 64bit Jaunty install I have to do this on occasion to keep my flash working.

~Jeff

---

### Post by HappyFeet on 2009-11-12
> **A Traveller said:**
> 
Is it possible that one of those updates has caused the problem?

Yes, it is possible, and actually it probably *is* the reason. That's why I never recommend upgrading.

But anyway, try completely removing flash, then:
```
sudo apt-get clean && sudo apt-get autoremove
```
Then reinstall flash.

---

### Post by A Traveller on 2011-04-10
Thanks for the replies beastrace91/HappyFeet.

Sorry for the VERY late reply. It looks like I forgot that I had posted this thread. Even though I've seen your replies late, the information you both have provided has been very useful. Thanks.

---

