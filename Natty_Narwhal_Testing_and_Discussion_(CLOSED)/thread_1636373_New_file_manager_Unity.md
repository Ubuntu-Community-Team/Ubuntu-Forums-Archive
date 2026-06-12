---
title: "New file manager Unity?"
date: 2010-12-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by garvinrick4 on 2010-12-03
# pcmanfm has a Applications instead of file systems and is new file manager in Unity and
   nautilus still opens file browser.
# Has this been in Unity Natty or new upgrade today?
# it is nice addition has a / a /home and Applications.
# ALT/F2 and run file manager "pcmanfm"

---

### Post by cariboo on 2010-12-03
Nautilus is and will be the default file manager in Natty. There are changes in the way files are managed coming, using zeitgeist.

---

### Post by garvinrick4 on 2010-12-03
Here it is:

---

### Post by lucazade on 2010-12-03
We all know pcmanfm!
Do you know why Nautilus is default and cannot be changed (at the moment) with other GTK+ filemanager? :)

Look at features and compare with other file managers.
[http://en.wikipedia.org/wiki/Nautilus_(file_manager)](http://en.wikipedia.org/wiki/Nautilus_(file_manager))
Add also UbuntuOne support.

---

### Post by garvinrick4 on 2010-12-03
# That is good I just ran into it and thought maybe it was a new update:
# That is what I was asking, thank you.
# And no lucizade I do not know the answer to your question:
# Only thing I know is I can run nautilus and get my file browser nautilus
and I can run pcmanfm and get a browser with a left panel that was new for me.
# And right now it seems my 11.04 nappy unity is running well and the more I look
around it the more I will learn.

---

### Post by cariboo on 2010-12-03
Nautilus has always been a core part of the Ubuntu/Gnome desktop removing it will also remove most of the functionality of the desktop. You can use other file managers, without uninstalling nautilus.

---

### Post by garvinrick4 on 2010-12-04
How about  Alt/F1 and  Alt/F2 functions, I have one install of Natty that they work and one install of Natty that Alt/F1 and Alt/F2 do not function? Both in Keyboard shortcuts are installed. I always set Terminal to Alt/t and it works fine in both installs. I am using Unity of course.

---

### Post by cariboo on 2010-12-05
Actually I learned something new today, you don't have to use nautilus as the default file manager. Just open gconf-editor and navigate to /desktop/gnome/applications/component_viewer/exec and change the key to your choice. See the screenshot

The Applications and Places menus should be ready for the alpha2 release, so we should see then showing up in the coming weeks.

Alt-F1 and Alt-F2 are a part of the gnome-panel, so if you've still got it running the shortcuts will work, as soon as you kill the panels they stop working.

---

### Post by NightwishFan on 2010-12-05
> **cariboo907 said:**
> Alt-F1 and Alt-F2 are a part of the gnome-panel, so if you've still got it running the shortcuts will work, as soon as you kill the panels they stop working.

You can replace that largely with Gnome-do if desired as well. :popcorn:

---

### Post by Gourgi on 2010-12-05
> **NightwishFan said:**
> You can replace that largely with Gnome-do if desired as well. :popcorn:

or Synapse : 

[http://www.omgubuntu.co.uk/2010/11/synapse-gnome-do-launcher-app-review-ubuntu/](http://www.omgubuntu.co.uk/2010/11/synapse-gnome-do-launcher-app-review-ubuntu/)
:popcorn:

---

### Post by screaminj3sus on 2010-12-07
> **Gourgi said:**
> or Synapse : 

[http://www.omgubuntu.co.uk/2010/11/synapse-gnome-do-launcher-app-review-ubuntu/](http://www.omgubuntu.co.uk/2010/11/synapse-gnome-do-launcher-app-review-ubuntu/)
:popcorn:

Just tried synapse, its quite good, much faster than do and better looking BUT. Its not nearly as "intelligent" as do or kupfer. For example it doesn't remember which applications you open the most and put those at the top of the search results. Also I would really like to be able to make it opens with the "applications" tab by default rather than "all"

---

