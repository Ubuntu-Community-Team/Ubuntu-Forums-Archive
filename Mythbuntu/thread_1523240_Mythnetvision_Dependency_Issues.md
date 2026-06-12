---
title: "Mythnetvision Dependency Issues"
date: 2010-07-03
forum: Mythbuntu
---

### Post by uncle hammy on 2010-07-03
A few days ago, I did an update and it ran as a partial upgrade.  When I returned to my frontend, Mythnetvision was no longer present. So I went to the MCC, and tried to reinstall it (it was no longer checked in the plugins section).  Howver, it refuses to install.

Trying to install it from terminal, I get this message...
```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mythnetvision: Depends: libmyth-python (= 0.23.0+fixes25178-0ubuntu0+mythbuntu2) but 0.23.0+fixes25221-0ubuntu0+mythbuntu2 is to be installed
E: Broken packages
```

I figured, oh well, must have hit the upgrades in the middle of being put up.  However, here we are 3 days later, and still can't install mythnetvision, with the exact same error.

Any ideas?

Mythbuntu 10.04 64 bit auto builds.

---

### Post by tgm4883 on 2010-07-03
Mythplugins broke for a few days. I fixed it last night, but it was after the daily build. It should be fixed after todays build.

---

