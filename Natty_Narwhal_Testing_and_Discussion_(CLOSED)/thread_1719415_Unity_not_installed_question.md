---
title: "Unity not installed question"
date: 2011-04-01
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by flintman on 2011-04-01
I have just upgraded from 10.10 to 11.04.  Installation went good no issues.  Restarted my computer and logged into ubuntu not ubuntu classic and it's still gnome nothing different.  I searched and found unity isn't installed.  My question is, is this upgrade suppose to install unity or since I upgraded from 10.10 i need to install?  If i need to install do I just need to install unity and let what ever is required install also?

Thanks

---

### Post by ankspo71 on 2011-04-01
Hi,
I'm not sure, but I think it was supposed to include the Unity desktop during the upgrade process too. I did a clean install of Ubuntu 11.04 so I can't say for certain.

Although, one possible reason for Unity not getting installed can be because prior to upgrading maybe you didn't have a package installed that requires Unity as a dependency, such as 'ubuntu-desktop'. Check to see if you have ubuntu-desktop installed. If it is not installed, installing 'ubuntu-desktop' should correct the problem.

A reverse dependency check for Unity on Ubuntu 11.04 says:
```
james@Ubuntu:~$ apt-cache rdepends unity
unity
Reverse Depends:
  ubuntu-chinese-desktop
  libclutk-0.3-0
  unity-common
  unity-common
  ubuntu-desktop
  netbook-launcher
  libunity3
  libbamf0
 |gnome-session
  compiz-core
```

Those would be all of the packages that require Unity.
Hope this helps.

---

### Post by flintman on 2011-04-01
I installed Unity and Ubuntu-desktop was installed.  After I installed Unity everything works fine now.  Thanks

---

