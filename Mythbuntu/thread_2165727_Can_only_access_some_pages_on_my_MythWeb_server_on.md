---
title: "Can only access some pages on my MythWeb server on Mythbuntu"
date: 2013-08-06
forum: Mythbuntu
---

### Post by scottmay on 2013-08-06
Hi there,

I can't seem to access all the pages on my mythweb site on my Mythbuntu 12.04.2 machine.  Specifically, I can access pages such as:

/mythweb
/mythweb/video (although it's not showing any recordings)
/mythweb/remote
/mythweb/stats
/mythweb/settings/*   (but not tv/channels)


I CAN'T access the following:

/mythweb/tv
/mythweb/status
/mythweb/settings/tv/channels



Some background - This machine has been working well for at least a year.  I ran apt-get upgrades the other night and it upgraded the kernel to 3.2.0.51 (not sure if that's related at all).  When the computer rebooted XBMC said it couldn't contact the backend on port 6543.  The mythtv-backend service was running.  mythtv-setup seemed to think that the backend was running, at least in one part of the setup anyway.  I've been starting and stopping services, and tweaking ownerships of relevant files with no luck.

I removed one of my tuners (a dual tuner USB device), ran setup and removed references to that - now there's just a HD HomeRun dual tuner. Upshot is now I can access the backend from XBMC, and it seems as though is was working in the mean time, as shows appear to have been recorded.

The problem I still have is remote management via the mythweb website - some pages work, some don't, as described above.  I installed a clean Mythbuntu install into a VMWare host and compared many things, and I can't find an error.

Anyone have any ideas?

Thanks - Scott.

---

### Post by novellahub on 2013-08-07
Most likely it is a memory setting in PHP that is making you not see part of mythweb.  See if this fixes your issues:

[http://ubuntuforums.org/showthread.php?t=1424649](http://ubuntuforums.org/showthread.php?t=1424649)
[http://ubuntuforums.org/showthread.php?t=2137793&p=12634863&viewfull=1#post12634863](http://ubuntuforums.org/showthread.php?t=2137793&p=12634863&viewfull=1#post12634863)

---

