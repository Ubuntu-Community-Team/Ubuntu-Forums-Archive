---
title: "Breezy Smartlink Modem"
date: 2006-02-02
forum: Networking &amp; Wireless
---

### Post by pace_tua on 2006-02-02
I managed to get my smartlink modem to work in hoary, but with breezy none of the packages I need are available. Any help would be appreciated.

Thank you.

---

### Post by towsonu2003 on 2006-02-03
check out the second link in my signature.

---

### Post by pace_tua on 2006-02-04
Thanks for the reply, but the problem is that none of the repositories have the sl-modem-* packages (this includes the universe/multiverse, backport, ect.).

So once I get somewhere with wireless internet access I'll be trying set everything up with the package directly from Smartlink.

---

### Post by towsonu2003 on 2006-02-04
it's in the multiverse (or so it says): [http://packages.ubuntu.com/breezy/misc/sl-modem-daemon](http://packages.ubuntu.com/breezy/misc/sl-modem-daemon)

if you decide to download the .deb, be careful with the dependencies and the dependencies of the dependencies etc...

---

### Post by mpvano on 2006-02-05
DO check out the wiki as other posts have suggested. It's essential to understanding what you're looking for.

One thing you said, however, caught my eye.

If you found the sl-modem packages in Hoary, but not in breezy, and that's your whole problem, it's possible that you're not set up to search all the needed repositories.

Whenever you do a new install, Ubuntu sets ONLY the minimal repositories needed for the basic installation for search by apt-get and synaptic. This is because all your old repositories are for Breezy only. You need new sources for EACH repository that contain Breezy packages, not Hoary ones. Ubuntu sets up the ones it needs for installation, but you need to review the situation and set up equivalent ones for all of   your optional repositories.

I believe that the sl-modem support packages are in the "multiverse" repositories and you need to add them to the configuration in synaptic's preferences to find them.

At least that's what I had to do to find them.

While you're at it add the "universe" as well if it's not already enabled.....

I had to do this myself to install sl-modem-daemon, which was needed to make my thinkpad T30's modem work.

hope it's this easy for you....

Mario

---

