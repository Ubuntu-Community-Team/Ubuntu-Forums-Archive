---
title: "Adding PPAs without manually adding keys is such a pain right now."
date: 2010-05-10
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Starks on 2010-05-10
[https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/502454](https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/502454)

This bug needs more attention.

Basically, until Maverick PPA repos start popping up, we either have to  use the deb/deb-src and manually add the key or use the ppa:blah/blah  method and change the maverick to lucid in Software Souces for that PPA.

---

### Post by Sam on 2010-05-10
I don't see the connection between the thread title and the bug (which is, by the way, marked as duplicate of [bug 49834](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/49834)).

---

### Post by Starks on 2010-05-10
Well, it's my bug report. I can frame it however I wish. Besides, I forgot a single digit in the URL.

---

### Post by Sam on 2010-05-10
Ok I see. You link to 50245 but it should be 502454. The text is ok, but the link is wrong.

---

### Post by DougieFresh4U on 2010-05-10
As far as the title to the thread, YES :)

---

### Post by Starks on 2010-05-10
Link should be fine now.

---

### Post by Bachstelze on 2010-05-10
> **Starks said:**
> Adding PPAs without manually adding keys is such a pain right now.

Er, what?

```
sudo add-apt-repository ppa:<user>/<ppa>
```

What a pain...

---

### Post by Starks on 2010-05-10
You totally missed the point.

Doing that will add the repo as maverick and not function at all until you change the source to lucid.

99% of PPA repos are still lucid or older.

---

### Post by MacUntu on 2010-05-10
How many PPAs do you add per day? :D apt-add-repository takes care of the key and changing the distribution field in "Software Sources" is a non-issue to me. The proposed change would be nice, though.

---

### Post by hugmenot on 2010-05-10
There’s no guarantee that packages pulled from other releases will work. There can be changes to ABI and in libc, glib, and all sorts of other libraries.

---

### Post by Starks on 2010-05-10
That isn't a problem for most PPAs. If a PPA only has a repo for an older release, chances are that the Ubuntu main repo already supersedes the PPA's packages.

Secondly, people on Maverick who want to use PPAs like ubuntu-mozilla-daily or xorg-edgers have been told by the respective PPA maintainers to use the Lucid repo.

---

### Post by sisco311 on 2010-05-10
> **Starks said:**
> 
Secondly, people on Maverick who want to use PPAs like ubuntu-mozilla-daily or xorg-edgers have been told by the respective PPA maintainers to use the Lucid repo.


..., use the lucid repos or help them in building packages for maverick.

---

### Post by nanog on 2010-05-11
> There’s no guarantee that packages pulled from other releases will work.  

There is not guarantee that any package in a ppa will work!

Most of those libraries are designed to be backwards compatible. And besides many of us have been doing this type of naughty stuff for years. And at this point in development (e.g. pre-alpha) I would hope we would have permission to completely fry out installs!

---

### Post by ranch hand on 2010-05-11
> **nanog said:**
> There is not guarantee that any package in a ppa will work!

Most of those libraries are designed to be backwards compatible. And besides many of us have been doing this type of naughty stuff for years. And at this point in development (e.g. pre-alpha) I would hope we would have permission to completely fry out installs!
I certainly haven't been doing this "naughty stuff" for years but I do have a lot of installs and I do have permission to fry as many as I want.

I know I do.   I have it on a sticky note on my tower.

---

### Post by seeker5528 on 2010-05-13
> **Starks said:**
> Basically, until Maverick PPA repos start popping up, we either have to  use the deb/deb-src and manually add the key or use the ppa:blah/blah  method and change the maverick to lucid in Software Souces for that PPA.

Maybe the command line script should be fixed for those adding PPAs that way, but I can't really say I feel your pain.

If I go to 'System --> Administration --> Software Sources'.....

Or my preference, since if I am adding a PPA I will probably want to be installing something right away....

Open Synaptic and go to 'Settings --> Respositories --> Other Sofware --> Add'......

Type in the line to add the PPA, I used... ```
ppa:ubuntu-mozilla-daily/ppa
``` for my test case.

The key seemed to be handled, at least I never saw any complaints any where.

If you need to change the distribution, scroll down the list, select the newly added entry, click on 'Edit', do it.

Where's the pain in that? :P

Later, Seeker

---

### Post by Yofel on 2010-05-13
There's no real pain there, but I agree it's annoying. Mvo has acknowledged the bug so he plans to implement it sometime...
To increase the priority a bit everyone that agrees with this should set the bug as affecting him. Thanks!

---

