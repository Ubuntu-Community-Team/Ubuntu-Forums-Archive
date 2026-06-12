---
title: "[Inactive] Error Installing Rhythmbox via Software Center"
date: 2014-03-11
forum: Multimedia Software
---

### Post by Wbie on 2014-03-11
I had messed up and added a PPA ([COLOR=#000000][FONT=UbuntuBeta Mono]jacob/media[/FONT][/COLOR]) which messed up my system to install the latest version of Rhythmbox.  I have removed the PPA from the software sources (and my system entirely).  I think I removed everything associated with Rhythmbox as well but I still can't install the Software Center version.  Here's the text I get when I try:

**[FONT=arial]Package dependencies cannot be resolved[/FONT]**

[FONT=arial]This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.[/FONT]

[FONT=arial]The following packages have unmet dependencies:[/FONT]

[FONT=arial]rhythmbox: Depends: librhythmbox-core7 (= 2.99.1-0ubuntu1) but 2.99.1-0ubuntu1 is to be installed[/FONT]
[FONT=arial]           Depends: libtotem-plparser17 (>= 3.2.0) but 3.4.5-1 is to be installed[/FONT]
[FONT=arial]           Depends: rhythmbox-data (= 2.99.1-0ubuntu1) but 3.0.1-1ubuntu5~ppa0 is to be installed[/FONT]
[FONT=arial]           Depends: gir1.2-rb-3.0 (= 2.99.1-0ubuntu1) but 3.0.1-1ubuntu5~ppa0 is to be installed
- - - - - - - - - - - 
Any help?  It'd be much appreciated and thanks in advance.[/FONT]

---

### Post by Wbie on 2014-03-12
So those items, for whatever reason, uninstalled via apt-get after a restart.  Wish I knew what changed but glad it did nonetheless...

---

### Post by matthewhrose on 2014-03-29
Thanks, I had the same issue and this corrected it!

---

