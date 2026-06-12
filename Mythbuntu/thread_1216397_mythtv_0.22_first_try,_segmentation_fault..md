---
title: "mythtv 0.22 first try, segmentation fault."
date: 2009-07-18
forum: Mythbuntu
---

### Post by Nirro on 2009-07-18
Hi guys,

I've decided to be bold and try the 0.22 trunk,
well, now when I start mythfrontend, I see the empty window popping, and than it closes, and I get segmentation fault.

These are the last messages I get in verbose mode (mythfrontend -v all)

```

2009-07-18 15:13:43.248 MSqlQuery::exec() "SELECT keylist, description FROM keybindings WHERE context = 'Teletext Menu' AND action = 'MENUYELLOW' AND hostname = 'htpc' ;"
2009-07-18 15:13:43.248 MSqlQuery::exec() "SELECT keylist, description FROM keybindings WHERE context = 'Teletext Menu' AND action = 'MENUBLUE' AND hostname = 'htpc' ;"
2009-07-18 15:13:43.249 MSqlQuery::exec() "SELECT keylist, description FROM keybindings WHERE context = 'Teletext Menu' AND action = 'MENUWHITE' AND hostname = 'htpc' ;"
2009-07-18 15:13:43.249 MSqlQuery::exec() "SELECT keylist, description FROM keybindings WHERE context = 'Teletext Menu' AND action = 'TOGGLEBACKGROUND' AND hostname = 'htpc' ;"
2009-07-18 15:13:43.249 MSqlQuery::exec() "SELECT keylist, description FROM keybindings WHERE context = 'Teletext Menu' AND action = 'REVEAL' AND hostname = 'htpc' ;"
2009-07-18 15:13:43.249 Registering Internal as a media playback plugin.
2009-07-18 15:13:43.250 MSqlQuery::exec() "DELETE FROM inuseprograms WHERE hostname = 'htpc' and recusage = 'player' ;"
Segmentation fault

```

Does anyone have an idea what should I do ?

Thanks.

---

### Post by Nirro on 2009-07-18
I followed the directions in the thread and it fixed the problem (basically reset the database).
[http://ubuntuforums.org/showpost.php?p=2704038&postcount=4](http://ubuntuforums.org/showpost.php?p=2704038&postcount=4)

Thanks.

---

