---
title: "Replacing ver 11.04 with 12.04 killed Wi-Fi"
date: 2012-12-22
forum: Networking &amp; Wireless
---

### Post by Riverglen on 2012-12-22
I recently replaced a working installation of version 11.04 with a fresh install of version 12.04 LTS.  I did this by deleting the old partition and doing a clean install from a live CD.  Everything went ok except that I've lost my Wi-Fi.  

This seems to be yet another instance of the infamous Broadcom card problem.  I've read the sticky and the wiki and based on the information contained in those sources I have done the following.

Identified the card as BCM4318 [14e4:4318] (Rev 02).

Based on that information, determined that the proper driver for the card is b43.

Have done apt-get update
          apt-get install bcmwl-kernel-source

No joy.  I have several questions in mind.  I gather from some of the relevant material I've read that I may have to also install b43-firmware-installer?  But this evidently updates the firmware on the card, which makes me concerned whether about the impact on its use under Windows XP.  The machine is set up to dual boot XP or Ubuntu.  And, since Ubuntu was working fine before the upgrade, I would not have expected to need a firmware update to get it going again now.

I got to the working version of 11.04 via a series of several 6 month version upgrades, spanning several years.  Seems to me that I had some struggles getting Wi-Fi going in the past, but don't remember the details.  And, the 11.04 live CD also doesn't work for Wi-Fi.

---

### Post by ahallubuntu on 2012-12-22
I sympathize with you.  Those Broadcom cards are such a pain in Linux!  I avoid the problem by replacing them in new laptops I acquire with Intel wireless cards when possible; those cards seem to work perfectly for me without any tweaking.  (It's fairly easy to swap a laptop wireless card unless you have an HP or Lenovo laptop, where they restrict which kinds of wireless cards you can use.)

There are lots of Broadcom threads (checked the "Sticky" at the top of this forum?).  You should be able to find a solution in one of them.  12.04 LTS is very different from 11.04 - it's a big step to the 3.2 kernel.  So it's hardly a surprise that what may have worked before no longer does.  Still frustrating that Broadcom wireless cards aren't supported automatically!!!

---

### Post by Riverglen on 2012-12-22
Well, I appreciate you sympathy. As it happens, the laptop is a fairly old HP, so swapping the card may not be an option.  And in any event, it probably isn't worth the trouble since I still have a working Ubuntu installation on my desktop machine.

Rummaging around in the "sticky" and other related old postings gets old really fast.  I very quickly get wrapped up in the details of other people's problems, which may or may not be relevant to my situation.

I did find a page in the "official?" documentation which purports to be directly relevant to my situation and was the basis for what I've already tried.  But it was also the source of the suggestion that I may need a firmware update.  I'm not going to try that unless and until someone can reassure me that it won't bollix up my Windows side.

One small correction to my original post.  The laptop is now running Windows 7, not XP.

---

### Post by bkratz on 2012-12-22
Post 14 of this thread should take care of you

[http://ubuntuforums.org/showthread.php?t=2094257&page=2&highlight=BCM4318](http://ubuntuforums.org/showthread.php?t=2094257&page=2&highlight=BCM4318)

---

### Post by Riverglen on 2012-12-22
Well, that post is another variant of the "you need to update your card firmware" train of thought.  I suspect that the recommended fix will get Ubuntu running.  But since I'm dual booting Windows and Ubuntu on this machine, I want some assurance that updating the firmware to get Ubuntu working won't have the side effect of killing Windows.

---

### Post by Pjotr123 on 2012-12-23
Firmware that you install in Linux, isn't being installed in the chips on the card. It's simply put in a folder in your Ubuntu. Usually in /etc/lib/firmware. No effect on Windows whatsoever. :)

---

### Post by Hadaka on 2012-12-23
Hi, [14e4:4318] requires the b43 driver, this should get you going.

```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modpeobe b43 
```

and ZERO effect on windows,

---

### Post by Riverglen on 2012-12-23
Thank you gentlemen for the contribution to my education and for the tip that solved the problem.  I was a little suspicious when I realized that I had probably installed the wrong driver (wl) but my level of command language competence is very low, so I wasn't sure.

And I am very glad to know that the required fix didn't require flashing a chip on the wi-fi card, which didn't make a lot of sense to me.  I really don't understand the rationale for calling loadable drivers "firmware".

But, I'm happy.

---

### Post by Hadaka on 2012-12-23
Hi, happy to hear its working for you.
firmware is the ****** to your OS software that allows for functional hardware.
please use thread tools to mark this thread SOLVED.

THANKS

---

