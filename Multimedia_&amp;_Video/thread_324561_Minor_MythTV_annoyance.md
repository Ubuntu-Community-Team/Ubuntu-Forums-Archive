---
title: "Minor MythTV annoyance"
date: 2006-12-23
forum: Multimedia &amp; Video
---

### Post by admiralawesome on 2006-12-23
I've got one MythTV backend and four frontends set up.  I've gotten everything working but one tiny thing.  In MythTV 0.20, is there some way I can get the "Yes, Exit and Shutdown" option on the quit menu to work?  It exits, but doesn't shutdown.  The mythfrontend output in the terminal windows says "halt: Need to be root".  All of my frontends run mythfrontend under the user "mythfe".  I guess Exit and Shutdown would probably work if I were running as root, but I'd like to avoid that.  I've already got the system to boot, login, and launch mythfrontend (by placing it in the gnome startup programs list under System>Preferences>Sessions) without any interaction with the user, so prompting for a password to run mythfrontend with gksudo would not be desirable.  Is there another way to allow the user mythfe to halt the system?

---

### Post by AusIV4 on 2006-12-24
Change the command it executes to

sudo halt

Then in a command line

sudo visudo

And add:

%mythfe ALL = NOPASSWD: /usr/bin/halt

I've not tested this, but I believe it should allow all users from the group mythfe to execute "/usr/bin/halt" without a password.

---

