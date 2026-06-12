---
title: "Rosegarden in Ubuntu Studio"
date: 2007-05-14
forum: Multimedia Production
---

### Post by drosky on 2007-05-14
Is the Ubuntu Studio project planning to keep the Rosegarden package more current than in the main Ubuntu repositories, as is being done with Ardour?  Currently the repository has Rosegarden 1.4.0, but the stable release has gone through 1.5.0 and is currently at 1.5.1.

Thanks.

---

### Post by MetalMusicAddict on 2007-05-14
> **drosky said:**
> Is the Ubuntu Studio project planning to keep the Rosegarden package more current than in the main Ubuntu repositories, as is being done with Ardour?  Currently the repository has Rosegarden 1.4.0, but the stable release has gone through 1.5.0 and is currently at 1.5.1.

Thanks.

The only reason our package for Ardour is newer is because we missed the mark for Feisty. That being said, we will try to get packages like Rosegarden updated if we can but alot depends on what Debian is doing.

Ubuntu Studio will not have its separate repo for Gutsy.

---

### Post by drosky on 2007-05-15
> **MetalMusicAddict said:**
> The only reason our package for Ardour is newer is because we missed the mark for Feisty. That being said, we will try to get packages like Rosegarden updated if we can but alot depends on what Debian is doing.

Ubuntu Studio will not have its separate repo for Gutsy.

Thanks for the reply.  I guess I'm not sure I completely understand, however.  I think what you are saying is that by the time Gutsy comes around, Studio will depend entirely on packages in the main Ubuntu repository.

I guess that's OK as long as there is an effort to keep packages more up to date than they traditionally have been.  I was hoping Ubuntu Studio would help me migrate back to Ubuntu.  I migrated away primarily because so many of the packages (Rosegarden being a prime example) were always out-of-date compared to what was available for a number of other distros.  If Ubuntu wants to be competitive for multimedia production, it will need to find a way to keep a number of the packages more up-to-date than it typically has done in the past (IMHO).  I was hoping that would be one of the goals of the Studio project.

---

### Post by MetalMusicAddict on 2007-05-15
> **drosky said:**
> I was hoping that would be one of the goals of the Studio project.

It is but you have to realize that alot of Ubuntu is based off of Debian-Unstable. So if we sync a package from them thats the one we get. Unless we create a delta. (think thats the right word)

So sometimes our hands are tied.

---

### Post by drosky on 2007-05-15
> **MetalMusicAddict said:**
> It is but you have to realize that alot of Ubuntu is based off of Debian-Unstable. So if we sync a package from them thats the one we get. Unless we create a delta. (think thats the right word)

So sometimes our hands are tied.

I understand a little better now, and it's good that it is a goal to stay more current.  My experience in the past is that Ubuntu releases tend to have nearly up-to-date packages at the beginning of the release, but they get "stale" a few months down the road, because there seems to be a reluctance to upgrade package versions within a release.  This is why for certain things, like music, I started using another distro which has a lot of 3rd party repositories where things are kept more up to date.

More to the topic, I looked at Debian and noticed that both unstable and testing are at version 1.5.1 for Rosegarden.  I downloaded Rosegarden and Rosegarden-data from testing and they installed and ran fine on Feisty (Mint Cassandra, actually) - all dependencies were satisfied from the Feisty repositories.  Given this, is it possible that those packages could be moved to Feisty (or to the Ubuntu Studio repository), to make them easier to obtain for newbies, etc.?

---

