---
title: "Backend won't update to 0.27"
date: 2013-10-04
forum: Mythbuntu
---

### Post by NikosF on 2013-10-04
I've used MCC to select the 0.27 repo, but using either the software updater, or sudo apt-get dist-upgrade doesn't prompt me to upgrade.  I've even tried forcing the repo from the command line : sudo add-apt-repository ppa:mythbuntu/0.27 

But - it still seems stuck to 0.26.

Any ideas how to force an upgrade?

Thanks!

(Had to wait until after Breaking Bad finale to upgrade, so only getting to this now).

---

### Post by NikosF on 2013-10-04
PS: Backend is running 12.04.3

Also - tried to select 0.27 (using MCC) on one of my frontends (also running 12.04.3 LTS) and it offered the upgrade - but can't do it on frontend until backend is sorted out.

Also - noticed on my frontend (that offered upgrade), my choices were 0.26/0.27/0.28, but on the backend it was only offering 0.25/0.26/0.27.  And  - yes - I hit refresh.

---

### Post by tgm4883 on 2013-10-07
> **NikosF said:**
> PS: Backend is running 12.04.3

Also - tried to select 0.27 (using MCC) on one of my frontends (also running 12.04.3 LTS) and it offered the upgrade - but can't do it on frontend until backend is sorted out.

Also - noticed on my frontend (that offered upgrade), my choices were 0.26/0.27/0.28, but on the backend it was only offering 0.25/0.26/0.27.  And  - yes - I hit refresh.

Did you do an apt-get update?

---

### Post by NikosF on 2013-10-08
> **tgm4883 said:**
> Did you do an apt-get update?

Yup.

I did eventually get it to update - but first I had to update to 13.04, then it worked from the command line.

Strange, since it worked through MCC for my frontends all still running 12.04.

Thanks for the advice.

---

