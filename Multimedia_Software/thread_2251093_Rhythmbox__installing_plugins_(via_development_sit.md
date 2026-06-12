---
title: "Rhythmbox | installing plugins (via development site)"
date: 2014-11-01
forum: Multimedia Software
---

### Post by fohrums on 2014-11-01
What is the best way to get plugins, especially those that are frequently updated?[INDENT]
According to Rhythmbox's *development* site (i feel like it's oudated) :
[/INDENT]
[INDENT][https://wiki.gnome.org/Apps/Rhythmbox/Plugins/ThirdParty#Stop_After_Current_Track](https://wiki.gnome.org/Apps/Rhythmbox/Plugins/ThirdParty#Stop_After_Current_Track)
[/INDENT]




**Aren't these the installation instructions?**
[LIST=1]
[*=1]clone via github 
[*=1]cd into directory 
[*=1]sh install.sh 
[/LIST]


After doing so I do have the plugin appear in '*Rhythmbox > Tools > Plugins...*' but I end up getting the error symbol, like so:
(*it doesn't work, basically*)

[[IMG]http://s16.postimg.org/fz57n8c29/rhythmbox_plugin.jpg[/IMG]]("http://postimg.org/image/fz57n8c29/")

---

### Post by CantankRus on 2014-11-02
See the first answer here....
[**_[COLOR="#B22222"]How do I install third-party rhythmbox plugins?[/COLOR]_**]("http://askubuntu.com/questions/147942/how-do-i-install-third-party-rhythmbox-plugins")

---

### Post by fohrums on 2014-11-06
> **CantankRus said:**
> See the first answer here....
[**_[COLOR=#B22222]How do I install third-party rhythmbox plugins?[/COLOR]_**]("http://askubuntu.com/questions/147942/how-do-i-install-third-party-rhythmbox-plugins")

In other words I am only limited to ones that are part of that PPA? Because the developer site has more.

---

### Post by mc4man on 2014-11-06
What version of Rb do you have
(current 3.0+ uses python3, your example plugin is for python2 so can't be loaded nor work in Rb-3.0+

---

