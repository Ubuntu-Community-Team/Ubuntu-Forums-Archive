---
title: "Mythbuntu settings won't open"
date: 2007-10-18
forum: Mythbuntu
---

### Post by w00tfest99 on 2007-10-18
When I go into utilities/setup->setup->mythbuntu I enter my password but then nothing happens.  Is there something that it's trying to start but can't?

---

### Post by superm1 on 2007-10-18
Try to apt-get update and do it once more.  If that doesn't work out, try this deb.  It will need to be pushed to gutsy-updates unfortunately:

[http://ppa.launchpad.net/mythbuntu/ubuntu/pool/main/m/mythbuntu-control-centre/mythbuntu-control-centre_0.11-0ubuntu1~ppa1_all.deb](http://ppa.launchpad.net/mythbuntu/ubuntu/pool/main/m/mythbuntu-control-centre/mythbuntu-control-centre_0.11-0ubuntu1~ppa1_all.deb)

---

### Post by jb5 on 2007-10-19
The deb package did the trick in Gutsy 64bit.

Thanks.

---

### Post by w00tfest99 on 2007-10-19
Thanks, that fixed 'er

---

### Post by spii on 2007-10-20
fixed it for me too (also amd64; I already have/had mythtv front and backend installed and working, since edgy - looking forward to this though, sounds promising!)

---

