---
title: "ABI naming for Ubuntu kernels should reflect RC status."
date: 2010-07-26
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Starks on 2010-07-26
2.6.35-rc6-11 would be far more informative and denote prerelease status.

---

### Post by ranch hand on 2010-07-27
> **Starks said:**
> 2.6.35-rc6-11 would be far more informative and denote prerelease status.
ABI = All Bogus Information?  Never heard of it.

---

### Post by psyke83 on 2010-07-27
> **Starks said:**
> 2.6.35-rc6-11 would be far more informative and denote prerelease status.

I can think of a few reasons why this is a bad idea.


[LIST]
[*]The Ubuntu kernel source has quite a lot of modifications compared to the vanilla releases. In many instances an Ubuntu kernel will contain several patches backported from later kernel releases (which is not likely in the specific case of an RC kernel, but it serves to illustrate the potential diversity from vanilla sources).
[*]Bumping from 2.6.35-rc6-11 to 2.6.35-12 (if, hypothetically, rc6 was to be the last release candidate), the newer kernel would  be considered a version downgrade to the packaging system (since the  ASCII decimal value of "r" is 114 compared to "1", which is 49).
[*]Kernels based on release candidate code are only used during the development phase. Testers should *always *assume that with each bump to the Ubuntu kernel version, compatibility with binary blobs and out of tree kernel modules may be at risk.
[/LIST]

---

### Post by Reiger on 2010-07-27
> **ranch hand said:**
> ABI = All Bogus Information?  Never heard of it.

API = [Application Programming Interface]("http://en.wikipedia.org/wiki/Application_programming_interface"). What you call the code in your program.
ABI = [Application Binary Interface]("http://en.wikipedia.org/wiki/Application_binary_interface"). This is how the code (and data) is laid out in memory, this is about where code/data is in your executable (and what some constants are).

If either changes it means some code compiled for a previous version of your program (in casu: Linux kernel) may no longer continue to work.

---

### Post by ranch hand on 2010-07-27
> **Reiger said:**
> API = [Application Programming Interface]("http://en.wikipedia.org/wiki/Application_programming_interface"). What you call the code in your program.
ABI = [Application Binary Interface]("http://en.wikipedia.org/wiki/Application_binary_interface"). This is how the code (and data) is laid out in memory, this is about where code/data is in your executable (and what some constants are).

If either changes it means some code compiled for a previous version of your program (in casu: Linux kernel) may no longer continue to work.
Well, we live and learn.  Even us grumpy geezers.

Thank you a bunch for the education.

---

### Post by seeker5528 on 2010-07-28
> **Starks said:**
> 2.6.35-rc6-11 would be far more informative and denote prerelease status.

For the most part, the ABI number is only intended to reflect when there has been a change that will require modules to be rebuilt

There is a better mechanisim to signify what the alpha/beta/rc status is as part of the version number.

>  The solution is to use a version like 0.99+1.0rc2-0joe1 which uses a lower version than 1.0 (0.99) and joins the release candidate version with a plus sign. This way the final version is greater than the previous one: 0.99+1.0rc2-0joe1 < 1.0-0joe1. 

It's a development cycle, so I don't really think there is any need for such a thing, it's not like once the actual release occurs and gets incorporrated any part of the package name/abi/version scheme includes anything to indicate which tiny release of the kernel is included anyway relative to the upstream versioning 'major.minor.teeny.tiny'. 

Later, Seeker

---

