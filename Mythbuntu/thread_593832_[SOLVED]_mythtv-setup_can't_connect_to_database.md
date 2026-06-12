---
title: "[SOLVED] mythtv-setup can't connect to database"
date: 2007-10-27
forum: Mythbuntu
---

### Post by Luuse on 2007-10-27
Hi

I installed mythbuntu on my ubuntu box which also run a few other things and everything worked fine and I went through the mythtv-setup without any problems. But at this point i didn't have xmltv installed yet so i installed it and tried to run mythtv-setup again, which failed.

The terminal that pops up when you push the button to start the setup (I'm not running the English version so i can't tell you the exact name) gets filled with attempts to connect to the database but all of them fails. I've run "dpkg-reconfigure" and set the correct details on both mythtv-common and mythtv-database.

I can connect to the database through the command line using the password i got during the initial install so there's nothing wrong with the account.

I've also tried to remove all packages beginning with myth and the config files through synaptic but the mythbuntu-control center still have the details filled in when i install it again.

If i uninstall the backend through the control center i can press the "test mysql connection" button and it succeeds.

Any ideas?

---

### Post by Luuse on 2007-10-27
Just tried to reconfigure it to use my own database details and that didn't work either. Is there any libraries that might be damaged that can be reinstalled?

---

### Post by Luuse on 2007-10-28
My bad.

For future reference see [this]("https://help.ubuntu.com/community/MythTV/Install/Troubleshooting#head-75ded5e7682340f0a88f9ed6ec69a68b6a8b4162").

---

