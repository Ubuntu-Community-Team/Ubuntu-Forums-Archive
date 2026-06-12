---
title: "Problem after upgrade"
date: 2010-08-04
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Tompalaz on 2010-08-04
Hey. Recently I got a problem after a upgrade process that I had to cancel. It just downloaded the packages so I figured it would be okay to abort it.

The following problem I have is: 

> Need to get 0B/69.7MB of archives.
After this operation, 100MB disk space will be freed.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
tar: Skipping to next header
tar: Exiting with failure status due to previous errors
dpkg-deb: subprocess tar returned error exit status 2
dpkg: error processing /var/cache/apt/archives/dpkg_1.15.8.2ubuntu3_amd64.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
configured to not write apport reports
                                      Errors were encountered while processing:
 /var/cache/apt/archives/dpkg_1.15.8.2ubuntu3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I have run
apt-get autoclean
apt-get clean

I've also removed all the packages in /var/cache/apt/archives/

Any ideas?

---

### Post by 23dornot23d on 2010-08-04
apt-get -f install

should fix the broken install problems

then if you want to carry on the upgrade .... do the following .....
__________________________

apt-get install aptitude

aptitude safe-upgrade

is the way I would try ........ if you are still wanting to continue the upgrade

---

### Post by Tompalaz on 2010-08-04
Thank you for answering.

Problems when I try to install aptitude

> Errors were encountered while processing:
 /var/cache/apt/archives/libboost-iostreams1.42.0_1.42.0-3ubuntu1_amd64.deb
 /var/cache/apt/archives/libcwidget3_0.5.16-3ubuntu1_amd64.deb
 /var/cache/apt/archives/aptitude_0.6.3-2ubuntu3_amd64.deb
 /var/cache/apt/archives/libsub-name-perl_0.04-1build1_amd64.deb
 /var/cache/apt/archives/libclass-accessor-perl_0.34-1_all.deb
 /var/cache/apt/archives/libio-string-perl_1.08-2_all.deb
 /var/cache/apt/archives/libparse-debianchangelog-perl_1.1.1-2ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Same thing even if I clean everything.

---

### Post by 23dornot23d on 2010-08-04
what was the output when you did this

apt-get -f install

---

### Post by Tompalaz on 2010-08-04
> tomas@MacBook:~/Downloads$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 128 not upgraded.
tomas@MacBook:~/Downloads$ 

However, when I ran that before I got a different output.

> tomas@MacBook:~/Downloads$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 128 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up libenca0 (1.13-2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

---

### Post by cariboo on 2010-08-04
From the looks of, the command did it's job. Can you install anything now?

---

### Post by Tompalaz on 2010-08-04
> **cariboo907 said:**
> From the looks of, the command did it's job. Can you install anything now?

No, same errors again.

> tomas@MacBook:~/Downloads$ sudo apt-get install aptitude
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libboost-iostreams1.42.0 libclass-accessor-perl libcwidget3
  libio-string-perl libparse-debianchangelog-perl libsub-name-perl
Suggested packages:
  aptitude-doc-en aptitude-doc tasksel debtags libcwidget-dev
  libhtml-template-perl libxml-simple-perl
The following NEW packages will be installed:
  aptitude libboost-iostreams1.42.0 libclass-accessor-perl libcwidget3
  libio-string-perl libparse-debianchangelog-perl libsub-name-perl
0 upgraded, 7 newly installed, 0 to remove and 128 not upgraded.
Need to get 2,789kB of archives.
After this operation, 8,581kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 [...]
Fetched 2,789kB in 9s (292kB/s)                                                
(Reading database ... 208560 files and directories currently installed.)
Unpacking libboost-iostreams1.42.0 (from .../libboost-iostreams1.42.0_1.42.0-3ubuntu1_amd64.deb) ...
Unpacking libcwidget3 (from .../libcwidget3_0.5.16-3ubuntu1_amd64.deb) ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:0>: invalid distance too far back'
dpkg-deb: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/libcwidget3_0.5.16-3ubuntu1_amd64.deb (--unpack):
 short read on buffer copy for backend dpkg-deb during `./usr/lib/libcwidget.so.3.0.0'
configured to not write apport reports
                                      tar: Skipping to next header
tar: Exiting with failure status due to previous errors
dpkg-deb: subprocess tar returned error exit status 2
dpkg: error processing /var/cache/apt/archives/aptitude_0.6.3-2ubuntu3_amd64.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
configured to not write apport reports
                                      Unpacking libsub-name-perl (from .../libsub-name-perl_0.04-1build1_amd64.deb) ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:0>: invalid distance too far back'
dpkg-deb: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/libsub-name-perl_0.04-1build1_amd64.deb (--unpack):
 short read on buffer copy for backend dpkg-deb during `./usr/lib/perl5/auto/Sub/Name/Name.so'
configured to not write apport reports
                                      Unpacking libclass-accessor-perl (from .../libclass-accessor-perl_0.34-1_all.deb) ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:0>: invalid distance too far back'
dpkg-deb: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/libclass-accessor-perl_0.34-1_all.deb (--unpack):
 short read on buffer copy for backend dpkg-deb during `./usr/share/man/man3/Class::Accessor.3pm.gz'
configured to not write apport reports
                                      Unpacking libio-string-perl (from .../libio-string-perl_1.08-2_all.deb) ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:0>: data error'
dpkg-deb: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/libio-string-perl_1.08-2_all.deb (--unpack):
 short read on buffer copy for backend dpkg-deb during `./usr/share/perl5/IO/String.pm'
configured to not write apport reports
                                      Unpacking libparse-debianchangelog-perl (from .../libparse-debianchangelog-perl_1.1.1-2ubuntu2_all.deb) ...
dpkg: error processing /var/cache/apt/archives/libparse-debianchangelog-perl_1.1.1-2ubuntu2_all.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
configured to not write apport reports
                                      Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/libcwidget3_0.5.16-3ubuntu1_amd64.deb
 /var/cache/apt/archives/aptitude_0.6.3-2ubuntu3_amd64.deb
 /var/cache/apt/archives/libsub-name-perl_0.04-1build1_amd64.deb
 /var/cache/apt/archives/libclass-accessor-perl_0.34-1_all.deb
 /var/cache/apt/archives/libio-string-perl_1.08-2_all.deb
 /var/cache/apt/archives/libparse-debianchangelog-perl_1.1.1-2ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by 23dornot23d on 2010-08-04
How much space is left on the drive > ?

df

---

### Post by Tompalaz on 2010-08-04
> **23dornot23d said:**
> How much space is left on the drive > ?

df

tomas@MacBook:~/Downloads$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda3              11G   4.3G   5.4G  45% /
none                   901M   271k   901M   1% /dev
none                   908M   1.5M   907M   1% /dev/shm
none                   908M   111k   908M   1% /var/run
none                   908M      0   908M   0% /var/lock
none                   908M      0   908M   0% /lib/init/rw
/dev/sda5               24G   6.5G    18G  28% /home

Should be enough.

---

### Post by ranch hand on 2010-08-04
Have you run;
```

sudo dpkg --configure -a

```
?

It is sometimes a good idea to run that 2 or 3 times or until it comes out with the same results twice.

To do an upgrade you also really need to run dist-upgrade instead of just upgrade in apt.

---

### Post by Tompalaz on 2010-08-04
> **ranch hand said:**
> Have you run;
```

sudo dpkg --configure -a

```
?


It is sometimes a good idea to run that 2 or 3 times or until it comes out with the same results twice.


That didn't work :/ 
Gave no output.
tomas@MacBook:~/Downloads$ sudo dpkg --configure -a
tomas@MacBook:~/Downloads$ sudo dpkg --configure -a
tomas@MacBook:~/Downloads$ sudo dpkg --configure -a
tomas@MacBook:~/Downloads$ 

> To do an upgrade you also really need to run dist-upgrade instead of just upgrade in apt
I'll keep that in mind, can I just ask, what's the difference between them?

I'm starting to think of a total reinstall...

---

### Post by ranch hand on 2010-08-04
A dist-upgrade is the traditional way to upgrade a Debian distribution (not recommended by Ubuntu) that I normally use.

it will install things that would normally be held back on a plain upgrade, which is the tool mainly used for upgrading your OS to current for it.  Anything that requires a new package to be installed with it will be held back.

Some of your errors have to do with the cache files and you said you deleted many of them.  A clean install may be the simplest thing to do.  I assume that you can get to the files you may want to keep for backing them up, from another install or the Live CD.

This is one reason to install on / and /home (backup still a GOOD idea).  If you just format / you will probably loose nothing from home.  You may want to use a different user name so that any screwy config files in /home do not effect the new install.

---

### Post by Tompalaz on 2010-08-05
> **ranch hand said:**
> A dist-upgrade is the traditional way to upgrade a Debian distribution (not recommended by Ubuntu) that I normally use.

it will install things that would normally be held back on a plain upgrade, which is the tool mainly used for upgrading your OS to current for it.  Anything that requires a new package to be installed with it will be held back.

Some of your errors have to do with the cache files and you said you deleted many of them.  A clean install may be the simplest thing to do.  I assume that you can get to the files you may want to keep for backing them up, from another install or the Live CD.

This is one reason to install on / and /home (backup still a GOOD idea).  If you just format / you will probably loose nothing from home.  You may want to use a different user name so that any screwy config files in /home do not effect the new install.

Thank you for the explanation. 
I'll go with a new install.

I always install / and home on different partitions, especially when it's alpha. :)

Thread closed

---

