---
title: "Myth Control Center (MCC) keeps changing my LIRC config"
date: 2011-10-18
forum: Mythbuntu
---

### Post by alien878 on 2011-10-18
I have a custom lirc config.  Every time I run the mcc, it changes the files in /etc/lirc and I have to fix them again by hand.  If I uncheck lirc in the mcc, it uninstalls lirc (not good).  If I check it and set the remote type to NONE, it changes the config files.  i don't see any "custom" remote type to get it to leave my configs alone.

Any idea how to stop the MCC from overwriting my lirc config files?

Cheers,

Allen

Edit: Mythtv 24.1, mythbuntu 10.10

---

### Post by thatguruguy on 2011-10-18
> **alien878 said:**
> I have a custom lirc config.  Every time I run the mcc, it changes the files in /etc/lirc and I have to fix them again by hand.  If I uncheck lirc in the mcc, it uninstalls lirc (not good).  If I check it and set the remote type to NONE, it changes the config files.  i don't see any "custom" remote type to get it to leave my configs alone.

Any idea how to stop the MCC from overwriting my lirc config files?

Cheers,

Allen

Edit: Mythtv 24.1, mythbuntu 10.10

I had this same problem.  I fixed it by choosing "USB or Serial Remote", and then deselecting both the IR receiver and IR transmitter in MCC, so that it wouldn't change settings for either.  I believe I may have had to manually set up my IR receiver after that, but I haven't had to deal with the issue since then.

Here's a screenshot of how my MCC is set up right now to illustrate my point:

---

### Post by alien878 on 2011-10-23
That's the settings I have.  I suspect it is because I have changed hardware.conf and the mcc sees that it doesn't match the settings, so it "fixes" it.

Is there anyway to remove the irconf from the mcc?

---

### Post by tgm4883 on 2011-10-23
Is it offering to change it every time you are in MCC (eg. After hitting apply on any screen does it say it is fixing LIRC even when you aren't touching the LIRC screen)? Or does it just change it without telling you?

Either way it sounds like a bug to me that should probably be filed on launchpad

---

### Post by alien878 on 2011-10-24
After fixing hardware.conf, the mcc will ask me to change lirc even if I did not change the lirc options.  Since it doesn't give me an option to cancel just one change, I can't make any other changes without it resetting hardware.conf.

From the screenshot, the mcc seems to have changed somewhat (I'm on 10.10 because of issues with the mantis drivers).  I'm going to try to upgrade again after the next LTS.  If the problem is still there, I'll open a bug.

In the mean time, I saw that some items in the mcc can be install/uninstalled with a package.  Is there a package for the lirc portion of the mcc?

---

