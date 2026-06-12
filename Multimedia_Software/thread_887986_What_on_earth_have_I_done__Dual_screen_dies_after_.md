---
title: "What on earth have I done?  Dual screen dies after logon"
date: 2008-08-12
forum: Multimedia Software
---

### Post by myxiplx on 2008-08-12
Hey folks,

I'm pretty new to Ubuntu, but eventually managed to get the latest ATI drivers installed and working (kinda).

The only problem I have now is that I just can't get the dual screen mode to work after I log in.  After the latest re-installation of the driver, I got things pretty much working by resetting the settings to the basics with:

# aticonfig --initial -f
# aticonfig --dtop=horizontal --overlay-on=1

Now what's stumping me is that this appears to work fine when I first boot Ubuntu.  The login screen works great in dual screen mode, and both monitors are running at 1280x1024.  The problem is that after I login it reverts to cloned displays and I can't for the life of me work out why.

I assume there's a login script or command firing off somewhere that's causing this, probably something left over from my earlier attempts to get the drivers working, but despite a good hunt on google, so far I've not been able to find what it could be.

Can anybody help?

thanks,

Ross

---

### Post by markbuntu on 2008-08-12
You need to use the Catalyst Control Center to set up the big desktop. It is ususally hiding in Applications/Other. It is a per user configuration option and the default configuration for users is for cloned screens.

If you are using the restricted driver from the repository, you may not have it installed. It is called

amdcccle

and you can open it with the amdcccle command from a terminal.

---

### Post by myxiplx on 2008-08-13
Yes, I've tried that but it doesn't help.  Running the control center allows me to set up the big desktop for the current session, but it reverts back to a cloned display after I reboot and log back on.

---

### Post by myxiplx on 2008-08-13
Can anybody else help me?  Where would I have to look for video card settings that only takes effect after logon?

---

### Post by myxiplx on 2008-08-13
Ok, it's confirmed.  It's definately something on my account causing this.  I've created a new test user and it doesn't happen there.

I'm currently trying to browse through all hidden files & folders to see if I can spot what's different between the two user accounts.  Does nobody have any clue where I would be best looking?

---

### Post by markbuntu on 2008-08-13
Really, I usually have to reset to get my big desktop. Have you tried saving your session in System/Preferences/Session after you have the bigdesktop up and running?
Also, make sure your default login is set to last session or whatever, not gmone or xscript.

---

