---
title: "problem rebuilding package"
date: 2011-01-24
forum: Mythbuntu
---

### Post by tritron on 2011-01-24
I wonder if someone can point me changes I need to make in order to fix  this error I am getting when I am attempting to rebuild package. I
usr/share/perl5/MythTV.pm exists in debian/tmp but is not installed 
h_install: usr/share/perl5/IO/Socket/INET/MythTV.pm exists in debian/tmp but is not installed to anywhere
dh_install: usr/share/perl5/MythTV/Channel.pm exists in debian/tmp but is not installed to anywhere
dh_install: usr/share/perl5/MythTV/Program.pm exists in debian/tmp but is not installed to anywhere
dh_install: usr/share/perl5/MythTV/Recording.pm exists in debian/tmp but is not installed to anywhere
dh_install: usr/share/perl5/MythTV/StorageGroup.pm exists in debian/tmp but is not installed to anywhere
dh_install: missing files, aborting
make[1]: *** [override_dh_install] Error 9

---

### Post by nickrout on 2011-01-24
Do you mean you are buiilding mythtv from source?

---

