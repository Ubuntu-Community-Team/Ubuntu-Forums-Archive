---
title: "can't install samba on 11.04"
date: 2011-07-10
forum: Networking &amp; Wireless
---

### Post by LeoEvs on 2011-07-10
Hi everyone.
I'm trying to install samba, but can't because the dependency seems to be more current than the samba requires;
I've tried various repositories but do not fix it.
could someone tell me how to solve this?

```
sudo apt-get install samba
Reading package lists ... ready
Building dependency tree
Reading state information ... ready
Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of the "Incoming".
The following information may help resolve the situation:

The following packages have unmet dependencies:
  samba: Depends: samba-common (= 2:3.5.8~dfsg-1ubuntu2) but 2:3.5.8~dfsg-1ubuntu2.2 is to be installed.
         Depends: libwbclient0 (= 2:3.5.8~dfsg-1ubuntu2) but 2:3.5.8~dfsg-1ubuntu2.2 is to be installed.
E: Broken packages
```

Note that the only difference is 2.2 at the end of the file name. And this two dependancy "2:3.5.8~dfsg-1ubuntu2.2" are already installed.



Thanks in advance.

---

### Post by LeoEvs on 2011-07-10
solved!

I entered the official site of the ubuntu packages ([http://packages.ubuntu.com](http://packages.ubuntu.com)) and add a natty-update's mirror to my sources.list and fix!

just install the samba with same version of dependencies already installed!  (samba_3.5.8~dfsg-1**ubuntu2.2**_i386.deb)

---

