---
title: "envy script won't install"
date: 2007-03-19
forum: Multimedia &amp; Video
---

### Post by Charles Hand on 2007-03-19
Can someone help with this?

```
charlie@gemini:~$ sudo dpkg -i envy_0.9.1-0ubuntu3_all.deb
Selecting previously deselected package envy.
(Reading database ... 373459 files and directories currently installed.)
Unpacking envy (from envy_0.9.1-0ubuntu3_all.deb) ...
dpkg: dependency problems prevent configuration of envy:
 envy depends on xserver-xorg-dev; however:
  Package xserver-xorg-dev is not installed.
dpkg: error processing envy (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 envy
```

```

charlie@gemini:~$ sudo apt-get install xserver-xorg-dev
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  xserver-xorg-dev: Depends: libdrm-dev but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

```

charlie@gemini:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  envy
0 upgraded, 0 newly installed, 1 to remove and 5 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 1241kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 373575 files and directories currently installed.)
Removing envy ...

```

```

charlie@gemini:~$ sudo apt-get install xserver-xorg-dev
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  xserver-xorg-dev: Depends: libdrm-dev but it is not going to be installed
E: Broken packages

```

```

charlie@gemini:~$ sudo apt-get install libdrm-dev
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libdrm-dev: Depends: libdrm2 (= 2.0-0ubuntu1) but 2.0.2+cvs20060824 is to be installed
E: Broken packages

```

Then if I go to uninstall libdrm2 in order to install the requested version, it turns out half the applications on the computer depend on libdrm-dev. My hunch is I don't want to uninstall all those applications. Or should I?

---

### Post by r4ik on 2007-03-19
It would not be the first time i missed something but simply click,


envy_0.9.1-0ubuntu3_all.deb

on the page should install what you want.

---

### Post by Charles Hand on 2007-03-19
That's what I did at first, and it failed. That's why I went to the command line to try to get some info about what was wrong.

"Error: Cannot install xserver-xorg-dev"

---

### Post by Charles Hand on 2007-03-22
The only thing I can figure is, this is what is meant by "dapper support temporarily disabled". I installed edgy from scratch, and afterwards the envy script installs ok.

---

### Post by phillipsrich on 2007-07-31
I have removed Beryl, had two of 3 compiz packages loaded.  Now what do I do?  I've tried just about everything?  Is there a work around?

user@system:~/Desktop$ sudo dpkg -i envy*.deb
Selecting previously deselected package envy.
(Reading database ... 191520 files and directories currently installed.)
Unpacking envy (from envy_0.9.7-0ubuntu3_all.deb) ...
dpkg: dependency problems prevent configuration of envy:
 envy depends on xserver-xorg-dev; however:
  Package xserver-xorg-dev is not installed.
dpkg: error processing envy (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 envy
user@system:~/Desktop$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  envy
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 2712kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 191869 files and directories currently installed.)
Removing envy ...
user@system:~/Desktop$ sudo apt-get install xserver-xorg-dev
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  xserver-xorg-dev: Depends: libdrm-dev but it is not going to be installed
E: Broken packages
user@system:~/Desktop$ sudo apt-get install libdrm-dev
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libdrm-dev: Depends: libdrm2 (= 2.0-0ubuntu1) but 2.0.2+cvs20060824 is to be installed
E: Broken packages

user@system:~/Desktop$ sudo apt-get install libdrm2
Reading package lists... Done
Building dependency tree... Done
libdrm2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

