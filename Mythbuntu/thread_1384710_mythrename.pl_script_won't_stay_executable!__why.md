---
title: "mythrename.pl script won't stay executable!  why?"
date: 2010-01-18
forum: Mythbuntu
---

### Post by neutron68 on 2010-01-18
I've got a cron.hourly job set to call the "/usr/share/doc/mythtv-backend/contrib/user_jobs/mythrename.pl" script once per hour.

My cron script looks like this:
```
#!/bin/bash
/usr/share/doc/mythtv-backend/contrib/user_jobs/mythrename.pl --link /var/lib/mythtv/pretty --verbose --format "%T %- %Y-%m-%d, %g-%i %A %- %S"
```

I made the cron job executable with the command:
```
sudo chmod 755 /etc/cron.hourly/prettynames
```

In order for the mythrename.pl script to be allowed to run, I had to make it executable, also:
```
sudo chmod 755 /usr/share/doc/mythtv-backend/contrib/user_jobs/mythrename.pl
```

This all works fine and the /var/lib/mythtv/pretty directory is populated with nice, readable filenames, UNTIL I turn off or reboot the pc.  The next time I power up the pc, the mythrename.pl file is not executable any more!  WHY???

How can I fix this, so I don't have to keep invoking the chmod command on the mythrename.pl script after every reboot?

Help appreciated,
Eric

---

### Post by nickrout on 2010-01-18
At a guess, try moving the rename script to /usr/bin or /usr/local/bin, and changing your cron script to the new path.

---

### Post by superm1 on 2010-01-19
Are you running the autobuilds by chance?  It's possible there's a bug here that's causing that in the packaging.

---

### Post by theSeekerr on 2010-01-19
That is indeed the problem - I mentioned it Jean-Yves Avenard (the maintainer of the Avenard repository) and he told me it was an issue coming from upstream, ie. the Auto-builds.

---

### Post by neutron68 on 2010-01-19
> **superm1 said:**
> Are you running the autobuilds by chance?  It's possible there's a bug here that's causing that in the packaging.
I do have the weekly Mythbuntu 0.22 updates enabled.  Is that what you mean by autobuilds?

Eric

---

### Post by superm1 on 2010-01-19
OK I just double checked debian policy and it appears to be allowed.  Can you please file a bug on Launchpad for this to be tracked?  it can be fixed in a future iteration of the autobuilds.

---

### Post by neutron68 on 2010-01-19
> **superm1 said:**
> OK I just double checked debian policy and it appears to be allowed.  Can you please file a bug on Launchpad for this to be tracked?  it can be fixed in a future iteration of the autobuilds.
Is this directed to me or to "theSeekerr"?

---

### Post by superm1 on 2010-01-19
Doesn't matter to me.  Just someone do it so this isn't forgotten :)

---

### Post by neutron68 on 2010-01-20
> **theSeekerr said:**
> That is indeed the problem - I mentioned it Jean-Yves Avenard (the maintainer of the Avenard repository) and he told me it was an issue coming from upstream, ie. the Auto-builds.

Given that "theSeekerr" has background info on the cause of the problem, it would make sense for him to make a bug report.

Sound good, "theSeekerr"?

---

### Post by superm1 on 2010-01-21
Don't fret.  I think this should be addressed in the next set of builds (anything bigger than 23193 and built after jan 18th)

---

