---
title: "Partial Upgrades"
date: 2010-09-23
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Asmodai on 2010-09-23
Although I read the sticky about partial upgrades, I'm still not sure under which circumstances a partial upgrade is offered.

Take an example: Recently the package libntfs-3g79 was added to the repos, the old ntfs-3g package is named libntfs-3g75. Now a partial upgrade is offered for the package ntfs-3g. Why though? To quote the sticky: "In its normal operating mode, Update Manager will not offer to remove packages". However, when I mark ntfs-3g for upgrade in synaptic, it requires installation of libntfs-3g79 (that is expected), however it does not offer to remove the package libntfs-3g75, as I would have expected.
Why is such an upgrade considered risky, so that user intervention is needed?

---

### Post by arubislander on 2010-09-23
Say you had package A and B installed where B is dependent on A.
Say later on you decided to install package C that is also dependent on A.

Now an update comes along for B in which its dependency has been altered in that it needs A to be removed to satify its dependency. But this would mean that package C would also need to be removed. But what if you depended on package C for doing some invaluable work. In this case you would be quite annoyed if the update to package B automatically removed your very important package C in the process without giving you a heads up.

---

### Post by seeker5528 on 2010-09-23
> **Asmodai said:**
> Although I read the sticky about partial upgrades, I'm still not sure under which circumstances a partial upgrade is offered.

I think the partial upgrade will be offered in any situation where something has been selected that would result in conflict if it were allowed to proceed as is. I don't run update-manager that often so it has been a while since I have seen how it presents these cases. 

> Take an example: Recently the package libntfs-3g79 was added to the repos, the old ntfs-3g package is named libntfs-3g75. Now a partial upgrade is offered for the package ntfs-3g. Why though?

The libntfs-3g packages are versioned libraries (libraries that include their version in the file name), installing the newer libntfs-3g should not have an effect on any other package, if packages make it into the archive that depend on a newer libntfs-3g before that version makes it into the archive, that's another story.

>  To quote the sticky: "In its normal operating mode, Update Manager will not offer to remove packages". However, when I mark ntfs-3g for upgrade in synaptic, it requires installation of libntfs-3g79 (that is expected), however it does not offer to remove the package libntfs-3g75, as I would have expected.

Packages don't get removed if there is no conflict, libntfs-3g75 and libntfs-3g79 are different packages so the old one isn't replaced and they provide versioned libraries so there is no conflict.

One reason I can think of for having the newer package conflict with the older, is if it is thought problems might result if some software uses the newer library and other software uses the older library. But since the installation of libntfs-3g79 didn't force the removal of libntfs-3g75, that doesn't seem to be the case here.

Later, Seeker

---

