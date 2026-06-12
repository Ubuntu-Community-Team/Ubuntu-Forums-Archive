---
title: "aptitude safe-upgrade failure"
date: 2011-03-10
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ratcheer on 2011-03-10
This morning on my natty testing installation, which was fully updated as of yesterday, I ran "sudo aptitude update" with no problems, followed by "sudo aptitude safe-upgrade", which downloaded a bunch of stuff, then failed with the following:

```
Extracting templates from packages: 100%
dpkg: error: parsing file '/var/lib/dpkg/available' near line 16:
 missing package name
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: error: parsing file '/var/lib/dpkg/available' near line 16:
 missing package name
```This occurred immediately after the fetches completed. Any suggestions on how I should deal wit this? I retried the update and safe-upgrade, but the problem recurred.

Thanks,
Tim

---

### Post by ratcheer on 2011-03-10
Google knows: [https://answers.launchpad.net/ubuntu/+question/10265](https://answers.launchpad.net/ubuntu/+question/10265)

sudo dpkg --clear-avail

Tim

---

