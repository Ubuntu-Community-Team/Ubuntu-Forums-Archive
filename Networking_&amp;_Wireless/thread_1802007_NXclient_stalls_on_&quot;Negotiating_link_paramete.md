---
title: "NXclient stalls on &quot;Negotiating link parameters&quot;"
date: 2011-07-11
forum: Networking &amp; Wireless
---

### Post by jdsmofo on 2011-07-11
I have a laptop with Kubuntu 10.04 and am connecting to a desktop with the same kernel, that runs a freenx server.   For many months I could use Nomachine's nxclient to connect to it, and show the screen of my desktop on my laptop.  However, a month or so ago, it stopped working.  Everything connected fine, but when it opened the screen to show the desktop, it would just crash, with no error messages, or anything.  I could still SSH to the machine, but no NX client.  I checked out the error logs, and it gave a warning that the versions were different, so I updated the NXClient on the laptop to 3.5   This helped nothing. I deleted the cache, and now it hangs at "Negotiating link parameters".  I checked the session log, and it gives:

Info: Proxy running in client mode with pid '5986'.
Session: Starting session at 'Mon Jul 11 11:06:46 2011'.
Info: Connecting to remote host '127.0.1.1:6000'.
Info: Aborting the procedure due to signal '15'.
Session: Session terminated at 'Mon Jul 11 11:07:16 2011'.

I don't know if it matters, but both machines are behind my router. 

I cannot find any more information about the cause of the crash.  

This is really a shame, because it was a beautiful connection before that worked very easily.

---

