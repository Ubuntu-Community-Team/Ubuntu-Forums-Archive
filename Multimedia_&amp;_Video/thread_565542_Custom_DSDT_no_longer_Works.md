---
title: "Custom DSDT no longer Works"
date: 2007-10-02
forum: Multimedia &amp; Video
---

### Post by gene6482 on 2007-10-02
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have upgraded to Gutsy and found that my custom DSDT file that I used to enable sound (Toshiba P105-S6192) no longer works.  It appears to load, but no sound comes out.  If I set acpi=off, the sound does work.  The DSDT fix worked with both edgy and feisty.  I noticed an open bug report, but was wondering if anyone had any workarounds, or a timeframe.

Thanks in advance,
Gene

---

### Post by gene6482 on 2007-10-03
bump

---

### Post by chamiltonj on 2007-11-10
bump as well...

I have a P105-S6227 and I was using the same custom DSDT fix.  I hope someone has some idea.

---

### Post by nwheavyw8 on 2007-11-12
Bump

I'm having the same problem here.  The fixed DSDT no longer provides sound.  I followed the guide that tells how to compile and install the new alsa drivers to no avail.  It works fine with DSDT=off.

---

### Post by gene6482 on 2007-11-12
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I found an open bug report for the issue.

---

### Post by Herminator on 2007-11-13
Same here P105 - 9722 back to fiesty & XP boo hoo Gusty:(

---

### Post by gene6482 on 2007-11-14
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				There is a custom kernel fix posted at the bug report which will get your sound working with a gutsy kernel.  Just follow the instructions there and you're good to go!!!!

---

