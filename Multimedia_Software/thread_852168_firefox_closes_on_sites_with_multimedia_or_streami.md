---
title: "firefox closes on sites with multimedia or streaming or ?"
date: 2008-07-07
forum: Multimedia Software
---

### Post by aBitLater on 2008-07-07
I'm using hardy and Firefox 3.  When I go to [www.cnbc.com](www.cnbc.com) or [www.nbc.com](www.nbc.com), firefox abrubtly closes.

Does anyone have an idea why, or how I can investigate the problem?

I'm assuming it's a plugin problem, but don't know where to start figuring it out.

Many thanks,
Brian

EDIT: I installed the adobe flash player 10 beta 2 and this seems to help.  Still, I'm unsure if version 9 will cause conflicts - I removed it per instructions from adobe, but firefox about:plugins shows both plugins.  It shows version 10 as the first item in the list, then at the bottom it shows version 9 as enabled also

________________________________________________________________
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0.0 d525

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
------------------------------------------------------------------
... <snip> ...

__________________________________________________________________
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r124

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
-------------------------------------------------------------------

---

### Post by gandaran on 2008-07-07
EDIT: I installed the adobe flash player 10 beta 2 and this seems to help. Still, I'm unsure if version 9 will cause conflicts - I removed it per instructions from adobe, but firefox about:plugins shows both plugins. It shows version 10 as the first item in the list, then at the bottom it shows version 9 as enabled also

__________________________________________________ ______________

how  did you install flash 9? from the repository's? if correct then just open synaptic, find the flashplugin-nonfree package, check- mark for complete removal and click the apply button.
if you did the install the same way as flash 10, you'll have to find the plugin and delete it.

---

### Post by aBitLater on 2008-07-07
will 'complete' removal remove all the dependency files?  If so, what about other programs that may need those dependent files?

---

### Post by gandaran on 2008-07-07
> **aBitLater said:**
> will 'complete' removal remove all the dependency files?  If so, what about other programs that may need those dependent files?

flashplugin-nonfree doesn't have any dependencies, complete removal just removes the package completely, it's not a complete removal if you just choose removal, it'll uninstall the package in use but it will still be on the system.

---

