---
title: "Show deleted in datatabase, but not on HD"
date: 2008-06-15
forum: Mythbuntu
---

### Post by NarsilAnduril on 2008-06-15
Hi,

Here is my small problem :

When I delete recorded shows through MythTV GUI (or through Mythweb), the entry does disappear from record's show list, but the files stay on the disk, filling it slowly ...

How can I fix this ?

Thanks

Diego

---

### Post by ian dobson on 2008-06-15
Hi,

Anything show in you mythbackend.log? It's usually in /var/log/mythtv

Regards
Ian Dobson

---

### Post by NarsilAnduril on 2008-06-16
Hi,

Nothing in the log, but I solved (or workarounded ?) the problem.

It looks like I have two different contextual menus in the "manage recordings" section. Whith a record selected, I can reach two contextual menus, one with the "select" button of my MS remote and another with the "right arrow" button.

With the first, "select", the options are (translation from french locale, don't know the exact text) "delete without re-recording", "delete allowing re-recording", ... etc. This "delete" doesn't delete the file, only the database entry.

The second, "right arrow", shows "delete" or "cancel", this one deletes both database entry and file.

---

