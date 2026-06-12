---
title: "How change to version 0.26 from the commandline"
date: 2012-10-26
forum: Mythbuntu
---

### Post by ian dobson on 2012-10-26
Hi,

I have a mythtv backend running 12.04/MythTV 0.25 and I'd like to upgrade to 0.26.

The problem is that the backend doesn't have a monitor/keyboard/mouse. In the past I used "dpkg-reconfigure mythbuntu-repos", now it only offrs to use the Updates Repo, rather than which version.

Regards
Ian Dobson

---

### Post by tgm4883 on 2012-10-26
> **ian dobson said:**
> Hi,

I have a mythtv backend running 12.04/MythTV 0.25 and I'd like to upgrade to 0.26.

The problem is that the backend doesn't have a monitor/keyboard/mouse. In the past I used "dpkg-reconfigure mythbuntu-repos", now it only offrs to use the Updates Repo, rather than which version.

Regards
Ian Dobson

```
apt-add-repository ppa:mythbuntu/0.26
```

---

### Post by ian dobson on 2012-10-26
Hi,

OK I'll try that tomorrow. 
Just to confirm that will upgrade to 26 rather that just adding 26, keeping 25 installed.

Regards
Ian Dobson

---

### Post by tgm4883 on 2012-10-26
> **ian dobson said:**
> Hi,

OK I'll try that tomorrow. 
Just to confirm that will upgrade to 26 rather that just adding 26, keeping 25 installed.

Regards
Ian Dobson

That will just add the 0.26 repository. The 0.25 repository will still be installed, and apt will query both for a package list. This doesn't cause issues though as the package names are the same so it will show the packages from the 0.26 repository as newer (since version 0.26 > 0.25). It will slightly increase the length of time it takes to run apt-get update (as it's querying an extra repository), so you can safely remove that by doing

```
apt-add-repository -r ppa:mythbuntu/0.25
```

And since that is only adding (or removing) a repository, and not updating/upgrading any packages, you will still need to do

```
apt-get update
apt-get upgrade
```

Although the latter will likely need a

```
apt-get dist-upgrade
```

as it will require additional packages to be installed to satisfy the new dependencies in 0.26

---

