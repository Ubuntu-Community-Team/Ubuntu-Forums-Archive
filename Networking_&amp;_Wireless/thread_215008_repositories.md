---
title: "repositories"
date: 2006-07-13
forum: Networking &amp; Wireless
---

### Post by mco on 2006-07-13
Yesterday I changed the configuration of the repositories file following somebody's advice... now I have the following problems in Synaptic:

Can anybody help me reseting the repositories list?  Thanks in advance

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_restricted_binary-i386_Packages)

---

### Post by neilp85 on 2006-07-13
I recommend replacing your sources.list file with the one found here:
[http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories)

That will get rid of the duplicate listings and add all the repositories you should need.

---

