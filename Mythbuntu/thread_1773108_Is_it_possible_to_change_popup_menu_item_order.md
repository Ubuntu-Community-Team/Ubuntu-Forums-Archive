---
title: "Is it possible to change popup menu item order"
date: 2011-06-01
forum: Mythbuntu
---

### Post by bcg30506 on 2011-06-01
Does anyone know if it is possible and if so how I can change the order of a few popup menu items in MythTV?

After upgrading from 0.23 to 0.24 some of my remote mappings no longer work because they assumed a certain order.  For example, when watching live TV, I'd like the program guide choice to be first when pressing the Menu key (M).  When watching a DVD, I'd like Navigate to be first for quickly getting to the menus.

I know I can change the menu order of the main UI menus, but cannot figure out how or if I even can change the popups.

---

### Post by ian dobson on 2011-06-01
Hi,

Aren't all the menu items in xml files? I've only hacked afew menus but never a popup.

Regards
Ian Dobson

---

### Post by bcg30506 on 2011-06-01
All the main UI menus are, which I've customized for years, but never a popup, and I cannot find them when grepping all the xml files.

---

### Post by azmyth on 2011-06-02
I could be wrong but I believe you'd have to compile as the menu is controlled in the tv_play.cpp file or mythfrontend_en_us.ts file from the sources from doing a grep.

---

### Post by nickrout on 2011-06-02
I think if you are basing keybindings on menu order you are doing it wrong.

---

### Post by crbnrod on 2011-06-02
You probably figured this out, but you can get rid of the stuff you don't want in the OSD editor which is in the frontend setup.

The comments for [this link]("http://kenyangeekboy.blogspot.com/2009/03/mythtv-osd-menu-editor.html") suggest what you're hoping to do will be a challenge.

---

### Post by bcg30506 on 2011-06-02
> **nickrout said:**
> I think if you are basing keybindings on menu order you are doing it wrong.

I guess I'm figuring that out, but I don't know how else to do it.

---

### Post by bcg30506 on 2011-06-02
> **crbnrod said:**
> You probably figured this out, but you can get rid of the stuff you don't want in the OSD editor which is in the frontend setup.

The comments for [this link]("http://kenyangeekboy.blogspot.com/2009/03/mythtv-osd-menu-editor.html") suggest what you're hoping to do will be a challenge.

I had not figured it out, but thanks for giving me credit for being smarter than I actually am. :)

Thanks for the link.  It seems the order is what it is.  However, I also never knew about the OSD editor to hide stuff.  I haven't seen it in the 0.24 setup menus, but will look again.

---

### Post by nickrout on 2011-06-02
> **bcg30506 said:**
> I guess I'm figuring that out, but I don't know how else to do it.

each "action" in mythtv has a "name" and each "name" can be bound to a key.

So if you want to bring up a programme guide from the remote, or a single keystroke, you assign the action to the keystroke.

Possibly the easiest way to do that is via mythweb

[http://backendmachine/mythweb/settings/mythtv/keys](http://backendmachine/mythweb/settings/mythtv/keys)

---

### Post by bcg30506 on 2011-06-03
> **nickrout said:**
> each "action" in mythtv has a "name" and each "name" can be bound to a key.

So if you want to bring up a programme guide from the remote, or a single keystroke, you assign the action to the keystroke.

Possibly the easiest way to do that is via mythweb

[http://backendmachine/mythweb/settings/mythtv/keys](http://backendmachine/mythweb/settings/mythtv/keys)

Ok, great!  I've got it working now for the program guide, but cannot find an action for edit recording.  I know "E" brings it up, but this system is controlled by remote control and I'm out of keys to map to it, so I need to remap this action to an "S" if possible.

---

### Post by nickrout on 2011-06-03
> **bcg30506 said:**
> Ok, great!  I've got it working now for the program guide, but cannot find an action for edit recording.  I know "E" brings it up, but this system is controlled by remote control and I'm out of keys to map to it, so I need to remap this action to an "S" if possible.

It is the "EDIT" action.

---

