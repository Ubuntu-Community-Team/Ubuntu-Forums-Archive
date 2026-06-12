---
title: "Moovida won't start on Lucid"
date: 2010-05-19
forum: Multimedia Software
---

### Post by gayedonn on 2010-05-19
Hi everyone,
All I get is a flash of the splash screen then nothing! I installed it  via Synaptic, I have scoured forums etc and checked everything is  installed.
My pycentral log reads:

2010-05-17 12:53:31 2  moovida-plugins-bad: has no Python-Version field, assuming default  runtime
2010-05-17 12:54:02 2 moovida-plugins-good: has no  Python-Version field, assuming default runtime
2010-05-17 12:54:07 2  moovida-plugins-ugly: has no Python-Version field, assuming default  runtime
2010-05-17 12:54:14 2 python-moovida: has no Python-Version  field, assuming default runtime

Tried via the terminal and got the  following:

Launcher core version: 1.0.9
Current core version:  1.0.9
WARN  MainThread      plugin_registry             May 18  15:18:15  plugin launchpadlib has the following unmet dependencies:  elementtree (elisa/core/plugin_registry.py:372)
WARN  MainThread       plugin_registry             May 18 15:18:15  plugin wadllib has the  following unmet dependencies: elementtree  (elisa/core/plugin_registry.py:372)
WARN  MainThread       plugin_registry             May 18 15:18:15  plugin lazr.restfulclient  has the following unmet dependencies: lazr.restful>=0.9.18  (elisa/core/plugin_registry.py:372)
ERROR: couldn't create the  window, exiting...

I have purged and reinstalled  ..... I'm now  totally exhausted!!!  [IMG]http://www.moovida.com/forums/images/smilies/icon_razz.gif[/IMG]
I am running Ubuntu Lucid 64 bit.
AMD Athlon 64 bit 3500+ MHz
Nvidia Geforce 6150 (on-board video)
1Gb RAM (minus video leaves me 934Mb)

---

### Post by zoubidoo on 2010-07-28
same here.

I think there is a problem with dependencies and elisa needs to be installed.

---

### Post by luigi_mb on 2010-07-28
> **zoubidoo said:**
> same here.

I think there is a problem with dependencies and elisa needs to be installed.

Synaptic does pull in elisa when you try to get moovida. However, have you installed

python-elementtidy

since the errors you report suggest some dependency on elementtree, which is part of python-elementtidy.


/luigi

---

### Post by zoubidoo on 2010-07-28
> **luigi_mb said:**
> Synaptic does pull in elisa when you try to get moovida. 


Nope, not here:

```
$ sudo apt-get remove moovida elisa
[sudo] password for     : 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-tagpy python-pyasn1 python-twisted-web2 python-encutils python-clientform python-twill python-mechanize python-moovida python-configobj python-pgm moovida-plugins-ugly python-twisted-conch python-louie python-nevow
  python-pysqlite2 python-cssutils python-epsilon python-axiom moovida-plugins-good python-coherence libpigment0.3-11 python-gpod python-storm moovida-plugins-bad libboost-python1.40.0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  elisa moovida
0 upgraded, 0 newly installed, 2 to remove and 4 not upgraded.
After this operation, 274kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 163039 files and directories currently installed.)
Removing elisa ...
Removing moovida ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_GB.utf8.cache...
Processing triggers for menu ...
Processing triggers for man-db ...
Processing triggers for python-support ...


$ sudo apt-get install moovida
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  moovida
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
Need to get 0B/26.5kB of archives.
After this operation, 180kB of additional disk space will be used.
Selecting previously deselected package moovida.
(Reading database ... 163018 files and directories currently installed.)
Unpacking moovida (from .../moovida_1.0.9+bzr1614-1ubuntu1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for menu ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_GB.utf8.cache...
Processing triggers for python-support ...
Setting up moovida (1.0.9+bzr1614-1ubuntu1) ...

Processing triggers for menu ...
$

```

Note how elisa wasn't installed.  Definitely a problem if elisa is required.

> **luigi_mb said:**
> However, have you installed

python-elementtidy

since the errors you report suggest some dependency on elementtree, which is part of python-elementtidy.


/luigi
I installed it but am still getting errors:

```
$ moovida
Launcher core version: 1.0.9
Current core version: 1.0.9
WARN  MainThread      plugin_registry             Jul 29 02:48:54  plugin lazr.uri has the following unmet dependencies: distribute (elisa/core/plugin_registry.py:372)
WARN  MainThread      plugin_registry             Jul 29 02:48:54  plugin wadllib has the following unmet dependencies: elementtree (elisa/core/plugin_registry.py:372)
WARN  MainThread      plugin_registry             Jul 29 02:48:54  plugin launchpadlib has the following unmet dependencies: distribute (elisa/core/plugin_registry.py:372)
WARN  MainThread      plugin_registry             Jul 29 02:48:54  plugin networkx has the following unmet dependencies: distribute (elisa/core/plugin_registry.py:372)
WARN  MainThread      plugin_registry             Jul 29 02:48:54  plugin lazr.restfulclient has the following unmet dependencies: van.testing (elisa/core/plugin_registry.py:372)
WARN  coherence                   Jul 29 02:48:55  Coherence UPnP framework version 0.6.6.2 starting... (coherence/base.py:283)
WARN  webserver                   Jul 29 02:48:55  WebServer on port 52887 ready (coherence/base.py:124)
/usr/lib/pymodules/python2.6/elisa/core/service_manager.py:27: DeprecationWarning: ServiceProvider.start is deprecated.
  warn("ServiceProvider.%s is deprecated." % attr, DeprecationWarning)
Traceback (most recent call last):
Failure: exceptions.RuntimeError: hildon not running
[.......]

```

---

### Post by bburgin on 2011-02-07
need some help with this same issue


ATI radeon card
amd 64 bit running 10.04 -  64 bit
fresh install

---

