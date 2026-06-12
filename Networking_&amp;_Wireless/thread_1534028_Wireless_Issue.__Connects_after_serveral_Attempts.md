---
title: "Wireless Issue.  Connects after serveral Attempts"
date: 2010-07-18
forum: Networking &amp; Wireless
---

### Post by sammyboy405 on 2010-07-18
Hello,

I Have an Odd Problem, More than likely caused by a series of event I brought upon on myself.

So the #1 Thing I dont want to have to do is Re-Load.. Which im 100% Positive I wont have to do. 

Here is kinda what I did, 

Network-Manager wasnt rescanning for new AP's (Or I didnt know and still dont know how to make it rescan) So I Installed WICD.  And thats where the Trouble Began of it Connecting and Disconnecting to my AP Several Times. then Finally staying connected after 10+ Tries. 

So I uninstalled WICD, and the Issues Remains, How ever my "Kinda" Quick workaround is to open up the Network-manager Connection List, and delete my wireless Connection.  Reconnect and put my WPA2 Password in.. and it connects..

Its getting Annoying and Id like any help i can get to rectify this.

Also Too I think even Maybe it "MAY" have something to do with Gnome-Key Ring because when my Laptop boots up (its a little slow) it tries to connect to the internet long before Gnome Key-ring asks me to unlock it.

Maybe a separate issue.  but I thought Maybe it might be connected to my Wireless issues, as it is asking to be unlocked to access the WPA2 password.

Thanks In Advance

---

### Post by sammyboy405 on 2010-07-19
Anyone Have Any Suggestions..

---

### Post by sammyboy405 on 2010-07-23
So I figured my problem out.

Come to Find out my Gnome-Keyring was either corrupt or something.

here is what I did to fix it.
Disconnected my current wifi connection
edited my wifi connection and deleted it.

then opened a terminal

I went to  ~/.gnome/keyring

and rm *

reconnect, recreate a gnome-keyring password.. put my password in for Wifi and Walla .. Been working like a champ every since.

---

