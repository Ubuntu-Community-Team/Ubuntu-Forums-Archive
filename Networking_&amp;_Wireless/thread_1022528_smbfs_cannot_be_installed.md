---
title: "smbfs cannot be installed"
date: 2008-12-26
forum: Networking &amp; Wireless
---

### Post by lacis_alfredo on 2008-12-26
Cannot install smbfs:

```
$ sudo apt-get install samba-common
Reading package lists... Done
Building dependency tree
Reading state information... Done
samba-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
homer@krusty2:/dossy/z_shared/entertain/music
$ sudo apt-get install smbfs
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  smbfs: Depends: samba-common (= 3.0.28a-1ubuntu4) but 3.0.28a-1ubuntu4.7 is to be installed
E: Broken packages
homer@krusty2:/dossy/z_shared/entertain/music
$ 
```

---

### Post by Rocket2DMn on 2008-12-27
Can you please run and post the output of the following commands:
```
sudo apt-get update
sudo apt-get install -f
sudo apt-get upgrade
```
Are you then able to install?

Can you also please clarify what version of Ubuntu you are using.  If you get errors with the above commands, also please post your /etc/apt/sources.list file.

---

