---
title: "Squeezebox Server Startup and IP Resolution Issues"
date: 2009-12-07
forum: Multimedia Software
---

### Post by kendoori on 2009-12-07
I have latest Squeezebox Server running on 8.10 desktop with a static IP address. For several releases now, there have been issues of the Squeezebox devices resolving IP address (e.g. Internet radio stations). Apparently this has to do with the server app getting started before the networking fully loads. I've tried multiple builds of the Squeezebox server and the only thing that seems to work, is to manually restart the Squeezebox server after the system comes back online after boot up. 

I think a simple fix would be to delay the start up of the /etc/init.d/squeezeboxserver script for something like 60 seconds, but am not sure how to do that.

Can anyone advise?

---

### Post by bluelamp999 on 2009-12-07
I had this issue on Squeezebox 7.3 running on Jaunty but it seems to have been resolved in version 7.4.1 running on Karmic.

I think 7.4.1 is supposed to fix this issue?

---

### Post by kendoori on 2009-12-07
I tried 7.4.2, but for some reason or other it never started properly. I since moved up to 7.5. Still same issues since any flavor of 7.x. Didn't have these issues previously under 6.x.

---

