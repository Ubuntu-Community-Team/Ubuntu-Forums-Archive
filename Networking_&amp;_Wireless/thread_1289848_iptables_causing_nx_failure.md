---
title: "iptables causing nx failure?"
date: 2009-10-12
forum: Networking &amp; Wireless
---

### Post by caustic386 on 2009-10-12
Recently, I tried to set up ICS to route my Xbox 360 through my Ubuntu machine.  After following these directions:

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

up to and stopping at the Client section, my NX connection stopped working.  It gets all the way to "Negotiating link parameters" (usually the final step), then returns the error:

"The remote proxy closed the connection while negotiating the session.  This may be due to the wrng authentication credentials passed to the server."

Clicking on details returns:

"Info: Proxy running in client mode with pid '1413'.
Session: Starting session at 'Mon Oct 12 20:29:38 2009'.
Error: The remote NX proxy closed the connection.
Error: Failure negotiating the session in stage '7'.
Error: Wrong version or invalid session authentication cookie.
Session: Terminating session at 'Mon Oct 12 20:29:43 2009'.
Session: Session terminated at 'Mon Oct 12 20:29:43 2009'.
"

I'm assuming this issue has something to do with the iptables commands, but I have no experience with that.  I've tried to read through the FAQ, but it's quite overwhelming.  Anybody have any thoughts on it?

---

