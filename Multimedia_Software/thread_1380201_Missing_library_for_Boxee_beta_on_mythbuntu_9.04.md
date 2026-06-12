---
title: "Missing library for Boxee beta on mythbuntu 9.04"
date: 2010-01-13
forum: Multimedia Software
---

### Post by mikearm on 2010-01-13
Hi!

I can install Boxee beta on my mythbuntu 9.04 installation, but when I try to run it, I get the following errors:

/opt/boxee$ ./run-boxee-desktop 
/opt/boxee/Boxee: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by /opt/boxee/Boxee) 
./run-boxee-desktop: 38: /opt/boxee/give_me_my_mouse_back: not found 

I get the same error if I run as root. For now, I don't care so much about the second error, but if anybody has some advice about how to resolve the first error (GLIBCXX...), I'd appreciate it. I've used Linux for years (usually gentoo), but I'm not experienced with Ubuntu. I would be surprised if the version of Boxee compiled for Ubuntu 9.04 depended on an installed library without the proper compiler version.

Note that I am using *mythbuntu*, not ubuntu itself, so this may be part of the problem, but it would also surprise me... I'm happy to just install the correct library, but where is it?? I assume I should get it from Ubuntu, or I will break something.

I've also posted to the boxee support forum, but not heard back yet (they are probably busy!)...

Also, I've got Boxee alpha running in a 32 bit chroot environment (on my 64 bit machine), so at least *some* version of Boxee runs, but I wonder if there is some conflict between the two versions.

Thanks, Mike

---

### Post by Maheriano on 2010-01-13
Looks like you're missing the package, open Synaptic and search for glib and install it.

---

### Post by mikearm on 2010-01-14
I searched under glib and it matched a lot of packages. I installed the ones that seemed reasonable (including development and debug packages), but still no luck. I suspect this may be a matter of waiting for a later version of boxee... I thought I'd check if anybody had seen this specific problem. Thanks, anyway!

---

### Post by chathamsq on 2010-01-15
Having the same problem on Ubuntu 9.04 64-bit.

---

### Post by ktmom on 2010-02-01
Boxee 64-bit runs on 9.10 only, not on 9.04.  Boxee originally had a typo on their download page that they have now fixed

---

### Post by almightybunghole on 2010-11-19
I'm getting the exact same thing on my Jaunty Myth box - it was a Mythbuntu install but now has ubuntu-desktop installed too. Tried installing most glib related packages but no beans. I'm stuck... :(

edit: mine's x86 so nothing to do with x64 incompatibility

---

