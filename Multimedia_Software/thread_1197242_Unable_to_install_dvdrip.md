---
title: "Unable to install dvd::rip"
date: 2009-06-25
forum: Multimedia Software
---

### Post by Oldhacker on 2009-06-25
I attempted to install dvd::rip using apt-get install, and this is what I received -----

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
  dvdrip: Depends: transcode (>= 2:1.0.2-0.8) but it is not going to be installed
          Depends: libevent-execflow-perl (>= 0.63) but it is not going to be installed
          Recommends: subtitleripper but it is not going to be installed
E: Broken packages

---

