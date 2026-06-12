---
title: "MythVideo Metadata Disappearing"
date: 2012-02-16
forum: Mythbuntu
---

### Post by nasha on 2012-02-16
Hi Guys,

This has been somewhat of an issue for some time, but become much more prominent since moving to 0.25. No doubt due to the changes with how Video operates.

If i scan in metadata for my videos it all loads fine, and i see entries in mythconverg for them.

After a reboot, or suspend/wake, all metadata info is gone on the frontend (remote).

All entries are still in the mythconverg DB though.

Another, possibly related issue: With TV series', i have to "reset details" then "retrieve details" in order to get data for them. This certainly isnt right.

As one of my troubleshooting steps, i removed all entries in the videometadata table of mythconverg, to ensure it wasn't some issue there. The issue remains after doing this also.

Any ideas?

Mythbuntu  - 11.10
MythTV     - 0.25.0~master.20120214.dcfe7b0

Thanks,
Nasha

---

### Post by nasha on 2012-02-16
Some further info:

Have run a few "Scan for changes", and it appears it's adding new entries for every video into the DB.

So i now have 4+ entries for every video....

---

### Post by nickrout on 2012-02-16
0.25 has not been released so you are running experimental code. Breakage should be expected. You need to subscribe to mythtv-dev and -commits email lists and I suggest you t take your question to -dev.

---

### Post by nasha on 2012-02-16
> **nickrout said:**
> 0.25 has not been released so you are running experimental code. Breakage should be expected. You need to subscribe to mythtv-dev and -commits email lists and I suggest you t take your question to -dev.

I've had issues with metadata disappearing prior to 0.25, so i thought it would be worth posting to see if anyone had any suggestions here...

Someone has suggested the following, but not elaborated on the matter:
> 
This sounds like yet another case of running 'File Browse Mode' and not 
understanding its implications.

---

### Post by nickrout on 2012-02-16
Much has changed with mythvideo in master.

---

