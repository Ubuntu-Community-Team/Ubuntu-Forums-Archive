---
title: "Broken(?) software-properties-gtk"
date: 2010-05-09
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by ubername on 2010-05-09
Hi

I edited etc/sources.list and replaced all 'lucid' with 'maverick'

Then went into synaptic, reload, mark all updates, apply - All good, I now have a maverick install.

I then noticed that when I tried to look at the repositories, I was told something along the lines of 'Repositories are out-of-date,  you need to reload'

Unfortunately I checked the box marked 'don't tell me again' and now I cant use anywhere that software-properties-gtk is required (synaptic and Software Source'

Couple of Q's- 

Did I upgrade the right way (I know it's way early, there is no right way etc., but is editing source.list what everyone else has done?)

Anyone know where to unset the 'don't show this message again' parameter? I've trawled around the python scripts for software-properties but can't follow them well enough to work it out.

---

### Post by m.rankovic on 2010-05-09
[http://ubuntuforums.org/showpost.php?p=9261429&postcount=43](http://ubuntuforums.org/showpost.php?p=9261429&postcount=43)

---

### Post by ubername on 2010-05-09
Thanks m.rankovic (and plun from the link, and LKjell from the link in plun's link!)

That's fixed the main problem.

Still interested to find out how I can switch the message 'You need to reload' back on, any clues.

---

### Post by Starks on 2010-05-09
This bug also prevent add-apt-repository from working. Python errors and such.

Furthermore, once I edited the file, the command exhibits this annoying bug:
[https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/502454](https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/502454)
"add-apt-repository should allow version specification or offer next highest repo version if repo for running version is not found"

---

### Post by ranch hand on 2010-05-09
> **ubername said:**
> Thanks m.rankovic (and plun from the link, and LKjell from the link in plun's link!)

That's fixed the main problem.

Still interested to find out how I can switch the message 'You need to reload' back on, any clues.
Good grief, I can tell you ways to make sure it never shows up in the first place.  Can't believe anyone wants that irritant on their box at all.

Wouldn't the world be boring if we were all the same and liked the same things?

---

### Post by ubername on 2010-05-09
> **ranch hand said:**
> Good grief, I can tell you ways to make sure it never shows up in the first place.  Can't believe anyone wants that irritant on their box at all.

Wouldn't the world be boring if we were all the same and liked the same things?

Hi Ranch hand:

Quite right, I don't WANT the message, but it bugs me not knowing how to get it back, so I can switch it off again!

---

### Post by plun on 2010-05-09
> **ubername said:**
> Thanks m.rankovic (and plun from the link, and LKjell from the link in plun's link!)

That's fixed the main problem.

Still interested to find out how I can switch the message 'You need to reload' back on, any clues.

Probably fixed now

[https://lists.ubuntu.com/archives/maverick-changes/2010-May/000075.html](https://lists.ubuntu.com/archives/maverick-changes/2010-May/000075.html)

> python-apt (0.7.94.2ubuntu7) maverick; urgency=low

 [B] * data/templates/Ubuntu.info.in:
    - add maverick[/B]


---

