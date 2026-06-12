---
title: "ACPI problem?"
date: 2011-01-07
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by icek on 2011-01-07
Hi, I'm affected by this bug : [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/77370](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/77370) 
solution proposed in comments worked fine in maverick, but does not work in natty. The reason is probably that in natty there is no /proc/acpi/fan folder... can someone tell me where is stored fan settings in natty please?

---

### Post by dino99 on 2011-01-08
this bug was reported in 2006 and is still open.
Better to google around and create your own missing file/folder.

[http://www.columbia.edu/~ariel/acpi/acpi_howto.txt](http://www.columbia.edu/~ariel/acpi/acpi_howto.txt)

---

### Post by espen77 on 2011-01-14
I am having problem getting the extra buttons on my thinkpad x200t to work. the volume up and down buttons work, but not button for rotating tablet screen, lock screen button, thinkvantage...etc. Anyone else have this issue with acpi buttons?

---

### Post by dino99 on 2011-01-15
> **espen77 said:**
> I am having problem getting the extra buttons on my thinkpad x200t to work. the volume up and down buttons work, but not button for rotating tablet screen, lock screen button, thinkvantage...etc. Anyone else have this issue with acpi buttons?

dont forget to search about "thinkpad" into synaptic: package like tpb might help you (and acpitool also)

---

### Post by Favux on 2011-01-16
Hi espen77,

linuxd00 also posted little scripts for X2001t buttons and rotation.  See:  [http://ubuntuforums.org/showthread.php?t=1656632](http://ubuntuforums.org/showthread.php?t=1656632)

---

### Post by espen77 on 2011-01-17
> **Favux said:**
> Hi espen77,

linuxd00 also posted little scripts for X2001t buttons and rotation.  See:  [http://ubuntuforums.org/showthread.php?t=1656632](http://ubuntuforums.org/showthread.php?t=1656632)

Thank you for the tip, but my problem is that i dont get any events from the buttons, not the mapping of them.

---

