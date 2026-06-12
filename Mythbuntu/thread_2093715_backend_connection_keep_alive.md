---
title: "backend connection keep alive"
date: 2012-12-11
forum: Mythbuntu
---

### Post by jonnybignote on 2012-12-11
12.04 64-bit

Hey all - not a very helpful topic title, so here's what I really want to do.

Wondering what is the best way for handling keeping awake of the backend server, when my new frontend is using software other than mythtv such as XBMC.  My backend is configured to sleep after 3 mins of not being connected to a frontend client or after performing recordings and other jobs etc.

Backend used to be a combined FE/BE and in that case, I had my shutdown check script check for open xbmc or terminal at which point it would reset the counter and the thing would stay on.  

Basically, what I think I really need is for the backend to turn on whenever the frontend is.  Not ideal in some cases (I could be watching streaming content on the frontend for example and would not need the backend connection) but would be the only way in order to have available my music and video files which remain only on the backend.

I'm sure I can fairly easily cobble something together through a script, but I just wanted to check if anyone had any elegant solutions, or something more simple that I may not be aware of.

Thanks again

---

### Post by nickrout on 2012-12-11
When XBMC is running on my machine, the frontend is still running too in the background. (I have a mythtv menu item to start xbmc). I don't know if the frontend sitting idle like that in the background is enough to keep the backend from shutting down, but it's worth a try.

---

### Post by jonnybignote on 2013-04-29
> **nickrout said:**
> When XBMC is running on my machine, the frontend is still running too in the background. (I have a mythtv menu item to start xbmc). I don't know if the frontend sitting idle like that in the background is enough to keep the backend from shutting down, but it's worth a try.

Sorry I didn't see your reply so long ago - thanks for that.  It would work to keep the backend open, but it really screws with my remote (some of the keys pressed for XBMC end up triggering things on the MythTV Frontend even though it's there in the background.

I have had luck scripting a remote ssh login to the backend, (the nature of my mythshutdown checks, forces the backend to stay on if anyone is logged in via ssh)

I have had trouble though, in that the frontend periodically seems to forget the login....)

---

