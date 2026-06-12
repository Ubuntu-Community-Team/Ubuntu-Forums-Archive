---
title: "Cannot connect to local network"
date: 2010-03-25
forum: Networking &amp; Wireless
---

### Post by AngelsJinx on 2010-03-25
Hey guys, up until about four days ago connecting to the local LAN was as simple as booting Ubuntu, and letting nm-applet automatically connect on Auto Eth0
But the other day it just randomly stopped working, with no cause that I can think of. I can still connect to the internet (This is via a PPPOE connection, running through the same wired interface) so it can't be a hardware problem with the ethernet port/cables themselves.
nm-applet just stays spinning in circles, and nothing ever happens.
I tried deleting the auto Eth0 entry, and creating another LAN entry with exactly the same settings, but I still get the same problems.
Does anyone know of a way to completely restore nm-applet settings? Or some other way to give me access to the local network?

---

### Post by RedSingularity on 2010-03-25
How about a fresh install of the nm-applet?

To purge all settings of it do the following.

sudo apt-get autoremove network-manager-gnome ; sudo apt-get purge network-manager-gnome

Then reinstall it.

---

### Post by AngelsJinx on 2010-03-25
Ok, I tried the commands you suggested, restarted, and when I reinstalled it was as if nothing had changed.
So, I ran sudo apt-get clean
which cleared my apt-cache, then tried purging and reinstalling all over again.
I'm back to exactly where I was except heres the wierd part, nm-applet still remembers my pppoe connection.. so maybe configuration files weren't wiped at all?
I'm going to try purging and reinstalling network-manager now, so hopefully that fixes it.
I'll post back with my results when I'm done trying this, but if anyone else can think of anything, it'd be greatly appreciated.

---

### Post by AngelsJinx on 2010-03-25
Well that solution sort of worked.
However, while nm-applet works perfectly fine to connect to the local network, I can no longer use my pppoe connection, which is required to get online.
So to access the internet I need to run:
 sudo pon dsl-provider

While thats not to bad, I would really like to have a nice simple applet that lets me manage my connections. Does anyone know of an applet I could use instead?
I've heard in many places that the version of nm-applet maintained in the repo's doesn't work with PPPOE connections, but I'd hoped that would have been fixed by now.

Anyone able to provide a solution for me?

---

