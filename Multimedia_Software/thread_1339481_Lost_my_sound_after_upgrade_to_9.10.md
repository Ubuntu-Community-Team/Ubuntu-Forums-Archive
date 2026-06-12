---
title: "Lost my sound after upgrade to 9.10"
date: 2009-11-27
forum: Multimedia Software
---

### Post by Roger Allott on 2009-11-27
I upgraded to 9.10 this afternoon and have been having various problems since. The latest to come to my attention is the complete loss of sound.

I've read through the HowTo sticky here, but I get lost when I get to the alsamixer bit.

My alsamixer shows only one column, whereas the HowTo says there should be ten of them.

Could someone help me diagnose and fix the fault?

---

### Post by HippieDave on 2009-11-27
I had same problem.  Did a complete clean install, and still had the problem.  One issue is whether you are still running the old kernel...make sure you are running the new one.

After my clean install I followed the lengthy but detailed instructions here: [http://monespaceperso.org/blog-en/2009/10/29/upgrade-alsa-1-0-21-on-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blog-en/2009/10/29/upgrade-alsa-1-0-21-on-ubuntu-karmic-koala-9-10/)
to upgrade to the 1.0.21 version of alsa.  I bet if you search for your alsa files you are running ver. 1.0.20, which is what comes with 9.10.  upgrading to 1.0.21 did the trick.  Be sure you follow the instructions carefully and BE SURE to do the last step, which he makes sound optional but is essential

---

### Post by Roger Allott on 2009-11-28
> **HippieDave said:**
> I had same problem.  Did a complete clean install, and still had the problem.  One issue is whether you are still running the old kernel...make sure you are running the new one.
What is the old one, and what is the new one?

> **HippieDave said:**
> After my clean install I followed the lengthy but detailed instructions here: [http://monespaceperso.org/blog-en/2009/10/29/upgrade-alsa-1-0-21-on-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blog-en/2009/10/29/upgrade-alsa-1-0-21-on-ubuntu-karmic-koala-9-10/)
to upgrade to the 1.0.21 version of alsa.  I bet if you search for your alsa files you are running ver. 1.0.20, which is what comes with 9.10.  upgrading to 1.0.21 did the trick.  Be sure you follow the instructions carefully and BE SURE to do the last step, which he makes sound optional but is essential
I presume what you mean is the package alsa-utils, which is showing in my Synaptic as 1.0.20, as you suspected, but it's also saying it's the latest version.

I'm off now to read those instructions to which you linked.

---

### Post by Roger Allott on 2009-11-28
> **HippieDave said:**
> 
After my clean install I followed the lengthy but detailed instructions here: [http://monespaceperso.org/blog-en/2009/10/29/upgrade-alsa-1-0-21-on-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blog-en/2009/10/29/upgrade-alsa-1-0-21-on-ubuntu-karmic-koala-9-10/)
to upgrade to the 1.0.21 version of alsa.

OK, I've done that. FWIW, that's the first time I've compiled source code. Quite terrifying, and I'd much prefer to get a deb from an archive!

This is my output after one reboot:
```
:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
Compiled on Nov 28 2009 for kernel 2.6.31-15-generic (SMP).
```

Is that kernel the old one or the new one?

---

### Post by Roger Allott on 2009-11-28
Unfortunately, after having run alsa configure and configured my sound card and rebooted again, I'm still getting no sound.

AAAARRRGGGGGHHHHHH!!!!!

---

