---
title: "Mythbuntu 11.10 and irqpoll"
date: 2011-10-26
forum: Mythbuntu
---

### Post by ian dobson on 2011-10-26
Hi All,

Just as a warning/heads up if you need the irqpoll option to get your PCI tuners working, then don't upgrade to 11.10. There is a bug/regression in all kernels >.38 that causes the irqpoll hack to stop working.

After upgrading to 11.10 my system ran OK for 2 days before I started getting i2c errors from both PCI tuners. I've had this problem before and adding irqpoll to the kernel commandline parameter fixed to problem (pre .39 kernels)

With abit of hacking/screwing about I've managed to get a 2.6.38 kernel up and running, using a 11.10 user space, but it's abit of a hack.

So, you've been warned. Kernel 3.0 brakes irqpoll.

Regards
Ian Dobson

---

### Post by ian dobson on 2011-10-30
Anyone?

I've googled abit and some across this:-
[https://lkml.org/lkml/2011/10/19/405](https://lkml.org/lkml/2011/10/19/405)

But it looks as if it's being ignored!

And here's the ubuntu bug
[https://bugs.launchpad.net/linux/+bug/855199](https://bugs.launchpad.net/linux/+bug/855199)

Seeing that this bug seems to be hitting several distros it must be a upstream bug (kernel bug).

What's the best way to go forward on this?

Regards
Ian Dobson

---

### Post by nickrout on 2011-10-30
Looks like the way forward is to go back to a kernel that works for you.

---

### Post by ian dobson on 2011-10-30
> **nickrout said:**
> Looks like the way forward is to go back to a kernel that works for you.

Hi, done that. It would be nice to get a 3.x kernel up and running due to security updates/there are some module updates in the 3.x kernel series that I've backported into the 11.04 kernels, but it's a pain in the butt to recompile on every update.

Regards
Ian Dobson

---

### Post by Edward D. on 2011-10-31
Hi -

I agree with you, Ian.

I filed the bug on Launchpad.  bugzilla.kernel.org is still down; it's too bad there's no central upstream point right now, as the versions with the regression are just starting to come out from the big distros.  

I'm still working away at the bug, and updating the report.  I expect to post to LKML again soon.  It make take multiple tries, but I think this can get attention.

Ed

---

### Post by Edward D. on 2011-10-31
I added Mythbuntu to the list of affected projects.  

Anyone seeing the loss of irqpoll and irqfixup, can go the bug report (linked above), and add to the number of users affected.  Maybe we'll get a little strength-in-numbers benefit - 

E

---

### Post by nickrout on 2011-10-31
Can't see your link above.

---

### Post by ian dobson on 2011-10-31
> **nickrout said:**
> Can't see your link above.

I think he means my second post.

Looking abit more I've found the following:-
[http://us.generation-nt.com/answer/problem-ide-cs-help-204264831.html#r](http://us.generation-nt.com/answer/problem-ide-cs-help-204264831.html#r)
[http://us.generation-nt.com/kinds-irq-16-nobody-cared-sandy-bridge-asus-p8h67-mb-multiple-drivers-help-203919671.html](http://us.generation-nt.com/kinds-irq-16-nobody-cared-sandy-bridge-asus-p8h67-mb-multiple-drivers-help-203919671.html)

So it looks alot like an upstream bug in the irq routing code. On another box that I have that needs irqpoll to boot, doesn't boot kernels > 0.38 (Plain kernel.org kernel). This box is a production box that I can't really play with that much (I have a 1 day service/maintance window every 6-7 weeks).

Edward it's not really that heavy handed to add all ubuntu versions that are effected by the bug. I think it's better that having 100's or bug reports for the same error.

Regards
Ian Dobson

---

### Post by Edward D. on 2011-11-01
Hi Guys -

> **ian dobson said:**
> I think he means my second post.


That's right, excuse me.  The link, anyway, is:

  [https://bugs.launchpad.net/linux/+bug/855199](https://bugs.launchpad.net/linux/+bug/855199)

- my bug report to Ubuntu.

And I think I found the problem: just one line, a test that checked for 'equal to,' when it wanted 'not equal'.  I've posted a patch now, to LKML. Here it is, if you want to see whether it fixes the regression for you, too:

```

diff --git a/kernel/irq/spurious.c b/kernel/irq/spurious.c
index aa57d5d..b5f4742 100644
--- a/kernel/irq/spurious.c
+++ b/kernel/irq/spurious.c
@@ -115,7 +115,7 @@ static int misrouted_irq(int irq)
        struct irq_desc *desc;
        int i, ok = 0;
 
-       if (atomic_inc_return(&irq_poll_active) == 1)
+       if (atomic_inc_return(&irq_poll_active) != 1)
                goto out;
 
        irq_poll_cpu = smp_processor_id();


```

---

### Post by ian dobson on 2011-11-02
Hi,

I must admit looking at the git commit the = / != did look abit strange, but without understanding the context of the change I wasn't really sure.

Do you have a link to you email ([https://lkml.org)?](https://lkml.org)?) I had a quick look and couldn't find anything this morning.

Regards
Ian Dobson

---

### Post by Edward D. on 2011-11-02
[https://lkml.org/lkml/2011/11/1/267](https://lkml.org/lkml/2011/11/1/267)

I linked that in Launchpad, I'm trying to collect my info there.

The maintainer has agreed to it, now.

I hope it's all over.  But...I may, unfortunately, have one machine where that patch doesn't help.  Only sometimes!  I have to take a closer look at its behavior.

If you get a chance to post, on the Launchpad report, whether the one-character patch, eliminates your errors, that would be great.  Thanks!

---

### Post by ian dobson on 2011-11-03
Hi,

I'll see what I can do at the weekend. It may take abit of time before I say if the patch fixes the problem, as it takes 2-3days for the tuners to die with i2c errors/interrupt but nobody cared.

Regards
Ian Dobson

---

### Post by ian dobson on 2011-11-04
Hi Edward D.,

Just to let you know I've just compiled an ubuntu kernel (from git://kernel.ubuntu.com/ubuntu/ubuntu-oneiric.git branch Ubuntu-3.0.0-13.21), including your patch.

It'll take afew days for me to say if it works, as it can take several days nefore the irqpoll/i2c errors appear. 

Regards
Ian Dobson

---

### Post by ian dobson on 2011-11-11
Hi,

For information I've been running a patched kernel (with the patch from Edward D.) for 7 days now without any problens, so I'd say the problem is solved. I just need to wait until it makes it upstream/into the ubuntu kernels.

Regards
Ian Dobson

---

