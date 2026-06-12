---
title: "MythWeb stopped working when I upgraded from Mythbuntu 12.04 to 14.04"
date: 2014-11-08
forum: Mythbuntu
---

### Post by Dan_Beaudet on 2014-11-08
I've searched for solutions and nothing has worked so far.

Before the upgrade everything worked perfectly when connecting from outside my LAN. I've uninstalled and reinstalled MythWeb, which seems to have fixed the apache2 folder issue. 

Again, this used to work until the upgrade. I have not made any other system changes (i.e. my router is set to forward port 80 to my mythtv server as it has always been).

I can remote into my computer for other applications but access to MythWeb over the internet is broken. The message I get when I attempt to connect is generic: ERROR: Gateway Timeout

Something I noticed (which may not be related) is that when I try to activate password protection for MythWeb in MCC I add the username and password, but then get an error. It then reverts to a disabled state. I'm not sure if this has anything to do with my issue (i.e. bad configuration of apache?). The error message seems to be related to a python script.

Any ideas or suggestions would be greatly appreciated.

Thanks.

---

### Post by Dan_Beaudet on 2014-11-10
I discovered my ISP is blocking port 80. I modified the port mapping on my router and now it works.

---

