---
title: "Plugin mythnews failed to run..."
date: 2010-01-01
forum: Mythbuntu
---

### Post by changeJunkie on 2010-01-01
Howdy,
a new install of Mythbuntu, when going to Information Center -> News the following error message is displayed:

```

The plugin mythnews has failed to run for some reason...

```I've checked that the plugin is installed (apt-get install mythnews shows its installed and current).

I've checked the perms on the mythnews folder.

I've dropped the table as in the instructions for updating the xml file of news sites.

The only info in the (mythfrontend.log) logs I can find is this:
```

<snip>
2010-01-01 21:51:28.452 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//info_menu.xml
2010-01-01 21:51:29.500 Loading window theme from /usr/share/mythtv/themes/metallurgy/news-ui.xml
2010-01-01 21:51:29.506 Error: container 'mythnews' is missing child 'thumbnail'
2010-01-01 21:51:29.506 Cannot load screen 'news'

```can someone give me a clue please?

:confused:

Thanks

---

### Post by pils92 on 2011-06-21
Any help on this, Same problem here mythtv version .24 :confused:

---

### Post by iamlindoro on 2011-06-21
> **pils92 said:**
> Any help on this, Same problem here mythtv version .24 :confused:

It means you are using a theme which has not properly themed MythNews, and thus it cannot run.

---

### Post by pils92 on 2011-06-23
> **iamlindoro said:**
> It means you are using a theme which has not properly themed MythNews, and thus it cannot run.

Doesn't seem to be the problem tryed each available theme and restarted mythfrontend each time, no luck. "The plugin mythnews has failed to run for some reason" The utility menu responds with, "Failed to configure mythnews plugin."

---

