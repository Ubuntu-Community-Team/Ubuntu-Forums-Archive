---
title: "Synergy and AutoStart"
date: 2010-03-30
forum: Networking &amp; Wireless
---

### Post by Unreasonable on 2010-03-30
Hi guys, I'm a brand new user to Ubuntu, and so far I'm liking it a lot. I currently have it installed on an older desktop, which is linked to a Windows XP machine through Synergy. I installed the Server version on the XP machine, and installed QuickSynergy on the Ubuntu (version 9.10 btw) machine. When I start up the XP machine, Synergy starts automatically and waits for the client to connect. When I start up the Ubuntu machine, the Synergy client does not autostart, and I have to go into the Terminal and type "Synergyc 192.168.2.4" in order to get it to start up and work. Once that is done, it works like a charm, no hiccups, lag or latency issues at all. The problem is, I eventually plan on using the Ubuntu machine as a network server, so it will be annoying to have a keyboard and mouse connected to it just so i can type "Synergyc 192.168.2.4" every time I need Synergy to connect.
 
Has anyone else had this problem before or know how I can get Synergy to autostart when I boot the machine? I did a Google and a Forum search and so far I haven't found anything helpful. Like I said, I'm brand new to Ubuntu, so if anyone does have instructions to fix this, please make them noob-friendly :)
 
 
EDIT: Solved: In order to get the machine to auto log me in, I went to System > Administration > Login Screen, and changed the radio button to log me in automatically. To get Synergy to also start up automatically upon login, I went into System > Preferences > Startup Applications and then added a custom startup program which I named "Synergy" with the Command of "synergyc 192.168.2.4" which tells it to load the client application of Synergy, with 192.168.2.4 as the Host (server) computer IP. Now when I turn on the PC, it will log me in automatically and start Synergy without the need of an extra keyboard/mouse to be attached for the sole purpose of logging in and entering the Synergy Client startup command.

---

### Post by Iowan on 2010-03-30
I haven't used Synergy (not yet, anyway). A couple of things to consider - Network Manager doesn't fire up interfaces until a user logs in. Dunno if this may cause a problem. Second, you can check to see if Synergy is set to run at startup. My Karmic machine got upgraded, but seems like System>Preferences>Startup Applications should show which programs launch at startup.

---

### Post by Unreasonable on 2010-03-30
Is there a way to disable the user password if I set one up during install?  I checked the User properties and I see a box that says "Don't ask for password on login" but it is grayed out.  Thanks for the reply btw.

---

