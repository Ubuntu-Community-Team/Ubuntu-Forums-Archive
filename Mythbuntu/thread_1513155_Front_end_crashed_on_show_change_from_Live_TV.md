---
title: "Front end crashed on show change from Live TV"
date: 2010-06-19
forum: Mythbuntu
---

### Post by gabrielbenjamin on 2010-06-19
I'm running Mythbuntu 9.04, with a single back/frontend and in the middle of watching live TV, mythfrontend crashed--significantly, it was just at the end of a show (so just at the point a new live recording would be starting). 

Reboot--same thing. Frontend log--unhelpful. (They actually end in October last year at some point for mythfrontend. I modified the mythfrontend script to not start mythfrontend.real if it's already up. Thing is, there's always a restored session of mythfrontend.real running by the time the script runs. Maybe that's why? Please forgive the tangent.)

Backend log shows nothing amiss, aside from autoexpiring an empty recording from the time of the crash, and this entry:
> 2010-06-18 22:57:27.208 Received a remote 'Clear Cache' request
Segmentation faultThere are two recording partitons, which are separate from the root, both 99% full, but the partition mythfrontend lives on is only 47% full.

I'm at my wit's end and very tempted to wipe and install 9.10 (no recordings I can't live without), but I hate throwing in the towel. Any suggestions?

Thanks to all in advance.

---

### Post by azmyth on 2010-06-20
> There are two recording partitons, which are separate from the root, both 99% full, but the partition mythfrontend lives on is only 47% full.
Is the FE, trying to write the recording to one of the full partitions?

---

