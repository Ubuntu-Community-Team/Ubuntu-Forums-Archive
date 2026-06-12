---
title: "Gramofile won't install"
date: 2007-07-27
forum: Multimedia &amp; Video
---

### Post by meanmrmustard on 2007-07-27
In attempting to install the program, I get this:
```

The following packages have unmet dependencies:
  x11-common: Conflicts: mctools-lite (<= 970129-16) but 970129-15 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
mctools-lite [Not Installed]

Leave the following dependencies unresolved:
gramofile recommends mctools-lite
Score is -141

Accept this solution? [Y/n/q/?] 

```

I try installing mctools-lite and I find that x11-common is broken:
```
The following packages are BROKEN:
  x11-common 
The following NEW packages will be automatically installed:
  cddb 
The following NEW packages will be installed:
  cddb mctools-lite 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 233kB of archives. After unpacking 627kB will be used.
The following packages have unmet dependencies:
  x11-common: Conflicts: mctools-lite (<= 970129-16) but 970129-15 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
mctools-lite [Not Installed]

Score is -10001

Accept this solution? [Y/n/q/?]
```

I run synaptic with the 'broken' filter and it comes up with nothing.

Where do I go from here?

TIA
Mr M.

---

### Post by meanmrmustard on 2007-07-29
Bump.... anyone got an idea?

---

