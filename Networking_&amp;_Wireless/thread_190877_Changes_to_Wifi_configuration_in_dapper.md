---
title: "Changes to Wifi configuration in dapper"
date: 2006-06-06
forum: Networking &amp; Wireless
---

### Post by hobbit1983 on 2006-06-06
Hi all,

Just upgraded my Dad's laptop to dapper from breezy.  He originally was using NDISWrapper to connect wirelessly to his network with no security turned on.

Since the upgrade ndiswrapper can see the wifi adapter and so can network manager.  However he cannot connect to it.  When I activate the adapter it breifly shows as being activated but sone goes back to deactivated.  

Has there been a change in network manager that means I have to use a secured network (I know I should (and have tif indeeried but his palm will not connect) in dapper while I didnt have to in breezy. ) and is there a way of turning this feature off!

If it helps it is a BROADCOM 4306 chipset that I am trying to get working.


Thx for any help (and indeed reading this far ;) )

---

### Post by spd106 on 2006-06-07
You need to decide wether to use bcm43xx or ndiswrapper modules. bcm43xx is part of the default kernel and so has to be blacklisted if you don't want to use it. Have a look around, there are many guides to this around the forum/wiki.

Here's an easy to follow guide to the whole mess [http://ubuntuforums.org/showthread.php?t=185174]("http://ubuntuforums.org/showthread.php?t=185174")

This one has the same information but for using ndiswrapper [http://ubuntuforums.org/showthread.php?t=187004]("http://ubuntuforums.org/showthread.php?t=187004")

Here's yet more [http://ubuntuforums.org/showthread.php?t=188290]("http://ubuntuforums.org/showthread.php?t=188290")

---

### Post by toLa` on 2006-06-07
Which is the best way to get a Broadcom up and running?

Theres so many how-to's floating around that I dont know which to follow, all with mixed results!

---

### Post by hobbit1983 on 2006-06-08
Finally got this working,

Thanks for the post that was the final bit of information I needed.  I have used the 43xx drivers that are in the kernel.  Although it needs to be reconfigured after each boot - thats nothing a little script can't fix.

As for the question I would recomend the BCM43xx route over using NDISWrapper.  it's a much cleaner solution.

---

