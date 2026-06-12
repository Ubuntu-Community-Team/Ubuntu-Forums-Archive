---
title: "[SOLVED] Mythetomer - Nokia n800 Remote for Mythtv"
date: 2008-07-31
forum: Mythbuntu
---

### Post by dmfrey on 2008-07-31
Anyone try Mythetomer as a network remote for mythbuntu.  It uses your wifi/bluetooth enabled nokia n800/810, or a bluetooth enabled phone.

[Mythetomer Website]("http://netti.nic.fi/~icewood/mythetomer/index.php")

I am having an issue getting it setup.  It needs to know the name of the display that the mythbuntu frontend is running in.  I can't seem to determine what that name actually is.  I was thinking it was mythfrontend.real but that didn't work.

Any ideas on what this might be?

Thanks

---

### Post by dmfrey on 2008-08-03
I resolved this issue.  As it turns out, starting mythetomer with the -frontend command line switch an with the value of 'mythfrontend.real' was the correct solution, however, I was trying it out over a ssh session and it could not grab the display in that mode....My bad.

Starting it on the mythbuntu box directly allowed me to take control of it with my nokia n800 very nicely.

---

### Post by johenkel on 2009-03-13
So what exactly did you type in ? (syntax)

I am trying to get it set up but it won't work.
Telnet port in mythtv is enabled and port is right. My N800 does connect to it but any button I push does not do anything.

johenkel

---

