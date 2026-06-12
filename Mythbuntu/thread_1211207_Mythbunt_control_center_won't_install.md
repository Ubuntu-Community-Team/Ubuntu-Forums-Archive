---
title: "Mythbunt control center won't install"
date: 2009-07-12
forum: Mythbuntu
---

### Post by korgman on 2009-07-12
I did an update with Mythbuntu and everything updates except the control center.    When it tries to install I get a dialog that says:

/var/cache/apt/archives/mythbuntu-control-centre_0.37-0ubuntu1_all.deb: subprocess pre-installation script returned error exit status 2.

Another window says:
Update is complete
Not all changes and updates succeeded. For further details of the failure, please expand the details panel
```

(Reading database ... 176953 files and directories currently installed.)
Preparing to replace mythbuntu-control-centre 0.31-0ubuntu1.1~ppa1 (using .../my
thbuntu-control-centre_0.37-0ubuntu1_all.deb) ...
Adding `diversion of /usr/share/mythtv/main_settings.xml to /usr/share/mythtv/ma
in_settings.xml.diverted by mythbuntu-control-centre'
dpkg-divert: rename involves overwriting `/usr/share/mythtv/main_settings.xml.di
verted' with
  different file `/usr/share/mythtv/main_settings.xml', not allowed
dpkg: error processing /var/cache/apt/archives/mythbuntu-control-centre_0.37-0ub
untu1_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/mythbuntu-control-centre_0.37-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```

---

### Post by korgman on 2009-07-12
Well, I worked around it.  I just renamed the main_settings.xml.diverted file to something else and the install completed.

---

### Post by kickinthethroat on 2009-11-30
Thanks for this! I had the exact same problem...

---

