---
title: "Squeezecenter crashes on 8.10 64bit"
date: 2008-12-28
forum: Multimedia Software
---

### Post by oliwel on 2008-12-28
Hi All,

I migrated my old gentoo fileserver to ubuntu intrepid this days and run into a problem with Logitechs "Squeezecenter" Software.

I installed it by apt-get using the provided repository at [http://debian.slimdevices.com](http://debian.slimdevices.com) - I tried stable and testing - results are the same.

Installation works, I can also start the server and access it via the browser to make my settings. As far as I can see, the errors occur when I start more than one network connection to the server, which happens already when clicking around in the GUI. 

I see this in my squeezecenter/server.log

```
Slim::Networking::IO::Select::select (271) Error: Select task failed: Not a reference at /usr/share/perl5/Slim/Utils/Prefs.pm line 342.
```

network connections start to timeout and I have to restart the server process to get it up working again.

Anybody has seen this so far or can point me to any useful resources?
NB: perl-gd as noted here [http://wiki.slimdevices.com/index.php/DebianPackage](http://wiki.slimdevices.com/index.php/DebianPackage) is already installed.

TIA Oliver

---

### Post by oliwel on 2008-12-31
Meanwhile, I fetched the 7.2.1 debian package by hand and its working without any problems.

---

### Post by oliwel on 2009-01-10
If anybody stumbles here - I filed a request agains Logitech and they opened a bugzilla thread for it: [http://bugs.slimdevices.com/show_bug.cgi?id=10628](http://bugs.slimdevices.com/show_bug.cgi?id=10628)

Oliver

---

