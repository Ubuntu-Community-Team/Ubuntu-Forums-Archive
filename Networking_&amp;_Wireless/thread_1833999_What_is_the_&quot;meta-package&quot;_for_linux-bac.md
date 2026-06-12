---
title: "What is the &quot;meta-package&quot; for linux-backports?"
date: 2011-08-26
forum: Networking &amp; Wireless
---

### Post by dryphi on 2011-08-26
I'm trying to install compat-wireless on Natty using an Intel 3945ABG wireless card. There are many pages explaining how to do this via the terminal, such as [COLOR="Blue"][this one]("http://www.aircrack-ng.org/doku.php?id=compat-wireless")[/COLOR], but I would prefer to use Synaptic to be sure to receive updates and what-not.

Anyway, I think I'd like to install this package:
linux-backports-modules-cw-2.6.39-2.6.38-11-generic

Which contains this description:
[INDENT][SIZE="1"]This package contains compat-wireless modules supplied by Ubuntu for Linux
kernel 2.6.38 on x86/x86_64.

You likely do not want to install this package directly. [B]Instead, install
the linux-backports-modules-cw-2.6.39-generic meta-package[/B], which will ensure
that upgrades work correctly, and that supporting packages are also installed.[/SIZE][/INDENT]
(A very vague explanation IMO)


#end_background_explanation, now on to...
MY QUESTION:
What, exactly, IS the "linux-backports-modules-cw-2.6.39-generic meta-package"?? Where do I find it? I can't find anything in Synaptic called "meta" relating to the wireless backports. Why is synaptic instructing me to install a package, without telling me the NAME of that package, or how to install it?

---

### Post by chili555 on 2011-08-26
It is a package that makes sure when a later kernel version than 2.6.38-11 is installed...> linux-backports-modules-cw-2.6.39-[COLOR="Red"]2.6.38-11[/COLOR]-generic
...that the later version of cw is installed, too. The real name of the meta package is linux-backports-modules-cw-2.6.39-natty-generic. This empty package allows people to keep their backported wireless modules up-to-date when upgrading their Linux kernel.

What is wrong with the in-kernel iwl3945?

---

### Post by dryphi on 2011-08-26
> **chili555 said:**
> The real name of the meta package is linux-backports-modules-cw-2.6.39-natty-generic. This empty package allows people to keep their backported wireless modules up-to-date when upgrading their Linux kernel.
Got it, thanks. I assumed that might be what I wanted, but without the "natty" in the description for the other, I wasn't sure.

> **chili555 said:**
> What is wrong with the in-kernel iwl3945?
To be honest, I'm not sure, exactly. The wireless works fine on my system. I'm trying to get the aircrack-ng suite working, and I get the "channel negative one" error. I've been told that I need to install compat-wireless with the maxim patch to fix it, like what was done here:
[http://blog.macuyiko.com/2010/11/ubuntu-1010-fixed-channel-mon0-1.html](http://blog.macuyiko.com/2010/11/ubuntu-1010-fixed-channel-mon0-1.html)
Apparently this is a well-known error that has yet to be patched in the kernel / driver / whatever?

---

### Post by chili555 on 2011-08-26
The package you install from the repos cannot be patched; it's pre-built already for Ubuntu. You'll need to download, patch and then compile the tar.gz as explained in the blog post. Post back if you get stuck. I'll check in tomorrow.

---

### Post by dryphi on 2011-08-26
Darn... I thought that might be the case, as well :)
Patching / installing now.
Thanks again for clearing a few things up.

---

### Post by dryphi on 2011-08-27
Installed and everything seems to be working fine.

---

