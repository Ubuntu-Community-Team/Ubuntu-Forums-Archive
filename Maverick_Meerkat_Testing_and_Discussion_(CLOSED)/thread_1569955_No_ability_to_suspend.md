---
title: "No ability to suspend?"
date: 2010-09-07
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Arla on 2010-09-07
Has this option been removed, or changed so I have to enable it somewhere? 

Currently I'm using the 2.6.35-19 kernel, I notice in Synaptic there is a -20 version of the kernel but it doesn't appear to have been installed (not entirely sure why)

---

### Post by teh603 on 2010-09-07
More info please? I can suspend/resume and hibernate/resume just fine on a Dell Inspiron 1564.

---

### Post by Arla on 2010-09-07
> **teh603 said:**
> More info please? I can suspend/resume and hibernate/resume just fine on a Dell Inspiron 1564.

Well did a bunch of google searching and found that apparently upgrading to Maverick had either removed, or nullified my ability to do this, installing acpi and acpi-support fixed the problem, although since I was able to in Lucid I'm curious why these would have either been removed by an upgrade, or now are required, but weren't before.

---

### Post by teh603 on 2010-09-10
> **Arla said:**
> Well did a bunch of google searching and found that apparently upgrading to Maverick had either removed, or nullified my ability to do this, installing acpi and acpi-support fixed the problem, although since I was able to in Lucid I'm curious why these would have either been removed by an upgrade, or now are required, but weren't before.Have you tried re-downloading the iso and making a fresh CD to see if those packages are back in place?

The main thing I can think of is that you might've done a dist-upgrade (you said you 'upgraded' instead of 'installed') at a time when the acpi packages were witheld. Thus you didn't get them, because they weren't available, while the old ones might've been removed for the upgrade to be replaced by the unavailable Maverick ones.

---

