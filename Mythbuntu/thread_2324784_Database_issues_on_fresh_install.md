---
title: "Database issues on fresh install"
date: 2016-05-16
forum: Mythbuntu
---

### Post by pbienst on 2016-05-16
On a fresh install of mythbuntu 16.04, I get database issues when running mythtv-setup:

[COLOR=#383838][FONT=gotham]>ERROR 130 (HY000) at line 1: Incorrect file format 'settings'

[/FONT][/COLOR][COLOR=#383838][FONT=gotham]I tried going into the mysql console and did

>repair table settings use_frm;

In fact, I had to do this for all tables in the database.

The initial setup now gets a bit further, but complains about not being able to upgrade the database scheme (the messages flash by a bit too quickly to read).

Can somebody help to get the database in clean working state? '[/FONT][/COLOR][COLOR=#383838][FONT=gotham]sudo dpkg-reconfigure mythtv-database' did not help either...

Ok, and I also get errors about failing to connect to the upstart socket...[/FONT][/COLOR]

---

