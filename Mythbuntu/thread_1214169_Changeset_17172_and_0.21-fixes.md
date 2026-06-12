---
title: "Changeset 17172 and 0.21-fixes"
date: 2009-07-15
forum: Mythbuntu
---

### Post by Observer64 on 2009-07-15
I run the 0.21-fixes weekly builds package from MythBuntu. I have my Motorola STB setup with a firewire connection for the unencrypted channels, and an S-VIDEO feed to a PVR-150 for the encrypted channels. I also have the analog tuner on the PVR-150 configured. The patch described here:

[http://cvs.mythtv.org/trac/changeset/17172](http://cvs.mythtv.org/trac/changeset/17172)

is supposed to resolve a case where the firewire and S-Video feeds are in the same input group. If the analog tuner is busy, then the backend prevents a recording from starting on the firewire feed by erroneously marking the firewire feed "busy." Do note that the analog tuner is not included in the input group.

My request:

Please integrate this patch into the weekly builds of 0.21-fixes. I have already posted a request to the mythtv-users and -dev mailing lists to merge it into the source tree.

-Ray

---

