---
title: "Wireless networking problem .. multiple computers."
date: 2012-08-22
forum: Networking &amp; Wireless
---

### Post by oldsoundguy on 2012-08-22
OK .. problem with WIRELESS portion of my network with just Linux based computers.

The boxes have been working fine for years, but recently, after an update, went crazy.  four boxes involved .. one Myth, one 12.04, one 11.10 and one Mint running the 10.04 core.

NONE of them work wireless .. all work if I hard wire them in .. Windows box and PDA work just fine, so not the access point or the router.  

What happens is the units see the network and asks for the access code .. I plug in the code and it will connect and after a few seconds will disconnect ask for the code again.

Is there a fix?

Thanks.

---

### Post by Kirk Schnable on 2012-08-22
It sounds like you're having the problem across multiple different versions (likely different kernels and different drivers).  We should probably pick 1 computer to troubleshoot the issue on for the sake of simplicity.

The 12.04 machine is probably the best candidate, as it has the most recent kernel.

Thinking out loud: The only thing I could maybe see these machines having in common is the "network-manager" package.

Sometimes with wireless issues like the one you're describing, deleting and recreating the connection has been known to fix the problem, in my experience.  You may want to try that. If you're using a graphical interface (I assume you are) you should be able to right-click the network manager icon and go to "Edit Connections".  Delete anything that is related to your home wireless network.  Then, use the network manager to establish a brand new connection.

Please keep us informed, and we'll do our best to assist you further!

Kirk

---

### Post by oldsoundguy on 2012-08-23
Apparently, that worked (deleting and re-installing) on the 12.04 and the 11.10 Ubuntu.  Next will try the Mint box, as un installing failed miserably .. so going to update the Mint to the latest iteration and see IF that will do .. then move on to the Myth (my PVR).

---

### Post by Kirk Schnable on 2012-08-23
> **oldsoundguy said:**
> Apparently, that worked (deleting and re-installing) on the 12.04 and the 11.10 Ubuntu.  Next will try the Mint box, as un installing failed miserably .. so going to update the Mint to the latest iteration and see IF that will do .. then move on to the Myth (my PVR).

Glad to hear it. Hopefully it's just a config file that got screwed, and it won't happen on its own again.

---

### Post by oldsoundguy on 2012-08-23
Had to update the Myth box to 12.04 and it too 3 tries (install/remove the manager settings) before the password finally took.  And had to RE-INSTALL Mint (the new 13 is trash .. tried that and could not even find the settings for the network with that POS!) 

So, right now, all seem to be working. Thanks for the info.

---

