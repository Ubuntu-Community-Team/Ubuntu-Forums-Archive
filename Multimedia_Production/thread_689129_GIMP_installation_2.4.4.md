---
title: "GIMP installation 2.4.4"
date: 2008-02-06
forum: Multimedia Production
---

### Post by ssuuddoo on 2008-02-06
Hi, it is not as hard, as it seems.

I used to download the source code from the gimp.org site, and tried to compile it on my own, installed tons of other ...-dev dependencies and applications, but errors were bigger than me and my google-find-solution capabilities.

Here on ubuntuforums people often share compiling problems.

[COLOR="Red"]BUT you can just download the testing packages from
the packages.debian.org site and install some dependencies and it works.[/COLOR]
...I did not search there before, since the packages were not in the official ubuntu depository and I didnt find any other repository server (on ubuntu repository even though I have the prerelease and unstable packages in synaptic checked, the newest version is 2.4.2).

for the GIMP 2.4.4 you just need to download the following packages:

gimp_2.4.4-1_i386.deb
gimp-data_2.4.4-1_all.deb
libgimp2.0_2.4.4-1_i386.deb

and some dependencies:
libc6_2.7-6_i386.deb
libhal1_0.5.10-5_i386.deb
libdatrie0_0.1.2-2_i386.deb
libpango1.0-0_1.18.4-1_i386.deb
libpango1.0-common_1.18.4-1_all.deb
tzdata_2007k-3_all.deb
(these dependent packages depend on your system, its configuration and installed packages).

first the system wrote a lots of packages and wanted to remove about 150 other packages, but step-by-step I installed gimp 2.4.4 without bigger problems.

thumbs up!

---

### Post by ssuuddoo on 2008-02-06
..after that I needed 2 install some other packages, so I've downloaded them and installed..


libc6-dev_2.7-6_i386.deb
libc6-i686_2.7-6_i386.deb
libgimp2.0-dev_2.4.4-1_i386.deb
libhal-dev_0.5.10-5_i386.deb
libpango1.0-dev_1.18.4-1_i386.deb

...so no big deal

BUT, for sure, be sure U have a BACKUP of things U need from your comp while "playing" with the system packages. xixi :D

---

