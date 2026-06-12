---
title: "Setting &quot;the PKG_CONFIG_PATH environment variable&quot;?"
date: 2011-01-21
forum: Networking &amp; Wireless
---

### Post by Mr. ViC on 2011-01-21
Hi guys.

So, I'm following this tutorial:

```
[http://www.danets.com/turbotenna/LinuxPatchDriverSetup.php](http://www.danets.com/turbotenna/LinuxPatchDriverSetup.php)
```I'm in here:

"5. Upgrading the package "IW""

In this step:

"sudo make"

But it gives me this error:

"Makefile:34: *** Cannot find development files for any supported version of libnl.  Stop."

Ok. Now, the drivers folder has a readme. And inside, it says this:

> To build iw, just enter 'make'. If that fails, set the
PKG_CONFIG_PATH environment variable to allow the Makefile
to find libnl.

How do I set that PKG thing?

Thanks in advance!

---

### Post by chili555 on 2011-01-21
I don't think you can show it how to find what you probably don't have. Please open Synaptic and see if you have installed libnl-***dev***. Did you carefully follow this step?> sudo apt-get install linux-headers-$(uname -r) build-essential make patch gettext gcc python-psyco autoconf subversion tcl8.5 libssl-dev libnl1 [COLOR="Red"]libnl-dev[/COLOR]I tried the 'make' process and it works fine for me.

---

### Post by Mr. ViC on 2011-01-21
Thank you! Got some error with that, but installed with Synaptic and works fine.

---

