---
title: "Shotwell database backward compatibility?"
date: 2014-07-07
forum: Multimedia Software
---

### Post by Z80A on 2014-07-07
Considering migrating a machine from L/Ubuntu 14.04 to elementaryOS, but (like others waiting for a new elementaryOS release) have some concerns about older versions of applications. This machine has quite a photo collection and Shotwell is used for managing these.

Would it be possible to move from one of the more recent Ubuntu releases e.g. 13.10 or 14.04 to elementaryOS Luna (12.04 based)? This would involve moving a Shotwell 0.18 (Ubuntu 14.04) database to a system with Shotwell 0.12.3 (Ubuntu 12.04).

Is the database structure compatible? Would this corrupt the database? I know the easy answer: Don't! Another one could be to use Yorba PPA's and upgrade. Or wait for elemenaryOS to catch up with 14.04...

Another related question on export and import: Is it possible to manage photos in one version of Shotwell, export the photos (together with nondestructive adjustments) and import these into another version of Shotwell? Can it even be done using same versions?

---

### Post by slooksterpsv on 2014-07-10
The adjustments are usually saved to the photos themselves. If you have the photos tagged and what not, that should all just port over. If there's newer features being used in the configuration that isn't available on the older version, it may recreate the config but use the tags (which are embedded into the photos). You could find a PPA for 0.18 for elementary OS. I'd wait till Freya comes out though.

---

