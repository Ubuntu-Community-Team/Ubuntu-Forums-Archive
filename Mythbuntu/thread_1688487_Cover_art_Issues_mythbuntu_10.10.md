---
title: "Cover art Issues mythbuntu 10.10"
date: 2011-02-15
forum: Mythbuntu
---

### Post by josh1988 on 2011-02-15
Ok,
So here is the problem now I have setup my system added all my movies scanned for cover art which worked perfectly. After a few restart all my cover art vanished and was replaced with blank images. All the plot information remained for movies. I have been searching for a solution the past few weeks but I have come up empty handed so far.

Any help in resolving this issue would be greatly appreciated

---

### Post by thatguruguy on 2011-02-15
> **josh1988 said:**
> Ok,
So here is the problem now I have setup my system added all my movies scanned for cover art which worked perfectly. After a few restart all my cover art vanished and was replaced with blank images. All the plot information remained for movies. I have been searching for a solution the past few weeks but I have come up empty handed so far.

Any help in resolving this issue would be greatly appreciated

I had that happen to a few of my videos. Resetting the metadata worked for most. In one particular case, it was pointing to a blank image (a .jpg file which was 0 bytes). I deleted the blank jpg, reset the metadata and had myth retrieve the metadata again, and it was fixed.

---

### Post by nickrout on 2011-02-15
Quite likely you are in browse mode, that doesn't keep the metadata, because by it's nature browse mode is transient (it works by parsing the folder and presenting what is on the disk, rather than what is in the database.

Get out of browse mode (menu|disable file browse mode) them scan (menu|scan for changes)

By the way, telling us you are in mythbuntu 10.10 is less halpful than the mythtv version number (0.23, 0.23.1, 0.24 etc)

---

### Post by josh1988 on 2011-02-19
Thank you very much nickrout, That is what the problem was so now i have all my covers restored and actually remaining. So thank you again.

---

