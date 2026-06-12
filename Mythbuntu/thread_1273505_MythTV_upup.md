---
title: "MythTV upup"
date: 2009-09-23
forum: Mythbuntu
---

### Post by davidstoll on 2009-09-23
Hi, I have several hardware and software units/programs that connect to uPnP.  However, I'm not seeing a MythTV upup server running on my network, but I do see some other upnp servers running.

How can I be sure that the mythtv upnp server is running and/or how do I enable it?

All I have right now is a single combo front/backend mythbuntu box.

Thank you!

---

### Post by ReddogOne on 2009-09-24
In the backend setup make sure you have the actual ip set for the machine rather than localhost or 127.0.0.1 (or similar).

---

### Post by davidstoll on 2009-09-24
> **ReddogOne said:**
> In the backend setup make sure you have the actual ip set for the machine rather than localhost or 127.0.0.1 (or similar).

That is it.  There are two IP locations on the General page.  By default, they were both set as 127.0.0.1.  After changing both, exiting the backend setup (no need to run mythfill database), the uPnP started broadcasting.

It looks like there are problems playing 1080 HD content, but the other stuff seems to play ok through uPnP.

Thank you for the help.

---

### Post by davidstoll on 2009-09-24
> **walter0515 said:**
> [http://google.com]("http://google.com/")

grow up and be original

I did search for this, but was not able to come up with a solution.  That's what this forumn is for.

---

