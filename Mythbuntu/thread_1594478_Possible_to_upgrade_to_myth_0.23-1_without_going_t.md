---
title: "Possible to upgrade to myth 0.23-1 without going to 10.10"
date: 2010-10-12
forum: Mythbuntu
---

### Post by bcg30506 on 2010-10-12
I have a nicely working 10.04 system running 0.23-fixes but there are some fixes in 0.23.1 I'd like to pick up in MythTV but without the risk of changing the underlying OS to 10.10 as kernel updates and driver updates can cause new instability issues.

Is there a way to do this?  Is the official Mythtv 0.23.1 release available now in the 10.04 repositories somewhere?

---

### Post by ian dobson on 2010-10-12
Hi,

Just enable the autobuilds (See the sticky at the top of this forum)). I've been running my frontend and backend with 10.04 and autobuild (23.1-fixes) for afew months now without any problems.

Regards
Ian Dobson

---

### Post by rhpot1991 on 2010-10-12
Linky: [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)

---

### Post by itlarson on 2010-10-12
Do you have to go to this page and download the .deb? Or can you just click the checkbox in mythbuntu control center, select .23.1 from the dropbox, then click apply?

---

### Post by rhpot1991 on 2010-10-12
> **itlarson said:**
> Do you have to go to this page and download the .deb? Or can you just click the checkbox in mythbuntu control center, select .23.1 from the dropbox, then click apply?

Sounds like you got the deb at some point, thats how that tab gets created in MCC.  You can do it right from in MCC.

---

### Post by bcg30506 on 2010-10-12
Thanks.  Any negatives to doing this?  How stable are the auto-builds.  This is our primary living room DVR so WAF is important.  I do not want to run testing code on this box that would cause problems for daily use.

---

### Post by tgm4883 on 2010-10-12
auto-builds are built from the upstream "fixes" branch, so arguably, you are getting more stable builds.

---

### Post by rhpot1991 on 2010-10-12
It is very low risk, and normally fixes many issues that you may have otherwise.  I would recommend using it unless you have a reason not to.

---

### Post by bcg30506 on 2010-10-12
I have now moved my combo BE/FE system to 0.23.1 using the auto builds and all seems to work after a reboot.  Before rebooting, my remote control did not work.  So far, so good.  Thanks!

However, I have other remote frontends.  The ubuntu ones I think I can do the same way by installing the deb for the auto builds and updating with the Update Manager.  But my Mac OS/X ones fail to start now as it seems MythTV changed the database protocol version yet again.  Arg!

I found an online source for a dmg file with a frontend for the fixes build from 10/7 but it crashes as soon as I run it.  Why does every point release change the DB protocol?  Shouldn't this be reserved for "major" builds like 23->24?

---

### Post by rhpot1991 on 2010-10-12
> **bcg30506 said:**
> I have now moved my combo BE/FE system to 0.23.1 using the auto builds and all seems to work after a reboot.  Before rebooting, my remote control did not work.  So far, so good.  Thanks!

However, I have other remote frontends.  The ubuntu ones I think I can do the same way by installing the deb for the auto builds and updating with the Update Manager.  But my Mac OS/X ones fail to start now as it seems MythTV changed the database protocol version yet again.  Arg!

I found an online source for a dmg file with a frontend for the fixes build from 10/7 but it crashes as soon as I run it.  Why does every point release change the DB protocol?  Shouldn't this be reserved for "major" builds like 23->24?

That is why it was a point release.

---

### Post by tgm4883 on 2010-10-12
> **bcg30506 said:**
> I have now moved my combo BE/FE system to 0.23.1 using the auto builds and all seems to work after a reboot.  Before rebooting, my remote control did not work.  So far, so good.  Thanks!

However, I have other remote frontends.  The ubuntu ones I think I can do the same way by installing the deb for the auto builds and updating with the Update Manager.  But my Mac OS/X ones fail to start now as it seems MythTV changed the database protocol version yet again.  Arg!

I found an online source for a dmg file with a frontend for the fixes build from 10/7 but it crashes as soon as I run it.  Why does every point release change the DB protocol?  Shouldn't this be reserved for "major" builds like 23->24?

No. Point releases are for changes such as protocol or database schema changes where the two versions are no longer compatible with each other (0.23.0 isn't compatible with 0.23.1). FWIW, it was a mythtv protocol version change, not a db schema change between 0.23.0 and 0.23.1. Major releases are for new features, but will likely also include mythtv protocol and db bumps. 

The fact that there was a mythtv protocol change is precisely why there is a 0.23.1 version.

---

### Post by bcg30506 on 2010-10-12
> **tgm4883 said:**
> No. Point releases are for changes such as protocol or database schema changes where the two versions are no longer compatible with each other (0.23.0 isn't compatible with 0.23.1). FWIW, it was a mythtv protocol version change, not a db schema change between 0.23.0 and 0.23.1. Major releases are for new features, but will likely also include mythtv protocol and db bumps. 

The fact that there was a mythtv protocol change is precisely why there is a 0.23.1 version.

Thanks for the clarification. :)

---

