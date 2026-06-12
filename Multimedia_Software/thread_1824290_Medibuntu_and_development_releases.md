---
title: "Medibuntu and development releases"
date: 2011-08-13
forum: Multimedia Software
---

### Post by carltonh on 2011-08-13
I upgraded from 11.04 to 11.10 and it seems there is not, at least yet, a medibuntu repository for oneiric.  However, some of the upgrades in oneiric while it is a development branch conflict with remaining medibuntu packages from 11.04, and wants to remove them when I run "sudo aptitude full-upgrade".  I don't want to remove them because I don't want to remove that functionality.  But at the same time, aptitude tells me I have a broken package because of it.

Any advice on dealing with this?  Should people who need medibuntu just never use a development release?  Are medibuntu repositories only created at a certain point in the development process?

---

### Post by oldos2er on 2011-08-13
As far as I know, Medibuntu only maintains repos for officially released versions of Ubuntu, not the alphas or betas.

Edit: And just to add, you should be able to manually download and install any packages you need from Medibuntu using dpkg or Software Center. "To access directly to a package page, use the following shortcut: [http://packages.medibuntu.org/](http://packages.medibuntu.org/)*release*/name.html"

---

