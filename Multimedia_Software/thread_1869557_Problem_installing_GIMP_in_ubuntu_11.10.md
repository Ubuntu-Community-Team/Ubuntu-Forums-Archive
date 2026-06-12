---
title: "Problem installing GIMP in ubuntu 11.10"
date: 2011-10-25
forum: Multimedia Software
---

### Post by Red Razor on 2011-10-25
Linux newbie here...Tried to install Gimp on ubuntu 11.10 using the ubuntu software center and got errors.  I then went to the terminal and tried > sudo apt-get -f install and got:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  gimp-help-en gimp-help libgimp-perl gimp-gap gimp-console
The following packages will be upgraded:
  gimp
1 upgraded, 0 newly installed, 0 to remove and 96 not upgraded.
4 not fully installed or removed.
Need to get 0 B/4,294 kB of archives.
After this operation, 369 kB disk space will be freed.
(Reading database ... 150109 files and directories currently installed.)
Preparing to replace gimp 2.6.11-2ubuntu4 (using .../gimp_2.7.4-2011102201~oo_i386.deb) ...
Unpacking replacement gimp ...
dpkg: error processing /var/cache/apt/archives/gimp_2.7.4-2011102201~oo_i386.deb (--unpack):
 trying to overwrite '/usr/lib/gimp/2.0/plug-ins/file-xmc', which is also in package gimp-plugin-registry 3.5.4-1
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for man-db ...
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Errors were encountered while processing:
 /var/cache/apt/archives/gimp_2.7.4-2011102201~oo_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I also get an error message now as soon as I open the Ubuntu Software Center that says: > Items cannot be installed or removed until the package catalog is repaired. Clicking the Repair button is no help.

Any ideas on what I'm missing and how I can either uninstall or complete the install. 

Thanks, 
Red Razor

---

