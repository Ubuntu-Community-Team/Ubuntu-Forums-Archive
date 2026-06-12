---
title: "Current state of ATI v Nvidia Drivers?"
date: 2009-11-24
forum: Multimedia Software
---

### Post by Degenerate on 2009-11-24
I need to run 5 1080p monitors from one box, so I'm looking to purchase 3 low-end graphics cards. The contenders are ATI 4550HDs or Nvidia GT220s.

My chief concern is hardware acceleration of HD 1080p playback. 3D performance is a secondary consideration, as long as it's adequate for a compositing window manger (which any of these cards should be.)

Can anyone enlighten me about the recent condition of ATI v Nvidia drivers? Looking around the web, I see reports at various points over the last couple of years that ATI have made a lot of progress, but others that they still have a long way to go. Can anyone give me a November 2009 update?

Please don't reply telling me the ATI drivers suck if you're not talking about a recent experience.

---

### Post by Melcar on 2009-11-24
Well, if HD playback is your main concern, nvidia is the only option at the moment.  If you don't mind waiting and indefinite amount of time, AMD is currently working on HD acceleration for their drivers.

---

### Post by markbuntu on 2009-11-25
For multiple gpus you will need to use xinerama instead of randr and it is not so easy to get compositing working with xinerama these days since it is being deprecated. Both the nvidia and ati proprietary drivers make use of xinerama, which they supply in their drivers, for multi-gpu support.

Randr has recently regained multi-gpu support in the latest release which is too late for this round of distribution releases but should be in the next round this coming spring. 

I have not heard of any problems with using the 4550 with the latest drivers and multi-gpu support has improved greatly over the last few releases. 

You can read about the current state of accelerated HD playback on ati cards here

[http://www.phoronix.com/scan.php?page=article&item=amd_xvba_vaapi&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_xvba_vaapi&num=1)

I have no idea what nvidia is doing.

---

