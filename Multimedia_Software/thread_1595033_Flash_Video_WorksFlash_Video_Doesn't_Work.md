---
title: "Flash Video Works/Flash Video Doesn't Work"
date: 2010-10-12
forum: Multimedia Software
---

### Post by neu5eeCh on 2010-10-12
Even though I'm not looking for help, thought I'd post this for the next sap.

Seems that FOSS really doesn't like the Daily Show (my first post at Ubuntu Forums was a rant about this). Either that or the Daily Show doesn't like FOSS.:rolleyes:

Anyway, after upgrading to 10.10 from 10.04, I could watch Youtube, but suddenly couldn't watch the Daily Show at HuffPost (and NBC or CNN, etc...can't remember which...).

I spent the afternoon trying to sort this out (including a **complete** reinstall of FF).

**Solution:** It seems that the upgrade installs Shockwave Flash. Even though I had Adobe Flash installed, having SWF killed its functionality. Uninstall SWF and everything will work again. Sorry FOSS...

---

### Post by sswords on 2010-12-08
Hi VTPoet,

Could you say any more about how you solved this problem?  I have a new 64-bit Ubuntu 10.10 install and it seems no matter what I do, when I go to the Daily Show's full episode page, I get the message:

Error loading stylesheet. RSL [http://media.mtvnservices.com/globa6l/flex/rsl/framework_3.2.0.3958.swz](http://media.mtvnservices.com/globa6l/flex/rsl/framework_3.2.0.3958.swz) failed to load. Error #2046

I've tried various different flavors of Flash (32-bit with nspluginwrapper, 64-bit without), each of which works on (for example) YouTube but not thedailyshow.com.  Seems like I've tried every suggestion on this and other forums and this is always the outcome.  The only thing I haven't tried is running Firefox in a 32-bit chroot.

Any ideas?

---

### Post by dBuster on 2011-12-04
Would like to revive this as I am getting these RSL errors left and right!!!  Mainly error 2046 and 2032...

---

