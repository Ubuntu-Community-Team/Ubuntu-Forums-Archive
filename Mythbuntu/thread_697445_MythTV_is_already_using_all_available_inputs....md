---
title: "MythTV is already using all available inputs..."
date: 2008-02-15
forum: Mythbuntu
---

### Post by scruffy1 on 2008-02-15
that's the message when i hit the tv button in mythbuntu

"MythTV is already using all available inputs for the channel you selected.  If you want to watch an in progress recording select one from the playback menu."

but there's no recordings listed

and despite deleting the capture card(s) and attempting a reinstall it won't let me scan for channels, telling me to go to the console 

presumably for consolation seeing i have no idea how to fix it :-?

all advice welcome

---

### Post by volkswagner on 2008-02-15
What does information center say about your tuners?  If they say unavailable try restarting Mythbackend.  Check info center again to see if it changed.  You may want to list more info about your setup, ie: backend/frontend same machine?

---

### Post by Caps18 on 2008-02-15
I'm not sure if it is a Mythbuntu or a MythTV problem, but I would bet that the backend SQL database hadn't started up.  And sometimes I find that it doesn't start up right away when I restart my machine.  Either I have to give it a minute or two once the MythTV screen comes up, or I have to go into Mythbuntu's control panel, launch MythTV setup, exit MythTV setup, and then restart MythTV.  It is something that I will be looking for and trying to figure out.

---

### Post by volkswagner on 2008-02-17
Hijack:

I see Caps18 has a similar problem as me.  I wonder if we all have the same problem, although the OP has yet to respond.

Why do I have to restart my backend manually as Caps18 to get my slave and master to communicate?

Symptoms:
[LIST=1]
[*]After a restart of my slave machine, the tuner installed is listed as unavailable.
[*]After a restart of my slave machine recordings on this machine are not found by DB on slave nor Master machines.
[/LIST]

Work Around:

I like Caps18 have to manually restart the slave machines mythbackend.  Myself unlike Caps18 wait several minutes for the systems to play catch up, but no joy.  I need to manually restart mythbackend.

---

