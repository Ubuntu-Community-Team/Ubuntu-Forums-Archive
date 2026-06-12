---
title: "Remove TV related options from menu?"
date: 2012-03-13
forum: Mythbuntu
---

### Post by the_dingman on 2012-03-13
I'm setting up a MythTV box for the sole purpose of games, music and pictures, and will not be using any of the TV features.  Is there a way to remove 'Watch TV' and 'My Recordings' from the menu?

---

### Post by klc5555 on 2012-03-13
Of course, Mythtv is nowhere close to the best app for what you want to do. XBMC is more likely correct.

Mythtv is first and foremost a TV and DVR app, that also allows you to do some other things. The mythbackend is set up above all to schedule and manipulate TV recordings. And while you could eliminate the interface buttons for Live TV, My Recordings, and Manage Recordings from the main menu by editing the /usr/share/mythtv/themes/defaultmenu/mainmenu.xml file (or the equivalent), you still wouldn't be able to avoid running mythbackend and its related bells and whistles that you wouldn't want to use.

---

### Post by wyliecoyoteuk on 2012-03-13
I am not sure that the latest version of Myth will even start without a TV card.

XBMC might be a better bet.

---

### Post by nickrout on 2012-03-14
> **wyliecoyoteuk said:**
> I am not sure that the latest version of Myth will even start without a TV card.

XBMC might be a better bet.

The backend will not start without a card defined, but you can use one of the DUMMY settings.

To answer the original question, you need to copy the relevant menu files to ~/.mythtv/ and then edit them, they will override the defaults.

I note the xbmc answers. Does xbmc have the equivalent of mythgame?

---

### Post by klc5555 on 2012-03-14
There are game launcher interfaces among the available XBMC addons.

---

