---
title: "Trunk build development query"
date: 2010-06-20
forum: Mythbuntu
---

### Post by gezb10 on 2010-06-20
Hi,

I am looking at fixing mythnetvision in the daily builds broken when upstream tha change was made to only have the scripts on the backend and have the frontends request them from the backend

I assume I need to branch from the following branches
lp:~mythbuntu/mythtv/mythtv-trunk 
lp:~mythbuntu-mythtv/mythplugins/mythtv-plugins


make my changes and then request a merge into the main branch?

What is the best way to test the changes as those branches are working on revision 24856 but the daily build is now up at 25143? 
Or am I better apt-geting the source of the latest build and submit patchs based on that?


Thanks

Gerald

---

### Post by nickrout on 2010-06-20
> **gezb10 said:**
> Hi,

I am looking at fixing mythnetvision in the daily builds broken when upstream tha change was made to only have the scripts on the backend and have the frontends request them from the backend

I assume I need to branch from the following branches
lp:~mythbuntu/mythtv/mythtv-trunk 
lp:~mythbuntu-mythtv/mythplugins/mythtv-plugins


make my changes and then request a merge into the main branch?

What is the best way to test the changes as those branches are working on revision 24856 but the daily build is now up at 25143? 
Or am I better apt-geting the source of the latest build and submit patchs based on that?


Thanks

Gerald

You should probably ask this on the -dev mailing list.

---

### Post by superm1 on 2010-06-21
> **gezb10 said:**
> Hi,

I am looking at fixing mythnetvision in the daily builds broken when upstream tha change was made to only have the scripts on the backend and have the frontends request them from the backend

I assume I need to branch from the following branches
lp:~mythbuntu/mythtv/mythtv-trunk 
lp:~mythbuntu-mythtv/mythplugins/mythtv-plugins


make my changes and then request a merge into the main branch?

What is the best way to test the changes as those branches are working on revision 24856 but the daily build is now up at 25143? 
Or am I better apt-geting the source of the latest build and submit patchs based on that?


Thanks

Gerald
So the version at the top of debian/changelog on the branch isn't updated unless it's uploaded to the main ubuntu archive.  The autobuilds server makes the change locally just for that build.

That is the latest packaging though.

Are your changes headed to upstream mythtv?  Best bet is to generate the patch from an svn checkout (myth source code itself isn't imported into bzr yet).  If you want to test it with ubuntu packaging, once you have the patch in place, checkout that packaging branch, drop the patch in debian/patches and modify debian/patches/series to apply it during the build.

---

### Post by gezb10 on 2010-06-21
Ah I see, so I can just update the version at the top of debian/changelog and run get-orig-source to get the latest code?

My changes are just to the packaging, all thats being missed when the backend packge is installed is copying some files to /usr/share/mythtv which is done as part of make install (the internetcontent folder so the backend can find the scripts to serve to the frontends)

In the plugins package mythnetvision depends on libmyth-python (= 0.22.0~trunk23213-0ubuntu0) which is outdated (I was just going to remove the depencency on a specific version and depend on libmyth-python is that okay)

Thanks

Gerald

---

### Post by superm1 on 2010-06-21
> **gezb10 said:**
> Ah I see, so I can just update the version at the top of debian/changelog and run get-orig-source to get the latest code?

Yes.

> 
My changes are just to the packaging, all thats being missed when the backend packge is installed is copying some files to /usr/share/mythtv which is done as part of make install (the internetcontent folder so the backend can find the scripts to serve to the frontends)

If the changes are just to the packaging, you don't even need to run get-orig-source.  Make your changes, push your branch to launchpad and propose a merge.  We'll merge it into auto-builds then.

> 
In the plugins package mythnetvision depends on libmyth-python (= 0.22.0~trunk23213-0ubuntu0) which is outdated (I was just going to remove the depencency on a specific version and depend on libmyth-python is that okay)

Thanks

Gerald
0.22? That's a wii bit old.  The packaging has changed significantly since then... it's currently setup for 0.24 on trunk.

---

### Post by gezb10 on 2010-06-21
Okay that makes sense, Thanks

The depends for mythnetvision currently in the mythplugins-trunk debian/control are
 ```
mythtv-common (>= 0.20-0.0), mythtv-frontend (>= 0.20-0.0), ${shlibs:Depends}, ${misc:Depends}, mythbrowser (>= 0.22),** libmyth-python (= 0.22.0~trunk23213-0ubuntu0)**, python-feedparser, python-pycurl, flashplugin-installer | adobe-flashplugin
```

should I submit a fix for that too?

---

### Post by superm1 on 2010-06-21
> **gezb10 said:**
> Okay that makes sense, Thanks

The depends for mythnetvision currently in the mythplugins-trunk debian/control are
 ```
mythtv-common (>= 0.20-0.0), mythtv-frontend (>= 0.20-0.0), ${shlibs:Depends}, ${misc:Depends}, mythbrowser (>= 0.22),** libmyth-python (= 0.22.0~trunk23213-0ubuntu0)**, python-feedparser, python-pycurl, flashplugin-installer | adobe-flashplugin
```

should I submit a fix for that too?

So I believe that's also auto-adjusted by the auto-builds server if I recall correctly, I wouldn't worry too much about a patch for that bit.

---

### Post by jlagrone on 2010-06-22
It looks like the trunk auto builds are failing: it shows mythplugins as failed to build - it looks like that's because mythtv is not being built for some reason and since libmyth-dev is a depend of mythplugins they aren't getting built either.

That might explain why the versions are so mismatched from those upstream.

---

### Post by superm1 on 2010-06-22
> **jlagrone said:**
> It looks like the trunk auto builds are failing: it shows mythplugins as failed to build - it looks like that's because mythtv is not being built for some reason and since libmyth-dev is a depend of mythplugins they aren't getting built either.

That might explain why the versions are so mismatched from those upstream.
According to the build log ([http://smithers.mythbuntu.org/~autobuild/weekly_trunk.txt](http://smithers.mythbuntu.org/~autobuild/weekly_trunk.txt)) it looks like it's having a hard time recovering from some of the patches from before.

I've committed some changes to the autobuilds scripts to hopefully clean it up, but if it fails will need to ping someone to go and manually prod it.

---

