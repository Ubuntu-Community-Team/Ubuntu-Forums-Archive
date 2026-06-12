---
title: "Mythbuntu repository 404?"
date: 2007-10-10
forum: Mythbuntu
---

### Post by 0thvarun on 2007-10-10
When I try to do a apt-get update, I get this - 

Failed to fetch http://www.mythbuntu.org/files/packages/dists/gutsy/mythbuntu/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://www.mythbuntu.org/files/packages/dists/gutsy/mythbuntu/source/Sources.g 404 Not Found

Could something in my sources.list be wrong?

These are it's contents - 

deb [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) gutsy main restricted universe multiverse
deb [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) gutsy-updates main restricted universe multiverse
deb [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) gutsy-security main restricted universe multiverse
deb [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) gutsy-backports main restricted universe multiverse
deb [http://www.mythbuntu.org/files/packages](http://www.mythbuntu.org/files/packages) gutsy mythbuntu
deb-src [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) gutsy-updates main restricted universe multiverse
deb-src [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) gutsy universe multiverse main restricted
deb-src [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) gutsy-security main restricted universe multiverse
deb-src [http://www.mythbuntu.org/files/packages](http://www.mythbuntu.org/files/packages) gutsy mythbuntu


Thanks,

Varun

---

### Post by superm1 on 2007-10-10
> **0thvarun said:**
> When I try to do a apt-get update, I get this - 

Failed to fetch [http://www.mythbuntu.org/files/packages/dists/gutsy/mythbuntu/binary-i386/Packages.gz](http://www.mythbuntu.org/files/packages/dists/gutsy/mythbuntu/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://www.mythbuntu.org/files/packages/dists/gutsy/mythbuntu/source/Sources.g](http://www.mythbuntu.org/files/packages/dists/gutsy/mythbuntu/source/Sources.g) 404 Not Found

Could something in my sources.list be wrong?

These are it's contents - 

deb [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) gutsy main restricted universe multiverse
deb [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) gutsy-updates main restricted universe multiverse
deb [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) gutsy-security main restricted universe multiverse
deb [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) gutsy-backports main restricted universe multiverse
deb [http://www.mythbuntu.org/files/packages](http://www.mythbuntu.org/files/packages) gutsy mythbuntu
deb-src [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) gutsy-updates main restricted universe multiverse
deb-src [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) gutsy universe multiverse main restricted
deb-src [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) gutsy-security main restricted universe multiverse
deb-src [http://www.mythbuntu.org/files/packages](http://www.mythbuntu.org/files/packages) gutsy mythbuntu


Thanks,

Varun
Sorry, but you can't cleanly upgrade from anything less than alpha 4 to the current easily.

You will have to take out that extra repository, and you can attempt apt-get update/upgrade, but no guarantees.  A LOT has changed since then, and not easily representable.

---

