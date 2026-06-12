---
title: "kernel update killed nvdia drivers (no screen)"
date: 2005-12-31
forum: Multimedia &amp; Video
---

### Post by zambizzi on 2005-12-31
So, I'm looking at using Ubuntu having used Gentoo for the last two years, quite happily (until recently.)

I like it so far but I just managed to hose my desktop completely.

I installed 5.10 and my monitor would not work (big ugly distorted screen w/ lines through it.)  I did "sudo apt-get install nvidia-glx" and made the appropriate changes to xorg.conf to use the nvidia driver.  My monitor worked great from that point forward and all was good...almost.

I have a HT CPU so I installed the same version of the kernel I was using only w/ SMP...it asked me to reboot...so I did.

Now X won't start...it fails w/ the error message telling me it can't find the "nvidia" module...and that was to be expected...the module would need to be recompiled w/ a new kernel in Gentoo as well.

So...trying to figure out how to do this the "ubuntu way" has yielded no successes as of yet.  I tried using apt-get to 'remove' nvidia-glx and then 'install' it again...but it didn't bring my desktop back.

What can I do?

Thanks!

---

### Post by NaplesBill on 2005-12-31
You need to load the linux-restricted-modules that match your new kernel.  There are two, one for older nvidia cards and one for newer.  Just read the description.

---

### Post by zambizzi on 2005-12-31
[QUOTE=NaplesBill]You need to load the linux-restricted-modules that match your new kernel.  There are two, one for older nvidia cards and one for newer.  Just read the description.[/QUOTE]

That did it!  Thanks!

---

