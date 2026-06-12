---
title: "Maverick upgrade does not remove leftover packages"
date: 2010-09-13
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by ptn107 on 2010-09-13
Upgrading 10.04 to the latest maverick daily (9/12, amd64) leaves the following packages installed.  Why doesn't the upgrade remove these when it says it's "cleaning up."  There are 121 in total.

[_http://ubuntu.pastebin.com/850KS3rZ_]("http://ubuntu.pastebin.com/850KS3rZ")

---

### Post by ptn107 on 2010-09-14
bump

---

### Post by ankspo71 on 2010-09-15
Hi,
I can only guess the reason for this, so here goes...

Updates to some packages are not always available in pre-releases of Ubuntu because the packages are waiting for dependencies to be resolved. See the sticky post in this Maverick forum about "Partial Upgrades" and you will start to see what I mean.

So I think if a person upgrades from an older release of Ubuntu to a pre-release of Ubuntu, they take a chance of upgrading during one of these Partial Upgrade periods (without being made aware of it), causing Ubuntu to upgrade successfully, but also it leaves behind some packages from the previous version to be used until the dependency issues can be resolved. I'm thinking that these remaining packages will be taken care of as soon as their updates become available for them.

---

### Post by seeker5528 on 2010-09-15
> **ptn107 said:**
> Why doesn't the upgrade remove these when it says it's "cleaning up."  There are 121 in total.

[_http://ubuntu.pastebin.com/850KS3rZ_]("http://ubuntu.pastebin.com/850KS3rZ")

It's pretty common for things to get uninstalled during a distribution upgrade that you might actually want to keep. Especially if you are upgrading during the development cycle where you are more likely to have dependency/packaging issues.

Having some extra configurations around isn't really going to matter much to most people, but people that have to re-install things that got removed during the upgrade probably like having the ones with residual configurations being listed so they can just go down the list and select the ones they want to re-install.

If you are talking about obsolete packages that don't get removed on the other hand. The packaging system doesn't know, and so update-manager doesn't know what you have installed that it doesn't now about that may still be using those things, so best policy, if there is not a conflict that requires it's removal, keep it. 

Later, Seeker

---

