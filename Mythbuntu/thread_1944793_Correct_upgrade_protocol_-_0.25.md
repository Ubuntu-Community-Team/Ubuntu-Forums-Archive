---
title: "Correct upgrade protocol - 0.25"
date: 2012-03-21
forum: Mythbuntu
---

### Post by jb282 on 2012-03-21
I'm relatively new to running Mythbuntu (after 6+ years with Knoppmyth). Since 0.25 has gone RC i figured it was time to give it an eval. 

Been running stock MB11.10 so far - with all cumulative updates. No local modifications.

I followed the instructions from here to activate the automatic daily builds:

[http://www.mythbuntu.org/node/4](http://www.mythbuntu.org/node/4)

I switched the mythtv builds repository to 0.25.

Now when I run the update manager I get:

"Not all updates can be installed. Run a partial upgrade, to install as many updates as possible".

Now in the actual list of updates, some of the myth packages are selected, some aren't:

SELECTED:
mythtv
mythtv-backend-master
mythtv-database
mythtv-theme-mythbuntu

UNSELECTED:
libmyth-mython
libmythtv-perl
mythgallery
mythmusic
mythtv-backend
mythtv-common
mythtv-frontend
mythtv-transcode-utils
mythweather

So my questions are:
A) Am i doing this correctly? Or is there some other protocol i should follow to upgrade mythtv?

B) If this is correct, what now?  Do i do the paritial upgrade, and (I'm guessing, because of dependancies?) run updateManager again which will then update the rest of the packages. It not doing all 0.25 packages at once makes me suspicious.

Thanks for any advice. Like most people I'm hesitant to break a working system.

---

### Post by nickrout on 2012-03-21
remove libmyth, it will probably remove other stuff too, don't panic.

Then do an upgrade and all should be well.

---

### Post by nickrout on 2012-03-21
Actually those are not the instructions you want.

Try here [http://www.mythbuntu.org/repos](http://www.mythbuntu.org/repos)

---

### Post by jb282 on 2012-03-21
> **nickrout said:**
> remove libmyth, it will probably remove other stuff too, don't panic.

Then do an upgrade and all should be well.

You mean uninstall the currently installed version of libmyth?

---

### Post by nickrout on 2012-03-22
yes, the current version prevents upgrading to the new version.

Also I hope you have backed up your database.

---

### Post by superm1 on 2012-03-22
This does sound like potentially a bug that update manager isn't resolving this properly.

If you run

# apt-get dist-upgrade

Does that do the right thing?

---

### Post by nickrout on 2012-03-22
> **superm1 said:**
> This does sound like potentially a bug that update manager isn't resolving this properly.

If you run

# apt-get dist-upgrade

Does that do the right thing?

I have found in upgrade from 0.22 --> 0.23 and 0.23-->0.24 that libmyth needs to be manually removed and then the new version installed or apt barfs.

---

### Post by uncle hammy on 2012-03-23
> **superm1 said:**
> This does sound like potentially a bug that update manager isn't resolving this properly.

If you run

# apt-get dist-upgrade

Does that do the right thing?

Like Nick, I've found that the Update manager hasn't handled this properly for a  couple versions now.  I found the easiest way to do it is to open Synaptic Package Manager and "Reload" and "Mark all Upgrades"

---

### Post by jb282 on 2012-03-24
> **superm1 said:**
> This does sound like potentially a bug that update manager isn't resolving this properly.

If you run

# apt-get dist-upgrade

Does that do the right thing?

Bullseye.  That performed the upgrade without complaints or conflicts.  Everything seems to be good. Thanks for that.

cheers -j

---

### Post by tgm4883 on 2012-03-25
dist-upgrade is required when a new package dependency is added (in the case of MythTV, the new dependency is libmyth-0.25 instead of libmyth-0.24). Needing the dist-upgrade to install new dependencies is the correct way to do that.

---

