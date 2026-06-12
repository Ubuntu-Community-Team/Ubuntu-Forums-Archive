---
title: "MythWelcome starts up instead of frontend"
date: 2010-12-31
forum: Mythbuntu
---

### Post by Bentley8 on 2010-12-31
I have a bit of an odd thing happening here.  Really got me scratching my head.

I'm using the Ubuntu 10.10 desktop and when I try and start the frontend by going under Applications--> Sound & Video--> MythTV Frontend, the frontend does not start.  MythWelcome starts up instead.  

Granted, I can start the frontend from MythWelcome, but I don't want to use MythWelcome right now.  I'm troubleshooting some suspend-to-ram issues and want to eliminate it as a variable.

So, how did I manage to confuse the frontend with MythWelcome on my system, and how can I fix it?

---

### Post by Neon Dusk on 2010-12-31
You should be able to comment out the 'MythWelcome' line in /etc/mythtv/session-settings

(In mythbuntu mythfrontend is a wrapper script that starts mythfrontend.real or mythwelcome depending on the settings in /etc/mythtv/session-settings)

---

### Post by Bentley8 on 2010-12-31
Hey, that did it!  

Thanks!

---

