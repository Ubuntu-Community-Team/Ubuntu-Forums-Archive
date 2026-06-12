---
title: "Remote Login over Wireless?"
date: 2009-01-31
forum: Networking &amp; Wireless
---

### Post by Another Monkey on 2009-01-31
I have got wireless going from boot after an fiddling with NetworkManager*.  That's great!

However, something seems to be wrong with remote login.
I can select the remote machine OK, but than all I get is a black screen with a cursor in the shape on an "X".  If I just leave it there, the screen seems to flicker from time to time but always comes back to the black screen with the "X".

If I fiddle about with NetworkManager to make the wired connection available from boot, I can remote login to the same machine with no trouble at all.

Other connections (e.g. Remote Desktop) work fine over wireless - it's just remote login, so I don't think it's bandwidth causing the problems.

Why would remote login work over wired but not wireless?  Any ideas?

Thanks.

(*Trick seems to be to not rely on "System setting" but to keep checking/unchecking "Connect Automatically" as well so that the changes actually take).

SOLVED: I ran an update on both system and also allows port 177 (XDMCP) and 6000-6015 (XWindows) on both.  I am not sure which change fixed and I only think I need the open ports on the server side, but I do not have time to check.

Still weird that it would work over the wire without these ports and that there was nothing showing in the firewall logs.

---

