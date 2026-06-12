---
title: "Where to get the source code for Mythbuntu 8.04?"
date: 2008-05-26
forum: Mythbuntu
---

### Post by TwistedLincoln on 2008-05-26
Where can I get the full source code for the Mythbuntu 8.04 distribution?  Normally, I get source ISOs from cdimage.ubuntu.com, but the listing for Mythbuntu links to a 0 k file.  (see: [http://cdimage.ubuntu.com/mythbuntu/releases/8.04/release/source/]("http://cdimage.ubuntu.com/mythbuntu/releases/8.04/release/source/"))

Was this just an oversight, or should I look elsewhere?

---

### Post by superm1 on 2008-05-26
For any particular package, apt-get source PACKAGE

Also look at the bzr branches:
[https://code.edge.launchpad.net/~mythbuntu/](https://code.edge.launchpad.net/~mythbuntu/)

---

### Post by TwistedLincoln on 2008-05-27
I know I can get the source for each package via APT, but I want to be able to distribute the Mythbuntu CD legally, and as such I'll need to provide access to the full corresponding source code for the entire distro.

I'm not familiar with bzr -- can I fetch the source for everything with in in the same way one might with SVN or CVS?

---

### Post by superm1 on 2008-05-27
Are you sure that you need to distribute all code "with" the CD?  Is it not sufficient to just link online?  Any of the mythbuntu-* packages are stored in bzr, you will have to check out each one however one at a time.  

All other packages may or may not be in bzr, but are most definitely stored in the Ubuntu archive (ala apt sources).  The mythbuntu-* are there as well, so if you can directly link that route, that's the way to go.

---

### Post by TwistedLincoln on 2008-05-27
> **superm1 said:**
> Is it not sufficient to just link online?

No, it's not, sadly.  The GPL requires that anyone who distributes binaries provide access to the source *themselves*, it is not sufficient to simply point to someone else's site and tell people "just get it from there." 

While I may not need to actually distribute the source code with the CD, I do need to personally have a copy of it so that I can provide it if asked.

Unless someone knows an automated way to fetch the source code for all installed packages, individually downloading hundreds of files is not an option.

Does anyone know who maintains the source ISO?  My guess is that they simply forgot to upload it -- obviously getting a source ISO is the best option...

---

### Post by superm1 on 2008-05-27
> **TwistedLincoln said:**
> No, it's not, sadly.  The GPL requires that anyone who distributes binaries provide access to the source *themselves*, it is not sufficient to simply point to someone else's site and tell people "just get it from there." 

While I may not need to actually distribute the source code with the CD, I do need to personally have a copy of it so that I can provide it if asked.

Unless someone knows an automated way to fetch the source code for all installed packages, individually downloading hundreds of files is not an option.

Does anyone know who maintains the source ISO?  My guess is that they simply forgot to upload it -- obviously getting a source ISO is the best option...
Well that's the unfortunate thing;

I'm the one who gets these things built.  The live ISO and the alternate ISO build in vastly different fashions for Hardy.  The live ISO it would not be feasible to provide all the source on another ISO (with the current build process).  The alternate ISO it would be closer to feasible, but Canonical is limited on hosting space so that still isn't going to happen.

My recommendation is this:
```

for i in `dpkg -l  | awk '{print $2}'`
do
    apt-get source $i
done
```

---

