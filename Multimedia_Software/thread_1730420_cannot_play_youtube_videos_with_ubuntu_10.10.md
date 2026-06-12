---
title: "cannot play youtube videos with ubuntu 10.10"
date: 2011-04-16
forum: Multimedia Software
---

### Post by palzhanov on 2011-04-16
HI i am new to ubuntu using 10.10 version 
I use mozilla firefox browser 
When i first time opened youtube it said that
plugins are missing and showed available ones
i installed them NOw player has appeared but it says
"An error appeared try later"
I installed Minitube and totem too but they are not playing
Totem says "Cant locate url"
What is the problem Could someone explain????
THANKS

---

### Post by K_45 on 2011-04-16
Google flashaid, install the plugin, and execute the script in the addon.

---

### Post by varunendra on 2011-04-16
Open Synaptic (System > Administration > Synaptic Package Manager), type **flash** in the search box, select and install **flashplugin-nonfree** in the packages list. Restart firefox and see if the youtube videos can play.

If you do not see "flashplugin-nonfree" in the software list in synaptic, then you will have to enable "**multiverse**" repository (in synaptic, **Settings > Repositories**)

Also, make sure to uninstall all other flash plugins if there are any, else they may cause conflict errors.

Please also note that this plugin is a very resource hungry program, so you may wish to try first what K_45 suggested. I haven't tried flashaid myself, so can't comment about it.

---

