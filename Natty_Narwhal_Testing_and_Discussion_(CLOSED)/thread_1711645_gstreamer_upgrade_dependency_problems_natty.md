---
title: "gstreamer upgrade dependency problems natty"
date: 2011-03-21
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by garvinrick4 on 2011-03-21
Last upgrades 64-bit from mirror.anl.gov in United States. 1:22 PM March 21
Using: sudo aptitude update && sudo aptitude safe-upgrade

dpkg: dependency problems prevent configuration of gstreamer0.10-plugins-good:
 gstreamer0.10-plugins-bad (0.10.21-1ubuntu5) breaks gstreamer0.10-plugins-good (<< 0.10.28-0ubuntu2) and is installed.
  Version of gstreamer0.10-plugins-good to be configured is 0.10.28-0ubuntu1.
dpkg: error processing gstreamer0.10-plugins-good (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gstreamer0.10-plugins-good
rick@rick-HP:~$

Is it reproduced on other machines?

---

### Post by exploder on 2011-03-21
Yeah, I am getting this.

> An unresolvable problem occurred while calculating the upgrade.

Please report this bug against the 'update-manager' package and include the following error message:
'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'

I am waiting because it is likely that some packages have been held back. I will just wait a while and see if more updates show up.

---

### Post by Harry33 on 2011-03-21
> **garvinrick4 said:**
> Last upgrades 64-bit from mirror.anl.gov in United States. 1:22 PM March 21

dpkg: dependency problems prevent configuration of gstreamer0.10-plugins-good:
 gstreamer0.10-plugins-bad (0.10.21-1ubuntu5) breaks gstreamer0.10-plugins-good (<< 0.10.28-0ubuntu2) and is installed.
  Version of gstreamer0.10-plugins-good to be configured is 0.10.28-0ubuntu1.
dpkg: error processing gstreamer0.10-plugins-good (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gstreamer0.10-plugins-good
rick@rick-HP:~$

Is it reproduced on other machines?

This is because 
the package gstreamer0.10-plugins-good 0.10.28-0ubuntu2
Breaks:
gstreamer0.10-plugins-bad (<< 0.10.21-1ubuntu5)
and
the package gstreamer0.10-plugins-bad 0.10.21-1ubuntu5
Breaks:
gstreamer0.10-plugins-good (<< 0.10.28-0ubuntu2)

The breaks have been dropped from the new packages:
- gst-plugins-bad0.10_0.10.21-1ubuntu6
- gst-plugins-good0.10 0.10.28-0ubuntu3

These updates are already built in Launchpad and should be soon in Natty repos.

---

### Post by garvinrick4 on 2011-03-21
Thank You Harry33 nothing to report then.

---

### Post by Harry33 on 2011-03-21
> **garvinrick4 said:**
> Thank You Harry33 nothing to report then.

Thank You!

Here they are:

[https://launchpad.net/ubuntu/natty/+source/gst-plugins-bad0.10/0.10.21-1ubuntu6](https://launchpad.net/ubuntu/natty/+source/gst-plugins-bad0.10/0.10.21-1ubuntu6)

[https://launchpad.net/ubuntu/natty/+source/gst-plugins-good0.10/0.10.28-0ubuntu3](https://launchpad.net/ubuntu/natty/+source/gst-plugins-good0.10/0.10.28-0ubuntu3)

---

### Post by exploder on 2011-03-21
Thanks! I figured it was just a matter of patience. :D

---

