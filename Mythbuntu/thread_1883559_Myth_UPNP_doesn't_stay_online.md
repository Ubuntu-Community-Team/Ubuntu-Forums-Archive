---
title: "Myth UPNP doesn't stay online"
date: 2011-11-19
forum: Mythbuntu
---

### Post by mnclayshooter on 2011-11-19
My current setup:

Mythbuntu 10.04 with Myth 0.24 connected to router via ethernet
WDTV Live via ethernet 
Windows 7 laptop via wireless 

When I initially start the the myth box, everything usually works perfectly.  I'm able to connect and watch recordings using my WDTV Live/Laptop and the frontend on the mythbox.  

After a while, I am not able to access the media server any longer.  I can still access network shares etc (samba) on the myth box, just not the DLNA/Upnp stuff.  

Thoughts?  Any good starting points?  I'm pretty novice at using linux, so patience/help with commands etc is appreciated.

---

### Post by ian dobson on 2011-11-19
Hi,

Have a look in the backend log file (/var/log/mythtv/mythbackend.log) just after seeing that the connection is down.

Regards
Ian Dobson

---

