---
title: "Utopic - need to upgrade Gstreamer from 1.2.4 to 1.4.3"
date: 2015-03-04
forum: Multimedia Software
---

### Post by opulentorca on 2015-03-04
I was attempting to install handbrake-gtk via [https://launchpad.net/~stebbins/+archive/ubuntu/handbrake-releases/](https://launchpad.net/~stebbins/+archive/ubuntu/handbrake-releases/) and received a missing dependencies message. Specifically:

The following packages have unmet dependencies:
 handbrake-gtk : Depends: libass5 (>= 0.10.2) but it is not installable
                         Depends: libgstreamer1.0-0 (>= 1.4.0) but 1.2.4-0ubuntu1 is to be installed

Regarding the second, how can one upgrade to version 1.4.3 of gstreamer?

---

### Post by ian-weisser on 2015-03-04
You can either:

1) Search for a PPA that  provides gstreamer 1.4.0 or higher.
2) Upgrade to 15.04 (the pre-release version of Ubuntu), which has 1.4.5.
3) Wait six weeks until 15.04 is released, and upgrade then.

---

### Post by mc4man on 2015-03-04
Are you actually on 14.10 (utopic)? gst 1.2.4 is what trusty is using, utopic is on 1.4.3
[https://launchpad.net/ubuntu/+source/gstreamer1.0](https://launchpad.net/ubuntu/+source/gstreamer1.0)

---

### Post by opulentorca on 2015-03-06
Good catch - I was mistaken - I am currently only on 14.04 ( hence the confusion ). Thanks so much!

---

