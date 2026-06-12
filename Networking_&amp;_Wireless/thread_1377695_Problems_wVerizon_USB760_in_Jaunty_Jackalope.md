---
title: "Problems w/Verizon USB760 in Jaunty Jackalope"
date: 2010-01-10
forum: Networking &amp; Wireless
---

### Post by root_worship on 2010-01-10
Hey ya'll,

 Wondering if theres anyone in the community who has had the same problem. Recently got a Verizon USB760, I still have time to take it back though. I ran VMACCESS Manager on a Windows box to register it (everything fine). Then installed VM manager on Linux w/ Wine (most current version in repos). 

  Set up 2 network connections both with Verizon, and Auto Mobile Broad Band CDMA. Heres the thing, it will recognize these network entries and use the card after a fresh install of VMACCESS Manager, but the program itself starts up then dies if you try to run it.

  If you unplug the card then plug it back in, it will mount but not be recognized in the network connections, and the previous settings I was using (CDMA and Verizon) are not available on a left click over the the network connection icons. This is strange.

   I have tried all sorts of tricks, but what I can do is go and wipe the /.wine directory (only way to fully nuke the VMACCS prog) and then reinstall the Wine package, then reinstall the access manager, try to run it, let it die, left click on network connections and it will let me use my previous connection settings. Is this ridiculous or what?
 

   It actually doesn't take that long, but I have to leave the connection on all the time or never take the card out. Any ideas?

   Running Ubuntu Jaunty 9.04 (heard that upgrading might solve, but also might break my system, no time for Linux repair fun).

   Box is Dell Dimension 2400 Maxed at 2 gigs/Ram, w/Nvida G4mx card. Everything else works great. The old Dells were mighty robust, this thing still runs pretty fast. Not sure bout keeping this card if it keeps up.

---

