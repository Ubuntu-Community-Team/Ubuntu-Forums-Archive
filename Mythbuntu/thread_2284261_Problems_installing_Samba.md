---
title: "Problems installing Samba"
date: 2015-06-28
forum: Mythbuntu
---

### Post by z7APXKm on 2015-06-28
Hi,

Having trouble installing Samba on my media PC:

Ubuntu 12.04.2 LTS \n \l

```
# apt-get install samba

Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 samba : Depends: heimdal-hdb-api-8 but it is not installable
         Depends: lsb-base (>= 4.1+Debian) but 4.0-0ubuntu20.2 is to be installed
         Depends: python-samba but it is not going to be installed
         Depends: samba-common-bin (= 2:4.1.18+dfsg-3~inverse1)
         Depends: samba-dsdb-modules but it is not going to be installed
         Depends: samba-libs (= 2:4.1.18+dfsg-3~inverse1) but it is not going to be installed
         Recommends: attr
         Recommends: samba-vfs-modules but it is not going to be installed
E: Unable to correct problems, you have held broken packages.



```

Have tried this:

```
# apt-get -o Debug::pkgProblemResolver=yes dist-upgrade

Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Starting
Starting 2
Investigating (0) libsmbclient [ amd64 ] < 2:3.6.3-2ubuntu2.6 -> 2:4.1.18+dfsg-3~inverse1 > ( libs )
Broken libsmbclient:amd64 Depends on samba-libs [ amd64 ] < none -> 2:4.1.18+dfsg-3~inverse1 > ( libs ) (= 2:4.1.18+dfsg-3~inverse1)
  Considering samba-libs:amd64 1 as a solution to libsmbclient:amd64 7
  Holding Back libsmbclient:amd64 rather than change samba-libs:amd64
 Try to Re-Instate (1) libsmbclient:amd64
Done
Done
The following packages have been kept back:
  libsmbclient
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

I suspect this is because I have run [COLOR=#111111][FONT=Consolas]apt-get dist-upgrade[/FONT][/COLOR] when upgrading Myth, which was possibly not the smartest thing to do.

Any help appreciated.

---

### Post by TheFu on 2015-06-28
The dist-upgrade didn't cause this.
Have you installed any packages directly - by downloading a .deb file?  
Or are there any PPAs in the APT sources that are not from Canonical approved sources?  When it comes to dependencies - those are the reasons - some package was installed and it had a specific dependency that cannot be removed until the package is removed. 

Try using **aptitude** instead of apt-get - it can sometimes figure out solutions that other tools miss.

---

### Post by z7APXKm on 2015-06-28
Not installed any .deb files (that I remember), but I think there's probably other repositories in there:

```
# apt-cache policy

Package files:
 100 /var/lib/dpkg/status
     release a=now
 500 http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/ precise/main i386 Packages
     release v=12.04,o=LP-PPA-ubuntu-audio-dev,a=precise,n=precise,l=Ubuntu Audio Dev team PPA,c=main
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/ precise/main amd64 Packages
     release v=12.04,o=LP-PPA-ubuntu-audio-dev,a=precise,n=precise,l=Ubuntu Audio Dev team PPA,c=main
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/ precise/main Translation-en
 500 http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/ precise/main i386 Packages
     release v=12.04,o=LP-PPA-team-xbmc,a=precise,n=precise,l=XBMC PPA,c=main
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/ precise/main amd64 Packages
     release v=12.04,o=LP-PPA-team-xbmc,a=precise,n=precise,l=XBMC PPA,c=main
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu/ precise/main i386 Packages
     release v=12.04,o=LP-PPA-stebbins-handbrake-snapshots,a=precise,n=precise,l=HandBrake Snapshots,c=main
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu/ precise/main amd64 Packages
     release v=12.04,o=LP-PPA-stebbins-handbrake-snapshots,a=precise,n=precise,l=HandBrake Snapshots,c=main
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/ precise/main i386 Packages
     release v=12.04,o=LP-PPA-stebbins-handbrake-releases,a=precise,n=precise,l=HandBrake Releases,c=main
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/ precise/main amd64 Packages
     release v=12.04,o=LP-PPA-stebbins-handbrake-releases,a=precise,n=precise,l=HandBrake Releases,c=main
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/richardgv/compton/ubuntu/ precise/main Translation-en
 500 http://ppa.launchpad.net/richardgv/compton/ubuntu/ precise/main i386 Packages
     release v=12.04,o=LP-PPA-richardgv-compton,a=precise,n=precise,l=compton,c=main
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/richardgv/compton/ubuntu/ precise/main amd64 Packages
     release v=12.04,o=LP-PPA-richardgv-compton,a=precise,n=precise,l=compton,c=main
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/mythbuntu/0.27/ubuntu/ precise/main Translation-en
 500 http://ppa.launchpad.net/mythbuntu/0.27/ubuntu/ precise/main i386 Packages
     release v=12.04,o=LP-PPA-mythbuntu-0.27,a=precise,n=precise,l=0.27,c=main
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/mythbuntu/0.27/ubuntu/ precise/main amd64 Packages
     release v=12.04,o=LP-PPA-mythbuntu-0.27,a=precise,n=precise,l=0.27,c=main
     origin ppa.launchpad.net
 500 http://webmin.mirror.somersettechsolutions.co.uk/repository/ sarge/contrib i386 Packages
     release v=3.1,o=Jamie Cameron,a=stable,n=sarge,l=Webmin,c=contrib
     origin webmin.mirror.somersettechsolutions.co.uk
 500 http://webmin.mirror.somersettechsolutions.co.uk/repository/ sarge/contrib amd64 Packages
     release v=3.1,o=Jamie Cameron,a=stable,n=sarge,l=Webmin,c=contrib
     origin webmin.mirror.somersettechsolutions.co.uk
 500 http://download.webmin.com/download/repository/ sarge/contrib i386 Packages
     release v=3.1,o=Jamie Cameron,a=stable,n=sarge,l=Webmin,c=contrib
     origin download.webmin.com
 500 http://download.webmin.com/download/repository/ sarge/contrib amd64 Packages
     release v=3.1,o=Jamie Cameron,a=stable,n=sarge,l=Webmin,c=contrib
     origin download.webmin.com

```

Also, no aptitude at this stage:

```
# apt-get install aptitude
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package aptitude is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'aptitude' has no installation candidate



```


Now I'm seeing different behaviour:

```

# apt-get install samba
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package samba is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'samba' has no installation candidate

# apt-get install samba-common
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package samba-common is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'samba-common' has no installation candidate
#




```

**edit:**

Having just run apt-get update and then apt-get install samba I'm back to the original issue with unmet dependencies.

---

### Post by z7APXKm on 2015-06-28
Have backed up and then deleted my etc/apt/sources.list file and recreated from the default.

The latest error is:

```
# apt-get install samba
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 samba : Depends: libwbclient0 (= 2:3.6.3-2ubuntu2) but 2:4.1.18+dfsg-3~inverse1 is to be installed
         Recommends: tdb-tools but it is not going to be installed
E: Unable to correct problems, you have held broken packages.



```

---

### Post by z7APXKm on 2015-06-28
Ah!  Removing [COLOR=#000000][FONT=Ubuntu Mono]libwbclient0  [/FONT][/COLOR]seems to be helping.  (Sorry for live-blogging this)...

---

