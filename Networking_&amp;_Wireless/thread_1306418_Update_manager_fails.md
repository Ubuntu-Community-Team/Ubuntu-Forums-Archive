---
title: "Update manager fails"
date: 2009-10-30
forum: Networking &amp; Wireless
---

### Post by Kruptein on 2009-10-30
If I do check in update manager, it fails in the half of his operation.
If I do:
```
sudo apt-get update && sudo apt-get upgrade
```
It also fails while it is trying to connect with: be.archive.ubuntu.com
it gives me the following errors:
> 
W: Ophalen van [http://be.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-nl.bz2](http://be.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-nl.bz2) Kan niet verbinden met be.archive.ubuntu.com http: is mislukt

W: Ophalen van [http://be.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-nl.bz2](http://be.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-nl.bz2) Kan niet verbinden met be.archive.ubuntu.com http: is mislukt

W: Ophalen van [http://be.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-nl.bz2](http://be.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-nl.bz2) Kan niet verbinden met be.archive.ubuntu.com http: is mislukt

W: Ophalen van [http://be.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-nl.bz2](http://be.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-nl.bz2) Kan niet verbinden met be.archive.ubuntu.com http: is mislukt

W: Ophalen van [http://be.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg](http://be.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg) Kan niet verbinden met be.archive.ubuntu.com http: is mislukt

W: Ophalen van [http://be.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-nl.bz2](http://be.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-nl.bz2) Kan niet verbinden met be.archive.ubuntu.com http: is mislukt

W: Ophalen van [http://be.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-nl.bz2](http://be.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-nl.bz2) Kan niet verbinden met be.archive.ubuntu.com http: is mislukt

W: Ophalen van [http://be.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-nl.bz2](http://be.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-nl.bz2) Kan niet verbinden met be.archive.ubuntu.com http: is mislukt

W: Ophalen van [http://be.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-nl.bz2](http://be.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-nl.bz2) Kan niet verbinden met be.archive.ubuntu.com http: is mislukt

W: Ophalen van [http://be.archive.ubuntu.com/ubuntu/dists/karmic-backports/Release.gpg](http://be.archive.ubuntu.com/ubuntu/dists/karmic-backports/Release.gpg) Kan niet verbinden met be.archive.ubuntu.com http: is mislukt

W: Ophalen van [http://be.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/i18n/Translation-nl.bz2](http://be.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/i18n/Translation-nl.bz2) Kan niet verbinden met be.archive.ubuntu.com http: is mislukt

W: Ophalen van [http://be.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/i18n/Translation-nl.bz2](http://be.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/i18n/Translation-nl.bz2) Kan niet verbinden met be.archive.ubuntu.com http: is mislukt

W: Ophalen van [http://be.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/i18n/Translation-nl.bz2](http://be.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/i18n/Translation-nl.bz2) Kan niet verbinden met be.archive.ubuntu.com http: is mislukt

W: Ophalen van [http://be.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/i18n/Translation-nl.bz2](http://be.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/i18n/Translation-nl.bz2) Kan niet verbinden met be.archive.ubuntu.com http: is mislukt

W: Ophalen van [http://be.archive.ubuntu.com/ubuntu/dists/karmic-proposed/Release.gpg](http://be.archive.ubuntu.com/ubuntu/dists/karmic-proposed/Release.gpg) Kan niet verbinden met be.archive.ubuntu.com http: is mislukt

W: Ophalen van [http://be.archive.ubuntu.com/ubuntu/dists/karmic-proposed/restricted/i18n/Translation-nl.bz2](http://be.archive.ubuntu.com/ubuntu/dists/karmic-proposed/restricted/i18n/Translation-nl.bz2) Kan niet verbinden met be.archive.ubuntu.com http: is mislukt

W: Ophalen van [http://be.archive.ubuntu.com/ubuntu/dists/karmic-proposed/main/i18n/Translation-nl.bz2](http://be.archive.ubuntu.com/ubuntu/dists/karmic-proposed/main/i18n/Translation-nl.bz2) Kan niet verbinden met be.archive.ubuntu.com http: is mislukt

W: Ophalen van [http://be.archive.ubuntu.com/ubuntu/dists/karmic-proposed/multiverse/i18n/Translation-nl.bz2](http://be.archive.ubuntu.com/ubuntu/dists/karmic-proposed/multiverse/i18n/Translation-nl.bz2) Kan niet verbinden met be.archive.ubuntu.com http: is mislukt

W: Ophalen van [http://be.archive.ubuntu.com/ubuntu/dists/karmic-proposed/universe/i18n/Translation-nl.bz2](http://be.archive.ubuntu.com/ubuntu/dists/karmic-proposed/universe/i18n/Translation-nl.bz2) Kan niet verbinden met be.archive.ubuntu.com http: is mislukt

Hope someone can help me :(
(This was both on Jaunty and Karmic)

---

### Post by Kruptein on 2009-10-31
A lot of packages misses too! I can't install a lot because the update-manager can't find all necessary packages :O

How can I fix this?

(I found out that If I browse to be.archive.ubuntu.com  the browser fails to connect, but if I connect to let's say de.archive.ubuntu.com  the browser shows me the index :O should I permantly switch to the english packages or should I wait until the belgian are back online?)

---

### Post by Kruptein on 2009-10-31
I changed my download server to the netherlands, and it is al solved,

still the belgian servers doesn't work?

---

### Post by leduc900 on 2009-10-31
I have the same problem. I am now using a server from netherlands and problem solved. Thank you.

---

