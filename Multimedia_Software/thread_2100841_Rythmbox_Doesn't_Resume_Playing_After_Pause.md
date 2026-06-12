---
title: "Rythmbox Doesn't Resume Playing After Pause"
date: 2013-01-02
forum: Multimedia Software
---

### Post by HDTimeshifter on 2013-01-02
Rythmbox won't resume playing after I pause in the middle of a track on a CD. I tried clicking on the play arrow and double clicking on the track number with no resume in playing. The only thing that works is to quit Rythmbox and relaunch.

I have version 2.96 and tried to remove it and install version 2.98 through Ubuntu Software Center, but it only installs 2.96.

---

### Post by vasiliscnisrok on 2013-01-03
try
```

sudo apt-get update
sudo apt-get purge rhythmbox
rm -Rf ~/.cache/rhythmbox/
rm -Rf ~/.local/share/rhythmbox/
sudo apt-get -o DPkg::options::=--force-confmiss --**reinstall** **install** rhythmbox

```

---

### Post by HDTimeshifter on 2013-01-03
Thanks vasiliscnisrok, but looks like it just reinstalled 2.96 and it still won't resume from pause. I guess 2.96 is the only Ubuntu supported version or something.

---

### Post by vasiliscnisrok on 2013-01-03
> **HDTimeshifter said:**
> Thanks vasiliscnisrok, but looks like it just reinstalled 2.96 and it still won't resume from pause. I guess 2.96 is the only Ubuntu supported version or something.
Maybe install rhythmbox from PPA ?
[https://launchpad.net/~webupd8team/+archive/rhythmbox](https://launchpad.net/~webupd8team/+archive/rhythmbox)

---

