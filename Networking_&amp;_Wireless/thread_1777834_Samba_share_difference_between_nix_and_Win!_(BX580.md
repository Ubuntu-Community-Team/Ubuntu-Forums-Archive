---
title: "Samba share: difference between *nix and Win?! (BX580 finds one but not the other)"
date: 2011-06-08
forum: Networking &amp; Wireless
---

### Post by attractedtofire on 2011-06-08
Dear all,

I'm currently facing the following problem: my newly acquired Bluray-Player, a LG BX580 I chose for its support of SMB/CIFS, is not able to find the samba shares on a little home built Atom NAS running Ubuntu Server 10.04 LTS. At the same time though, it is perfectly capable to connect to shared folders on a Windows 7 machine.

When I navigate to the "Home Link" menu point (offering access to local network shares and DNLA-sources) on the BX, it will only list my Win machine (just some shared folders on there, no DNLA Windows Media crap). My NAS, despite having several folders shared via smbd (with and without access restrictions) is not shown at all.
I tried using a DNLA-Server (mediatomb) on the NAS and it worked fine, although it is not a good solution for me due to the restrictions of DNLA (no subtitle files supported ect.).

Does anybody have an idea if there exist any differences between the way a *nix Samba share via smbd and a Windows share appear to an smb/cifs-client (apparently there have to).


With many thanks and regards,
a.
____________________
OT 
maybe this info will proof useful to somebody someday - at least I didn't find any information on this anywhere on the net:
If you got an LG Bluray player with network streaming support and you are facing the problem that it just keeps crashes when trying to access the home link-menu you probably are a happy owner of a squeezebox and thus running a squeezebox server. LG-player's crappy written network-sw seems to get fairly upset by a running SBS - so - just block port 9000-traffic to the ip of the LG-player and things will work (cost me two days of fumbling around to get behind that one ;) ).

---

