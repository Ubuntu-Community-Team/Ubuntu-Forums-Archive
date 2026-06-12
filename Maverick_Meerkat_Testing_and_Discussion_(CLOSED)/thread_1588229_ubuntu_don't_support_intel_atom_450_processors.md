---
title: "ubuntu don't support intel atom 450 processors"
date: 2010-10-04
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by KristinaK on 2010-10-04
During the Maverick development cycle, support for the intel_idle driver was included in the Maverick kernel. The intent of intel_idle is to allow Linux to take better advantage of Intel hardware and make Linux more immune to ACPI BIOS bugs and shorcomings of the ACPI implementation itself. This unfortunately appears to have an adverse affect on systems with Intel Atom N450 processors rendering them incapable of booting.

---

### Post by kansasnoob on 2010-10-04
> **KristinaK said:**
> During the Maverick development cycle, support for the intel_idle driver was included in the Maverick kernel. The intent of intel_idle is to allow Linux to take better advantage of Intel hardware and make Linux more immune to ACPI BIOS bugs and shorcomings of the ACPI implementation itself. This unfortunately appears to have an adverse affect on systems with Intel Atom N450 processors rendering them incapable of booting.

What exactly happens during boot?

We need more info :)

---

### Post by 23meg on 2010-10-04
Sounds like [bug #634702]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/634702").

---

