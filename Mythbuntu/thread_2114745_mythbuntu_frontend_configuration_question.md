---
title: "mythbuntu frontend configuration question"
date: 2013-02-10
forum: Mythbuntu
---

### Post by Old Jimma on 2013-02-10
Hi Myth Community!

I'm running Myth on a trusty 12.04 machine (Unity Desktop), as a frontend and backend.

I bought new hardware to build a frontend, and have a few questions...

I read the info about the Mythbuntu Control Center at [http://www.mythbuntu.org/]("http://www.mythbuntu.org/").

I'm not exactly sure how to interpret the pargaraph describing the Mythbuntu Control Center.

Does it mean that if I use the Mythbuntu Control Center to configure my new machine as a Mythbuntu frontend, it will somehow query me or find out where the TV recordings are storeed on my trusty 12.04 machine and do all the mounts, fstab, ntfs, etc configuration for me?

[COLOR="Red"]***_That seems too good to be true! Is that correct??_***[/COLOR]

Thanks,
Old Jimma from the Old Country

:popcorn:

---

### Post by wildmanne39 on 2013-02-10
*Thread moved to **Mythbuntu**.*

---

### Post by AlecJ on 2013-02-11
> **Old Jimma said:**
> Hi Myth Community!

I'm running Myth on a trusty 12.04 machine (Unity Desktop), as a frontend and backend.

I bought new hardware to build a frontend, and have a few questions...

I read the info about the Mythbuntu Control Center at [http://www.mythbuntu.org/](http://www.mythbuntu.org/).

I'm not exactly sure how to interpret the pargaraph describing the Mythbuntu Control Center.

Does it mean that if I use the Mythbuntu Control Center to configure my new machine as a Mythbuntu frontend, it will somehow query me or find out where the TV recordings are storeed on my trusty 12.04 machine and do all the mounts, fstab, ntfs, etc configuration for me?

[COLOR=Red]***_That seems too good to be true! Is that correct??_***[/COLOR]

Thanks,
Old Jimma from the Old Country

:popcorn:

Yes
As all the directories are set in the backend Sorage Directories, a remote frontend just looks at the backend, so video folder, music folder, recordings are streamed over the network

---

### Post by nickrout on 2013-02-11
<pedantmode=on>Actually the frontend looks at the database (which may or may not be on the backend), the database tells it where to find recordings etc.</pedantmode>

---

### Post by Old Jimma on 2013-02-26
Please see solution at: [http://ubuntuforums.org/showthread.php?t=2119332]("http://ubuntuforums.org/showthread.php?t=2119332")

---

