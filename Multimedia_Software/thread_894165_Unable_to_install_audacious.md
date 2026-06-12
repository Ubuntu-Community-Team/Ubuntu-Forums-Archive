---
title: "Unable to install audacious"
date: 2008-08-19
forum: Multimedia Software
---

### Post by betawind on 2008-08-19
Whenever I try to install Audacious from the repositories I get the below:

Any thoughts?


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
  audacious: Depends: audacious-plugins but it is not going to be installed
E: Broken packages

---

### Post by kostkon on 2008-08-19
> **betawind said:**
> Whenever I try to install Audacious from the repositories I get the below:

Any thoughts?


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
  audacious: Depends: audacious-plugins but it is not going to be installed
E: Broken packages
Go to *System -> Administration -> Software Sources* and enable all your repositories (i.e. *main*, *universe*, *multiverse*, *restricted*) and then try again to install *Audacious*.

---

### Post by betawind on 2008-08-19
Already enabled :(  Any other thoughts?

---

