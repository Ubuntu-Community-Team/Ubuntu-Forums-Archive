---
title: "MCC hangs with Jamu-related error on frontend (new install)"
date: 2010-09-24
forum: Mythbuntu
---

### Post by duiker.ts on 2010-09-24
I have done a clean install of Mythbuntu 10.04 on an Acer Revo, and have selected frontend-only during install. 

When I launch MCC I get errors related to Jamu and a backend:

tony@myth-front:~$ mythbuntu-control-centre
WARNING: With any -M option Jamu and its MCC plugin must be run on a MythTV backend,
Error(Could not find setting 'BackendServerIP' on host 'myth-front')
CRITICAL: Jamu configuration plugin must be run on a MythTV backend. Local host (myth-front) is not a MythTV backend.

WARNING: Error loading plugin <class 'jamuconfig.JamuconfigPlugin'>
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/MythbuntuControlCentre/plugin.py", line 75, in find_plugin_instances
    self._instances[plugin] = plugin()
  File "/usr/share/mythbuntu/plugins/python/jamuconfig.py", line 100, in __init__
    raise JamuconfigPlugin_error(errormsg)
JamuconfigPlugin_error: Jamu configuration plugin must be run on a MythTV backend. Local host (myth-front) is not a MythTV backend.

When I try to change the SQL pin for remote access to the backend the MCC GUI hangs with these errors in the terminal:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Traceback (most recent call last):
  File "/usr/bin/mythbuntu-control-centre", line 264, in summaryApply
    plugin.user_scripted_changes(self.reconfigure_user[item])
  File "/usr/share/mythbuntu/plugins/python/mysql_configuration.py", line 161, in user_scripted_changes
    if item == "securitypin":
NameError: global name 'item' is not defined

Any ideas?

---

### Post by superm1 on 2010-09-24
> **duiker.ts said:**
> I have done a clean install of Mythbuntu 10.04 on an Acer Revo, and have selected frontend-only during install. 

When I launch MCC I get errors related to Jamu and a backend:

tony@myth-front:~$ mythbuntu-control-centre
WARNING: With any -M option Jamu and its MCC plugin must be run on a MythTV backend,
Error(Could not find setting 'BackendServerIP' on host 'myth-front')
CRITICAL: Jamu configuration plugin must be run on a MythTV backend. Local host (myth-front) is not a MythTV backend.

WARNING: Error loading plugin <class 'jamuconfig.JamuconfigPlugin'>
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/MythbuntuControlCentre/plugin.py", line 75, in find_plugin_instances
    self._instances[plugin] = plugin()
  File "/usr/share/mythbuntu/plugins/python/jamuconfig.py", line 100, in __init__
    raise JamuconfigPlugin_error(errormsg)
JamuconfigPlugin_error: Jamu configuration plugin must be run on a MythTV backend. Local host (myth-front) is not a MythTV backend.

When I try to change the SQL pin for remote access to the backend the MCC GUI hangs with these errors in the terminal:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Traceback (most recent call last):
  File "/usr/bin/mythbuntu-control-centre", line 264, in summaryApply
    plugin.user_scripted_changes(self.reconfigure_user[item])
  File "/usr/share/mythbuntu/plugins/python/mysql_configuration.py", line 161, in user_scripted_changes
    if item == "securitypin":
NameError: global name 'item' is not defined

Any ideas?
Can you please file a bug on launchpad to track this with?

```
apport-bug mythbuntu-control-centre

```
So we can look at all the details.

---

### Post by duiker.ts on 2010-09-25
> **superm1 said:**
> Can you please file a bug on launchpad to track this with?

```
apport-bug mythbuntu-control-centre

```So we can look at all the details.

Done, bug #647367

Thx

---

