---
title: "error in package totem"
date: 2008-08-30
forum: Multimedia Software
---

### Post by ferd on 2008-08-30
I tried to uninstall package totem using synaptic but I get this error message so I tried to reinstall it and got the same error message and I cannot install any other video player as long as I continue to get this error message. Is it possible to completely remove totem and install another video package? I am using Hardy. Then I tried the fix below.Thanks in advance for all help.:confused::~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up totem-common (2.22.1-0ubuntu2) ...
dpkg: error processing totem-common (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of totem-gstreamer:
 totem-gstreamer depends on totem-common (>= 2.22); however:
  Package totem-common is not configured yet.
 totem-gstreamer depends on totem-common (<< 2.23); however:
  Package totem-common is not configured yet.
dpkg: error processing totem-gstreamer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem-plugins:
 totem-plugins depends on totem-gstreamer (= 2.22.1-0ubuntu2) | totem-xine (= 2.22.1-0ubuntu2); however:
  Package totem-gstreamer is not configured yet.
  Package totem-xine is not installed.
dpkg: error processing totem-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem:
 totem depends on totem-gstreamer (>= 2.22.1-0ubuntu2) | totem-xine (>= 2.22.1-0ubuntu2); however:
  Package totem-gstreamer is not configured yet.
  Package totem-xine is not installed.
 totem depends on totem-plugins (>= 2.22.1-0ubuntu2); however:
  Package totem-plugins is not configured yet.
dpkg: error processing totem (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 totem-common
 totem-gstreamer
 totem-plugins
 totem
E: Sub-process /usr/bin/dpkg returned an error code (1)
Then I tried this. Any other ideas?

---

### Post by wolfen69 on 2008-08-30
try ```
sudo apt-get install -f
```

---

### Post by ferd on 2008-08-30
> **wolfen69 said:**
> try ```
sudo apt-get install -f
```

Thank you. I posted the results of that in my first post.

---

### Post by ferd on 2008-08-31
I reinstalled the offending package to remove it from the auto removable list in synaptic and that solved my problem.

---

