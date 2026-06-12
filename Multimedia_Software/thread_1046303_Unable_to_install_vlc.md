---
title: "Unable to install vlc"
date: 2009-01-21
forum: Multimedia Software
---

### Post by Unr3a1r00t on 2009-01-21
this is the after doing sudo apt-get install vlc
 
 
 
root@ubuntu:/home/different# sudo apt-get install vlc
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
root@ubuntu:/home/different# sudo apt-get install vlc
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
  vlc: Depends: vlc-nox (= 0.9.4-1ubuntu3) but it is not going to be installed
       Depends: libqtcore4 (>= 4.4.3) but it is not installable
       Depends: libqtgui4 (>= 4.4.3) but it is not installable
       Depends: libsdl-image1.2 (>= 1.2.5) but it is not installable
E: Broken packages

---

### Post by krul on 2009-01-21
I think are mixing up different vlc versions. Try to deinstall everything related to vlc and try again.

---

### Post by ppc_guy on 2009-01-21
Dumb question. Are you installing as root?

Nathan
----------------------------------------------------------
When you are Sierra-Oscar-Lima. I am Hotel-Tango-Hotel.
----------------------------------------------------------

---

### Post by Shazaam on 2009-01-21
```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```
usually means another package manager (Synaptic, the auto-updater) is running. Close them and try again.

---

