---
title: "Use Android remote option not working in Control Centre"
date: 2014-05-15
forum: Mythbuntu
---

### Post by dom7 on 2014-05-15
Hi,

When I run control centre and try and select teh Android Remote radio button I get the following dialog box :

Exception in compareState of plugin MySQL

Disabling plugin.

And when I run the control centre from the OS command I can see the following :

Traceback (most recent call last):
  File "/usr/bin/mythbuntu-control-centre", line 360, in compareState
    plugin.compareState()
  File "/usr/share/mythbuntu/plugins/python/mysql_configuration.py", line 124, in compareState
    if not self.mysql_service and self.enablemysql.get_active_text() == "Enable":
AttributeError: 'ComboBox' object has no attribute 'get_active_text'

Any ideas what might be wrong ?  This is a 2 day old installation so hopefully I've not broken it (too much).

cheers

---

### Post by tgm4883 on 2014-05-15
> **dom7 said:**
> Hi,

When I run control centre and try and select teh Android Remote radio button I get the following dialog box :

Exception in compareState of plugin MySQL

Disabling plugin.

And when I run the control centre from the OS command I can see the following :

Traceback (most recent call last):
  File "/usr/bin/mythbuntu-control-centre", line 360, in compareState
    plugin.compareState()
  File "/usr/share/mythbuntu/plugins/python/mysql_configuration.py", line 124, in compareState
    if not self.mysql_service and self.enablemysql.get_active_text() == "Enable":
AttributeError: 'ComboBox' object has no attribute 'get_active_text'

Any ideas what might be wrong ?  This is a 2 day old installation so hopefully I've not broken it (too much).

cheers

It's a known bug. You can help get it fixed by testing the proposed fix here [https://bugs.launchpad.net/mythbuntu/+bug/1316905](https://bugs.launchpad.net/mythbuntu/+bug/1316905)

---

### Post by dom7 on 2014-05-15
Great. I will. Thanks for your help

---

