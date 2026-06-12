---
title: "Some internet works, some doesn't???"
date: 2009-04-12
forum: Networking &amp; Wireless
---

### Post by cougar4u on 2009-04-12
Cheers linux community,

I am new here and have been using ubuntu 8.10 for about 6 months now. Most every problem I encounterd was solved via google, however, this one has me pulling my hair out.

Right now, when I open firefox, my home page will load perfectly, however none of my add-ons connect (foxmarks, forecastfox, etc...). Moreover, I can go to any website from the address bar..for example google.com, however, once there, I cannot submit a query in any way.

Same goes for applications, Pigdin does not connect properly nor does gFTP.

The last thing I did before this started was attempt to install a VPN client my university requires to connect.

Has anyone experienced this or have an idea of what's going ?!?

Any help would be much appriciated.

Regards,
Travis from Chicago


I'm using wireless internet on a Dell Inspiron 1520 with a dual-boot on xp & ubuntu 8.10. xp works fine, only ubuntu is giving me issues.

---

### Post by ajgreeny on 2009-04-12
Just temporarily rename the hidden folder ~/.mozilla in your home as ~/.mozillabak and then start FF again.  A new profile will be made and if that works OK without your old config then you at least know where the problem lays.  It may be one of your extensions or something like that but I would try just copying over the bookmarks from old .mozillabak folder to the new .mozilla, and then reinstall your extensions again from the web, just in case one of them is corrupt.  Bookmarks are now held in *places.sqlite* in the *alphanumeric*.default folder, not bookmarks.html.

---

