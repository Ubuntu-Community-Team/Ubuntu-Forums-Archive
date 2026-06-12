---
title: "Cannot install VLC in Ubuntu Server 14.10"
date: 2014-11-25
forum: Multimedia Software
---

### Post by dqvinh87 on 2014-11-25
Today I updated my Ubuntu Server from 14.04 to 14.10, and now I cannot install VLC.

When I tried:
sudo apt-get install vlc

I see the error:

The following packages have unmet dependencies:
 vlc : Depends: libgles1-mesa (>= 7.8.1) but it is not going to be installed or
                libgles1


I tried with some related threads, but nothing helps, this error still appears.

Any suggestion is appreciated.

Thank you very much

---

### Post by slickymaster on 2014-11-25
Hi dqvinh87, welcome to the forums.

Have you already have a read through this thread: [http://ubuntuforums.org/showthread.php?t=2250015](http://ubuntuforums.org/showthread.php?t=2250015)

---

### Post by dqvinh87 on 2014-11-25
Hi

I tried as instructed in the thread you mentioned.

When I typed:

```

apt-cache policy libgl1-mesa-glx libglapi-mesa

```

The output is:

> 
libgl1-mesa-glx:
  Installed: 10.5.0~git20141122.3d9c1a9d-0ubuntu0ricotz~trusty
  Candidate: 10.5.0~git20141122.3d9c1a9d-0ubuntu0ricotz~trusty
  Version table:
 *** 10.5.0~git20141122.3d9c1a9d-0ubuntu0ricotz~trusty 0
        100 /var/lib/dpkg/status
     10.3.0-0ubuntu3 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) utopic/main amd64 Packages
libglapi-mesa:
  Installed: 10.5.0~git20141122.3d9c1a9d-0ubuntu0ricotz~trusty
  Candidate: 10.5.0~git20141122.3d9c1a9d-0ubuntu0ricotz~trusty
  Version table:
 *** 10.5.0~git20141122.3d9c1a9d-0ubuntu0ricotz~trusty 0
        100 /var/lib/dpkg/status
     10.3.0-0ubuntu3 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) utopic/main amd64 Packages




---

### Post by slickymaster on 2014-11-25
> **dqvinh87 said:**
> Hi

I tried as instructed in the thread you mentioned.

When I typed:

```

apt-cache policy libgl1-mesa-glx libglapi-mesa

```

The output is:

Did you add the xorg-edgers PPA to your system before running that command?

**apt-cache** by itself does not manipulate/install anything on the system. It just provide operations to search and generate output from the package metadata. In this case the **policy** option prints out detailed information about the priority selection of those packages.

---

### Post by mc4man on 2014-11-25
In other words -
If you have xorger ppa packages & are upgrading to a new  Ubuntu release, then either 

1. Use ppa-purge before  the  upgrade 
Or
2. Right after the upgrade add back the xorger's ppa, then update source's  & install the xorger's  versions for your current  release

---

### Post by dqvinh87 on 2014-11-26
> **mc4man said:**
> In other words -
If you have xorger ppa packages & are upgrading to a new  Ubuntu release, then either 

1. Use ppa-purge before  the  upgrade 
Or
2. Right after the upgrade add back the xorger's ppa, then update source's  & install the xorger's  versions for your current  release

Hello all,

1. Yeah, I added the PPA mentioned in the thread already.
2. How to use ppa-purge, could you make it a little bit more details?

---

### Post by slickymaster on 2014-11-26
> **dqvinh87 said:**
> Hello all,

1. Yeah, I added the PPA mentioned in the thread already.
2. How to use ppa-purge, could you make it a little bit more details?

The ppa-purge package disables a PPA and reverts it to the official package if applicable. For example, if you added the xorg-edgers PPA and installed the Nvidia drivers, when you run a ppa-purge on the xorg-edgers PPA, it would not only disable it but also will revert the NVIDIA drivers from the one in the PPA to the official ones found on the official Ubuntu repositories.

To install the ppa-purge package:```
sudo apt-get update && sudo apt-get install ppa-purge
```
To use against xorg-edgers:```
sudo ppa-purge ppa:xorg-edgers/ppa
```

---

