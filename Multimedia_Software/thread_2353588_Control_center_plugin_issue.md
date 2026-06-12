---
title: "Control center plugin issue"
date: 2017-02-23
forum: Multimedia Software
---

### Post by studio105 on 2017-02-23
hi all.
just upgraded from 12.X to 14.04/ .27 several things got broken and it seems  there is NO recent 
update or solved posts for these issues.
i have tried several of the solutions offered on many other threads in many other forums.
as im new to posting, i apologize if this gets hairy.
im pretty novice with command line items but ill do what i can to research anything i dont understand.



  control center gets a Plug in error each time it opens and closes.
this error is well documented but none of the stated fixes actually fix the issue.
posts go back to .25 on this with no recent posts actually solving the issue.
the error message is as follows.
> "Exception in applyStateToGUI of plugin Plugins. Disabling Plugin."
some of this must be related to the repository as thats just broken 
i have been exploring the error line by line.
ill try to post the results below.
what file(s) do you need to see to diagnose this issue, 

output of starting the control centre from a terminal window

```
carl@mythtv:~$ sudo mythbuntu-control-centre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Traceback (most recent call last):
  File "/usr/bin/mythbuntu-control-centre", line 383, in refreshState
    plugin.applyStateToGUI()
  File "/usr/share/mythbuntu/plugins/python/plugins.py", line 92, in applyStateToGUI
    self.mythweb_password_combobox.append_text("Reconfigure")
AttributeError: 'ComboBox' object has no attribute 'append_text'
Traceback (most recent call last):
  File "/usr/lib/python3.4/configparser.py", line 1116, in _unify_values
    sectiondict = self._sections[section]
KeyError: 'cfg'

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/share/mythbuntu/plugins/python/mythbuntu_repos.py", line 132, in captureState
    self.changes['MythTVUpdatesRepo'] = self.config.get("cfg", "MythTVRepo")
  File "/usr/lib/python3.4/configparser.py", line 754, in get
    d = self._unify_values(section, vars)
  File "/usr/lib/python3.4/configparser.py", line 1119, in _unify_values
    raise NoSectionError(section)
configparser.NoSectionError: No section: 'cfg'

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/bin/mythbuntu-control-centre", line 377, in refreshState
    plugin.captureState()
  File "/usr/share/mythbuntu/plugins/python/mythbuntu_repos.py", line 134, in captureState
    self.changes['MythTVUpdatesRepo'] = self.versions[0]
IndexError: list index out of range
HTTP Error: 404 [http://people.ubuntu.com/~tmg4883/repos.db](http://people.ubuntu.com/~tmg4883/repos.db)
Traceback (most recent call last):
  File "/usr/lib/python3.4/configparser.py", line 1116, in _unify_values
    sectiondict = self._sections[section]
KeyError: 'cfg'

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/share/mythbuntu/plugins/python/mythbuntu_repos.py", line 132, in captureState
    self.changes['MythTVUpdatesRepo'] = self.config.get("cfg", "MythTVRepo")
  File "/usr/lib/python3.4/configparser.py", line 754, in get
    d = self._unify_values(section, vars)
  File "/usr/lib/python3.4/configparser.py", line 1119, in _unify_values
    raise NoSectionError(section)
configparser.NoSectionError: No section: 'cfg'

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/share/mythbuntu/plugins/python/mythbuntu_repos.py", line 215, in refresh_button_clicked
    self.captureState()
  File "/usr/share/mythbuntu/plugins/python/mythbuntu_repos.py", line 134, in captureState
    self.changes['MythTVUpdatesRepo'] = self.versions[0]
IndexError: list index out of range
carl@mythtv:~$
```

---

