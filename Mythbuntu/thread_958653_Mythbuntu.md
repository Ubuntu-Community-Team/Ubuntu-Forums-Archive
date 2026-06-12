---
title: "Mythbuntu"
date: 2008-10-25
forum: Mythbuntu
---

### Post by dardack on 2008-10-25
Ok I've searched and may have missed it.  If i loose power and power backup my mythtv box, mythbackend doesn't run, however if I log in and soft boot mythbackend runs.  So I want to have a mythtv menu item to reboot the system.  Is there a way?

---

### Post by ian dobson on 2008-10-25
Hi,

You'll need to edit the xml menu files (/usr/share/mythtv/mainmenu.xml or whatever your theme used) and add an extra button with something like:-

```
<!-- <button>
   <type>SHUTDOWN</type>
   <text>Reboot</text>
   <action>shutdown -r now</action>
</button> -->
```

It would be interesting to know why mythbackend doesn't automaticly start after an unclean shutdown. Maybe there is something in the backend log file. The only thing I can think of is MySQL needing time to check/repair the database.

Regards
Ian Dobson

---

