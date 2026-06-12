---
title: "upgrading Kubuntu 10.04 to maverick?"
date: 2010-06-08
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by tr333 on 2010-06-08
What is the recommended way to upgrade a Kubuntu 10.04 install to maverick?  The Ubuntu docs say to use "update-manager -d" for Ubuntu, but I can't find the Kubuntu equivalent anywhere.

---

### Post by descendent87 on 2010-06-08
The way I usually do it is to edit /etc/apt/sources.list in kwrite, change all "lucid" to "maverick" then apt-get upgrade && apt-get dist-upgrade.
At the moment the new X is slowly coming in so check **very carefully** what is going to be removed etc when you dist-upgrade or you'll end up with an unusable system

A safe option would be to download alpha 1 cd and install that or to wait a few days until the X updates have finished then upgrade

---

### Post by ranch hand on 2010-06-08
Doesn't Kubuntu use Update Mangler?  If it does the same command would work.

You could also edit the /etc/apt/sources list to read "maverick" at every instance of "lucid", save the file, run;
```

sudo apt-get update

```
I believe that you need something other than "sudo" under Kubuntu but hopefully you know that.

Then;
```

sudo apt-get dist-upgrade

```
Before doing any of the above read ALL the stickies at the top of this forum, at least the first post.

10.10 is in development it is not a production OS at this point by any means.  Expect it to break, that is what it is supposed to do.

Our job is to have it break, file bugs, let the devs fix it.

---

### Post by Reiger on 2010-06-09
> **ranch hand said:**
> I believe that you need something other than "sudo" under Kubuntu but hopefully you know that.

No you don't. sudo is the terminal program. (Both Gnome and KDE offer a wrapper around them [gkdsudo/kdesudo], but for working in a terminal these are fairly irrelevant.)

> 
Then;
```

sudo apt-get dist-upgrade

```
Before doing any of the above read ALL the stickies at the top of this forum, at least the first post.

10.10 is in development it is not a production OS at this point by any means.  Expect it to break, that is what it is supposed to do.

Note that I would not use apt-get dist-upgrade especially not due to aforementioned X-related breakage that has been promised with the upgrade to the new X server. Rather I would use sudo aptitude update && sudo aptitude safe-upgrade which should hold back parts of the system that cannot be safely upgraded yet.

---

### Post by taavikko on 2010-06-09
One can always use the 
```
sudo do-release-upgrade --devel
```
as well...

If the /etc/update-manager/release-upgrades
has prompt=normal

---

### Post by tr333 on 2010-06-10
Thanks all for the info.  I've got experience with Ubuntu/server dev releases, but trying Kubuntu for the first time.

---

