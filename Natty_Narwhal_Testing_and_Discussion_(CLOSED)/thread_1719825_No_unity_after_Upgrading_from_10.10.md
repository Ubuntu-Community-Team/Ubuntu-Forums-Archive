---
title: "No unity after Upgrading from 10.10"
date: 2011-04-02
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Da Choice on 2011-04-02
Hi guys, having a bit of a problem:

Just upgraded to Ubuntu 11.04  straight from Ubuntu 10.10 (both 64bit edition) and I haven't been able to get unity to work. I've got an ATI card with restricted drivers enabled but upon startup unity refuses to work. 

I'm thinking it might be better to cut my losses, format and install from the live disc and if all else fails go back to 10.10 and wait for a stable release, but if anyone can help me figure out what's going on without losing a disc and some time, that would be incredibly appreciated.

---

### Post by taojian on 2011-04-02
> **Da Choice said:**
> Hi guys, having a bit of a problem:

Just upgraded to Ubuntu 11.04  straight from Ubuntu 10.10 (both 64bit edition) and I haven't been able to get unity to work. I've got an ATI card with restricted drivers enabled but upon startup unity refuses to work. 

I'm thinking it might be better to cut my losses, format and install from the live disc and if all else fails go back to 10.10 and wait for a stable release, but if anyone can help me figure out what's going on without losing a disc and some time, that would be incredibly appreciated.

I've got a similar setup, probably you'll have to do[this]("https://wiki.ubuntu.com/DesktopExperienceTeam/UnityWithFglrxBeta"). If we've all got the same issue, you'll also have to make Unity a startup application -- it won't start by itself.

---

### Post by taojian on 2011-04-02
Oh wait, [this thread]("http://ubuntuforums.org/showthread.php?p=10621903") seems to have better take on it, as well as a better solution over the startup application route.

---

### Post by Da Choice on 2011-04-02
Thank you! Turns out it was running all along, just wasn't working with my driver. All I needed to install the daily build from the repository your second link.

---

