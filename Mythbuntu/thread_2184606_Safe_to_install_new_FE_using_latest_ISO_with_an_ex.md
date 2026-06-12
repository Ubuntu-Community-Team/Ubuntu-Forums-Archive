---
title: "Safe to install new FE using latest ISO with an existing .26 BE?"
date: 2013-10-29
forum: Mythbuntu
---

### Post by GaryP2 on 2013-10-29
If I install the latest Mythbuntu 12.04.3 64-bit ISO on a new frontend computer to connect to my existing 12.04.3 0.26-fixes backend (fully upgraded), will I be given the chance to update that new system from 0.25 to 0.26 before the frontend tries to connect to the .026 backend? Or will it safely fail and I simply run MCC and select the .26 repo and do another update/upgrade/dist-upgrade?

I've never tried bringing up dissimilar versions across the BE and FE and don’t want to corrupt anything if the new system first comes up as 0.25. I already have one external FE and have kept both the BE and FE Myth versions in sync using MCC.

Thanks in advance.

---

### Post by GaryP2 on 2013-10-30
I went ahead and installed my new frontend and thought I&#8217;d give a quick update on what happened. During setup when I received the prompt to enter the security key &#8220;0000&#8221; on the Master Backend Info screen, I received the message:
[INDENT][I]
Mismatched schema version for &#8216;DBSchemaVer&#8217;:database speaks version 1307, we speak version 1299[/I][/INDENT]

After finishing the install and the system rebooted, I keyed in the backend IP address and mythconverg password in the frontend setup. At that point, the frontend displayed a similar schema mismatch error. When selecting OK (the only option available), the frontend.real process terminated and then restarted (the frontend wrapper seeing it terminated and restarted it like it should). I had to kill the mythfrontend process to stop the restart loop at which time I ran MCC, selected the 0.26 repo and ran update/upgrade/dist-upgrade to get to 0.26.

I did database backup just before attempting this, but given how things went I don&#8217;t anticipate any issues.

---

