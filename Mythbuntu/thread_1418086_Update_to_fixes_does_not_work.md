---
title: "Update to fixes does not work"
date: 2010-02-28
forum: Mythbuntu
---

### Post by Techmanm on 2010-02-28
I used the following command to update to the fixes:

"sudo svn co [http://svn.mythtv.org/svn/branches/release-0-22-fixes/](http://svn.mythtv.org/svn/branches/release-0-22-fixes/) mythtv-0-22" 

I get the message that mythtv is updated to revision 23626.

When i startup the frontend end press menu it shows revision 22594.

So it looks like the update didn't work,

How is this possible?

---

### Post by tgm4883 on 2010-02-28
> **Techmanm said:**
> I used the following command to update to the fixes:

"sudo svn co [http://svn.mythtv.org/svn/branches/release-0-22-fixes/](http://svn.mythtv.org/svn/branches/release-0-22-fixes/) mythtv-0-22" 

I get the message that mythtv is updated to revision 23626.

When i startup the frontend end press menu it shows revision 22594.

So it looks like the update didn't work,

How is this possible?

What you did there was just check out the mythtv branch (or possibly update a branch you already checked out). Basically you now have the source code to mythtv. You would still need to compile that code. Where did you get the idea to upgrade that way? You should install mythbuntu-repos from [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds) and then upgrade using apt.

---

### Post by azmyth on 2010-03-02
Once you checkout the first time I think you just need to enter the command svn update from the directory.

$svn update

Not sure why you're doing it root as it's not necessary

---

### Post by tgm4883 on 2010-03-02
> **azmyth said:**
> Once you checkout the first time I think you just need to enter the command svn update from the directory.

$svn update

Not sure why you're doing it root as it's not necessary

I don't think the OP is trying to update a checked out branch. I think the OP is trying to upgrade his installed version of MythTV

---

### Post by azmyth on 2010-03-03
Ahh, I misread the OP. Anyhow, I think I know what your problem is.

1) If you're using mythtv packages, you'll want to remove them before you do the install if you're compiling.

2) The other thing is when you compile the default location if you don't specify is /usr/bin/local. MB installs to /usr/bin so you need to set the prefix in the config command --prefix=/usr so if you have an old package in /usr/bin I believe the system looks here first so it runs your older rev of mythtv.

---

### Post by tgm4883 on 2010-03-03
> **azmyth said:**
> Ahh, I misread the OP. Anyhow, I think I know what your problem is.

1) If you're using mythtv packages, you'll want to remove them before you do the install if you're compiling.

2) The other thing is when you compile the default location if you don't specify is /usr/bin/local. MB installs to /usr/bin so you need to set the prefix in the config command --prefix=/usr so if you have an old package in /usr/bin I believe the system looks here first so it runs your older rev of mythtv.

That is if the OP is actually trying to compile, which I don't think is the intention here. I believe they just want to update (which can be done from the auto-builds repo). In either case, I wonder if the OP is still reading this or if it's just you and I speculating.

---

### Post by Techmanm on 2010-03-05
> **tgm4883 said:**
> That is if the OP is actually trying to compile, which I don't think is the intention here. I believe they just want to update (which can be done from the auto-builds repo). In either case, I wonder if the OP is still reading this or if it's just you and I speculating.

I'm still here.

You are right i just want to upgrade to the latest fixes because my HVR4000 doesn't work.

Thanks for the reply.

---

