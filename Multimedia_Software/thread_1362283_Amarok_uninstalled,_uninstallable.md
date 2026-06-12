---
title: "Amarok uninstalled, uninstallable"
date: 2009-12-22
forum: Multimedia Software
---

### Post by Gitykins on 2009-12-22
I recently built a new computer for myself for christmas and just switched over my drives to the new one and booted it up. I noticed Amarok was suddenly gone, so I went terminal and typed in:

sudo apt-get install amarok

and got:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  amarok: Depends: kdebase-runtime (>= 4:4.3.3) but 4:4.3.2-0ubuntu4.1 is to be installed
          Depends: kdelibs5 (>= 4:4.3.3) but 4:4.3.2-0ubuntu7.2 is to be installed
          Depends: libplasma3 (>= 4:4.3.3-0ubuntu1~ppa1) but 4:4.3.2-0ubuntu7.2 is to be installed
E: Broken packages

---

### Post by mc4man on 2009-12-23
Check your sources and ppa's, (kubuntu beta backports ..?) and run an update 

The amarok available to install is requiring kde  libs in higher versions than karmic provides (more like lucid or the above mentioned

---

