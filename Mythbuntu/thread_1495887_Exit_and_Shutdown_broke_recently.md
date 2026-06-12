---
title: "Exit and Shutdown broke recently"
date: 2010-05-28
forum: Mythbuntu
---

### Post by bunglebungle on 2010-05-28
I have a fresh 10.04 Mythbuntu frontend.  The Exit and Shutdown menu was working fine.  A couple of weeks ago I switched to the .23-fixes PPA.  At some point in the last week or so the Exit and Shutdown option stopped working - it just goes back to the Myth main menu.  

I have seen a few issues in Myth's Trac that indicate there were some changes to the exit logic (ie use DBus instead of a command if empty), but these all look to have been committed to .23 and thus should have been in the original 10.04 release.  None of the commits the last couple of weeks look related.  There's also some comments in this forum about clearing the "shutdown command", but I don't see that in the settings anywhere, nor was there anything in the settings table for that hostname.  

I tried adding a "HaltCommand" setting for this frontend to do a "sudo shutdown -P now", but it doesn't work.  (Shutdown is in sudoers and works from the command line without a password.)  I have run the frontend with "-v all" and MythFrontend gives no indication that it's trying to do anything at all when selecting the "Exit and Shutdown" link.  

Does anyone else have this problem?  Any other ideas to try?

---

### Post by Neon Dusk on 2010-05-28
I've just updated a frontend and see the same here. The frontend has 'HaltCommand' set to blank so that DBus will be used.

Think this issue must of appeared between 0.23 -fixes Chgset 24728 & Chgset 24879. The only change that I can see that might be relevant is [backports [24638] from trunk configure: check linking for QtDBus Fix &#8230; ](http://svn.mythtv.org/trac/changeset/24836/branches/release-0-23-fixes)

Edit: That changeset seems to be the issue - created ticket [here](http://svn.mythtv.org/trac/ticket/8505)

---

### Post by uncle hammy on 2010-05-31
Ditto with this problem.

---

### Post by bunglebungle on 2010-06-01
Thanks, ND.  I'm still not sure why setting a 'HaltCommand' doesn't work, but hopefully they'll fix this soon.

---

### Post by joshoekstra on 2010-06-04
A me too here as well...
Used to work without a hitch until the last update...

---

### Post by nickrout on 2010-06-05
> **bunglebungle said:**
> I have a fresh 10.04 Mythbuntu frontend.  The Exit and Shutdown menu was working fine.  A couple of weeks ago I switched to the .23-fixes PPA.  At some point in the last week or so the Exit and Shutdown option stopped working - it just goes back to the Myth main menu.  

I have seen a few issues in Myth's Trac that indicate there were some changes to the exit logic (ie use DBus instead of a command if empty), but these all look to have been committed to .23 and thus should have been in the original 10.04 release.  

10.04 did not ship 0.23. It shipped 0.23-RC2

---

### Post by kyfehr on 2010-06-07
Since doing an update last thursday I too no longer have this funcutionality working anymore. Used to work wonderfully.

---

### Post by Neon Dusk on 2010-06-12
It looks Mythbuntu includes a patch that removes the menu option for setting the halt command and updates the code so that only DBus will used ('HaltCommand' is ignored)

There's a patch that fixes the issue of DBus not getting detected [here](http://svn.mythtv.org/trac/ticket/8556) - hopefully 0.23-fixes will include this soon.

---

### Post by joshoekstra on 2010-06-15
One of the devs set it to .24, other milestone, so it's not gonna be in .23-fixes.
Maybe the mythbuntu-devs will include it.
Otherwise I'll have to resort to some irexec voodoo :(

---

### Post by tgm4883 on 2010-06-15
> **joshoekstra said:**
> One of the devs set it to .24, other milestone, so it's not gonna be in .23-fixes.
**Maybe the mythbuntu-devs will include it.**
Otherwise I'll have to resort to some irexec voodoo :(

I already did :), should be in the latest updates

---

### Post by tgm4883 on 2010-06-15
For anyone that cares, here is the bug report  [https://bugs.edge.launchpad.net/mythtv/+bug/574877](https://bugs.edge.launchpad.net/mythtv/+bug/574877)

The change would obviously be in a build after the date I posted I pushed the change

---

### Post by joshoekstra on 2010-06-16
> **tgm4883 said:**
> I already did :), should be in the latest updates
Bedankt, muchos gracias, thank you :)

---

### Post by tgm4883 on 2010-06-16
The build from last night should have fixed the issue. I'm away from home for a few days so can't test it myself. Please test it and update the bug report. Should be fixed in 0.23.0+fixes25111

---

### Post by David Grigor on 2010-06-16
I did notice it working again after the updates last night.

---

