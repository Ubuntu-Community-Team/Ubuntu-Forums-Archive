---
title: "mythbuntu-control-centre python bindings and trunk (0.24) problem"
date: 2010-09-22
forum: Mythbuntu
---

### Post by the_crowbar on 2010-09-22
I am not sure which part of my system is causing my problem so I will probably put too much detail into this post. :)

I have a Mythbuntu 10.04 amd64 system. It started out as my main hard drive in my standalone FE only. I moved the drive to my MBE so I could try out trunk (0.24) to see if it fixed some issues I was having with 0.23.1. I was running 0.23.1 from JYA's repo. I removed all myth related packages before installing the mythbuntu-repos.deb.

0.24-trunk26433 is currently running fine on my MBE and SBE.

The problem I have is mythbuntu-control-centre does nothing. Here is the version:
```

james@james-desktop:~$ dpkg -l | grep mythbuntu-c
ii  mythbuntu-common                      0.50-0ubuntu1                                   Mythbuntu application support functions
ii  mythbuntu-control-centre              0.62-0ubuntu1                                   Mythbuntu Configuration Application

```
and here is the error when mythbuntu-control-centre starts:
```

james@james-desktop:~$ mythbuntu-control-centre 
WARNING: Error loading plugin <class 'jamuconfig.JamuconfigPlugin'>
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/MythbuntuControlCentre/plugin.py", line 75, in find_plugin_instances
    self._instances[plugin] = plugin()
  File "/usr/share/mythbuntu/plugins/python/jamuconfig.py", line 97, in __init__
    if not self.jamuconf.mythdb.getSetting('BackendServerIP', hostname = self.jamuconf.localhostname):
AttributeError: 'MythDB' object has no attribute 'getSetting'
CRITICAL: MythTV python bindings could not be imported, error(cannot import name MythDBBase)

WARNING: Error loading plugin <class 'mirobridgeconfig.MirobridgeconfigPlugin'>
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/MythbuntuControlCentre/plugin.py", line 75, in find_plugin_instances
    self._instances[plugin] = plugin()
  File "/usr/share/mythbuntu/plugins/python/mirobridgeconfig.py", line 88, in __init__
    self.mbfunctions = MirobridgeConfigFunctions(self.logger)
  File "/usr/share/mythbuntu/plugins/python/mirobridgeconfig.py", line 392, in __init__
    self.accessMythDB() # Test that this is a BE
  File "/usr/share/mythbuntu/plugins/python/mirobridgeconfig.py", line 468, in accessMythDB
    raise MirobridgeconfigPlugin_error(errormsg)
MirobridgeconfigPlugin_error: MythTV python bindings could not be imported, error(cannot import name MythDBBase)

Reading package lists... Done
Building dependency tree       
Reading state information... Done
james@james-desktop:~$ 

```

The control center loads, but if I change an option and click apply the change is never saved.

Any help is appreciated.

---

