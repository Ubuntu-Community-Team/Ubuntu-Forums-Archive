---
title: "mythtv databases became read only"
date: 2010-05-07
forum: Mythbuntu
---

### Post by pbienst on 2010-05-07
Hi,

For some reason, mythtv cannot make changes anymore to the mythtv database. This happened a few days after upgrading to 10.04.

e.g.:

2010-05-07 21:09:20.757 DB Error (Insert Keybinding):
Query was:
INSERT INTO keybindings (context, action, description, keylist, hostname) VALUES ( ?, ?, ?, ?, ? );
Bindings were:
:ACTION=CUSTOMEDIT, :CONTEXT=TV Frontend, :DESCRIPTION=Edit Custom Record Rule,
:HOSTNAME=urnammu, :KEYLIST=
Driver error was [2/1036]:
QMYSQL3: Unable to execute statement
Database error was:
Table 'keybindings' is read only

This is true for all my keybindings.

Any ideas?

---

