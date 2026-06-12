---
title: "XBMC (Dharma official) grooveshark addon"
date: 2010-12-29
forum: Multimedia Software
---

### Post by jimbo99 on 2010-12-29
Been trying to get Grooveshark to work with XBMC 10 (the official Dharma release).

[LIST]
[*]Under my windows install of XBMC I can download any/all addons and they work.

[*]Under any of my Ubuntu (10.10) no addons will download.  They stop at Downloading 0%.

[*]XBMC has an option for installing an addon via a .zip file (system > system > addons).  I have the Grooveshark addon in .zip format.
[/LIST]

I've added that addon via that option.  When I go to access it, there's a drawn out period of time while it gets some popular song info and sends me some album art.  When I choose to play, the Grooveshark addon for XBMC indicates that Grooveshark is at 100% and then says to wait.  I wait.  It then tells me that one or more items failed to play.

[LIST]
[*]On the same network on a Windows box Grooveshark works fine.

[*]On the same network on a Windows box all addons download fine.

[*]I've also disabled IPV6.

[*]Under 64bit Ubuntu 10.10 with the latest XBMC installed from the PPA no addons work.
[/LIST]

I think the key here is that nothing downloads.

[LIST]
[*]My XBMC user data is in the appropriate folders under ~/.xbmc.  
[*]During the install of Grooveshark (via the .zip file) no errors are presented.  
[*]After a reboot, no errors are presented when I launch XBMC.
[/LIST]
Has anyone else encounted this problem?  XBMC is pretty popular.  The only thorn that I can see to XBMC is that Dharma was just released and it has some pretty serious changes when it comes to dealing with addons.

Help would be appreciated.

---

### Post by jimbo99 on 2010-12-30
No one has any thoughts?  No one using XBMC but me?

---

### Post by stephanecharette on 2011-01-10
Installed XBMC on two Ubuntu 10.10-64bit computers tonight.  On one of them, addons work fine.  On the other, the download stays stuck at 0% complete like you describe above.  I don't know what difference between these computers makes it work for one and not the other.

On the one that doesn't work, the user account is "desktop user", not an administrator.  I changed the account after installation, but that didn't fix it.  Maybe if I had created it as an admin account prior to installing xbmc?

If you run into the solution, please post to this forum thread, as searching in Google turns many many people with this problem, but no solution.

---

### Post by diamoph on 2011-02-13
I just ran "xbmc" in terminal and used it like normal. Any errors with packages or missing files will show up in terminal.

Then just type the names of mentioned packages in synaptic package manager, usually they will have errors on them and need "upgrading" or just need to be installed in the first place.

After doing this a few times until only trivial errors were showing (such as not finding a thumbnail pic), the addons suddenly came back to life! Hope this helps, if not a little late lol.

---

