---
title: "KDE (networkmanager) offline with HSO connected"
date: 2009-01-06
forum: Networking &amp; Wireless
---

### Post by Bèr Kessels on 2009-01-06
I have an Option Icon 3g modem, connected with HSO/pharscape drivers and the HSOConnect GUI. This works fine. 

But KDE cannot use this network connection for some reason. Firefox, on the other hand can connect, though it always starts in offline mode. Ping and so on all work. It seems a KDE-only issue.

Firefox starts in offline mode, annoying, but fixable by unchecking the 
"offline" mode under File menu. 
Konqueror refuses to go online at all. Kmail. or kontact all appear to use the same (non existing connection) and cannot connect. Various kio-slaves, such as kio_http and kio_imap/kio_pop report connection errors. 

Important to note, is that konqueror also *cannot* connect to localhost (or yasmine, as the host is called) when there is no active wireless or eth connection. I suspect these issues to be related.

In other words: KDE cannot find or use networking *at all*, not even to localhost, if the knetworkmanager has no active connection. 

This may indicate that my networking is broken alltogether, or that some (leftover) configuration breaks the default handling of KDE/Kubuntu's networking. I am trying to find out if this is the case and how I can fix this by bringing back vanilla conf files.

What files should I investigate for broken or weird network settings?
I found little to none references of the same issue, so I am curious if this happens to more people.
Again, note that my Option Icon works perfectly fine, I am not looking for howto's on getting the pharscape drivers running!
Do you think that not KDE not being able to connect could be solved by running a local proxy? If so, what would be advisable?

---

### Post by MadeR on 2009-01-15
I have the same problem here.
Also the same problem arises if I connect using kppp and an analogue modem.

---

