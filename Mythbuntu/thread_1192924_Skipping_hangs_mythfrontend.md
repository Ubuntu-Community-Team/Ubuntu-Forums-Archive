---
title: "Skipping hangs mythfrontend"
date: 2009-06-20
forum: Mythbuntu
---

### Post by BenZo on 2009-06-20
Hi All,

Just did a dist-upgrade from 8.10 to 9.04 & now any time I try to skip forward or fast forward mythfrontend will hang with the OSD. I have to kill the frontend to be able to use it again. I've waited upto 20 minutes for the frontend to become responsive, but nothing.

This happens in recorded TV or when using the Internal player for videos. I've never seen this type of issue before & searching has revealed info about the seek tables. I've run the optimize_mythdb.pl script & even did a repair tables * extended in mysql itself. No difference.

It was working fine with 8.10. I do have the -fixes weekly builds enabled. 

Any ideas ? It's pretty frustrating not being able to skip past the commercials....

Thanks,
BenZo

---

### Post by ian dobson on 2009-06-21
Hi,

I saw this yesterday with the VDPAU backports, I just did a apt-get update/upgrade and it downloaded an update for myth-frontend and all is well now.

I think VDPAU backports follows the weekly build version number fairly closly so maybe just try an update in afew days.

Regards
Ian Dobson

---

### Post by BenZo on 2009-06-22
Spot on Ian,

I didn't realize that the avenard repo got disabled in the dist-upgrade.

Re-enabled it, ran the update/upgrade & all is well again.

Thanks for your help.

Cheers,
BenZo

---

