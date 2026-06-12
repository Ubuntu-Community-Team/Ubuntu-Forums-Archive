---
title: "libmyth-python does not contain any modules in 0.25"
date: 2011-05-03
forum: Mythbuntu
---

### Post by awaterson on 2011-05-03
Hi All,

Has anyone else noticed that the mythbuntu 0.25 ppa contains an empty libmyth-python package.  I have been attempting to run the mythnetvision plugin on my 0.25 system and have found that the python package only contains documentation. Anyone else seen this and resolved it?

Thanks is advance for any help

Andy

---

### Post by superm1 on 2011-05-03
According to a recent build log ([https://launchpadlibrarian.net/70549467/buildlog_ubuntu-natty-i386.mythtv_2%3A0.25.0~master.20110428.cf5a9bc-0ubuntu0mythbuntu2_BUILDING.txt.gz](https://launchpadlibrarian.net/70549467/buildlog_ubuntu-natty-i386.mythtv_2%3A0.25.0~master.20110428.cf5a9bc-0ubuntu0mythbuntu2_BUILDING.txt.gz)) it appears that python bindings aren't getting enabled for some reason


# Bindings
bindings_perl             yes
Perl config options       INSTALLDIRS=vendor
bindings_python           no
bindings_php              yes

---

### Post by superm1 on 2011-05-03
Oh, I just noticed a little higher up:


```
WARNING: disabling Python bindings; missing urlgrabber

```

I've committed a change to mythtv-master packaging to add that build-dependency.  Next 0.25 build should be fixed.

[http://bazaar.launchpad.net/~mythbuntu/mythtv/mythtv-master/revision/435](http://bazaar.launchpad.net/~mythbuntu/mythtv/mythtv-master/revision/435)

In the future can you please report these bugs to [http://bugs.launchpad.net/mythbuntu](http://bugs.launchpad.net/mythbuntu)

They're more likely to end up somewhere trackable there.  You just so happened to find a day I was looking at the front page of the forums.

Thanks!

---

