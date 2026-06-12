---
title: "Add plugins to Rhythmbox???"
date: 2009-07-21
forum: Multimedia Software
---

### Post by Ernesto RD on 2009-07-21
I want to add some plugins to Rhythmbox, but i have no clue of how.

The plugin i want to add is the 10 band Equalizer i found here
[http://cs.helsinki.fi/u/ttokalli/rb-plugins/](http://cs.helsinki.fi/u/ttokalli/rb-plugins/)

The instructions there say...
**Installation**

 
[LIST=1]
[*]Download [equalizer.tar.gz]("http://cs.helsinki.fi/u/ttokalli/rb-plugins/equalizer.tar.gz")
[*]Create local plugin directory: mkdir ~/.gnome2/rhythmbox/plugins/
[*]Decompress archive: tar -xzvf equalizer.tar.gz -C ~/.gnome2/rhythmbox/plugins/
[*]Restart Rhythmbox
[/LIST]
but there is no ~/.gnome2/rhythmbox directory!

Can someone tell me where rhythmbox stores its plugins? where should i extract this archive to?
im using ubuntu 9.04
Thanks!

---

### Post by ShadowTek on 2009-07-21
Maybe in /.cache/rhythmbox/ ?

At least that's where *some* things are stored.

---

### Post by Ernesto RD on 2009-07-21
Found it!
its
/usr/lib/rhythmbox/plugins

You need to run nautilus with sudo from a terminal to be able to write to that folder tho.

---

### Post by youarefunny on 2010-03-07
The point of the "mkdir" is to create the directory.

What you have found is the system wide and default plug-in directory.  It will work but different purpose.

---

