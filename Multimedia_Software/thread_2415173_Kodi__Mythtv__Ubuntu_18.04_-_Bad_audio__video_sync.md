---
title: "Kodi / Mythtv / Ubuntu 18.04 - Bad audio / video sync"
date: 2019-03-21
forum: Multimedia Software
---

### Post by Tadaen_Sylvermane on 2019-03-21
I'm having difficulty getting 18.04 to play nice with Kodi / Mythtv. The problem seems isolated to my 4k tv in the living room, 1080 and lower seems fine. My symptom is only with mythtv playback. Audio out of sync, video stuttery at best, washed out at worst. Wondering if anyone has a similar setup, that is working just fine with Mythtv.

Kodi Leia, Mythtv .29 backend, Ubuntu 18.04, Amd graphics. I'm hoping someone has it working and I can compare the differences between our systems / packages and find what I'm missing, if anything. I've been fiddling with this awhile now, still nothing. Any help would be appreciated. For what it's worth, everything is perfectly fine on 16.04 right now. Just hoping to get upgraded as soon as I can.

---

### Post by Tadaen_Sylvermane on 2019-09-03
I am finally marking this as solved. I have worked off and on over the last 5 months, trying different things. Always ended up rebooting back to my 16.04 LVM volume.

The problem involved mergerfs. I cannot explain why, but eliminating it from the equation and mythtv playback is perfect. It's some combination of mythtv, mergerfs and 18.04 that causes the problem. I'm fairly certain mergerfs isn't the actual issue as I backported 18.04 mergerfs to 16.04 and never had this issue. Disabling it did work however. The reason I never found anything is because likely no one has the same configuration I have. I've learned mergerfs isn't used by many. Most use a proper raid or lvm.

I will be replanning my storage needs around a nas instead of more local drives with mergerfs. I am finally successfully upgraded to 18.04 on my server / living room htpc.

---

