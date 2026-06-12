---
title: "Does Kubuntu's Network Manager suck?"
date: 2008-12-18
forum: Networking &amp; Wireless
---

### Post by NagWolf on 2008-12-18
Hi All;
I've been a big fan of Mint Linux for the past year and decided to upgrade the KDE3.x on there to KDE4.1 via a bit of dodgeball repository adding of Ubuntu.
This worked 99% brilliant so I decided to move on to the full Kubuntu edition and not just a Nix based on Ubuntu (Mint) that's been hacked to give so more Ubuntu stuff.

Please could someone just tell me though that following the route to get your Static IP network up and running as per this post is not the final answer:
[http://ubuntuforums.org/showthread.php?t=991708&highlight=network+setup](http://ubuntuforums.org/showthread.php?t=991708&highlight=network+setup)

I've transitioned completely to Linux from Windows and have enjoyed all the convenience of Plug and Play as perfected in Linux/Ubuntu/Mint... up until now.

I did the New Connection setup, Static, put everything in except for the "DNS Search" which I haven't encountered before. Network cable is plugged in but State shows as Disconnected...

Is there a way to install a different Network manager other than the default one coming with Kubuntu?

Thanx peoples
N8Wolf

---

### Post by The Cog on 2008-12-18
I don't know about the Kubuntu network manager, but I have just succesfully installed wicd on Kubuntu and it works nicely. I think you have to uninstall the default network manager first, and you also have to install python-gtk2 which can be tricky if your wireless isn't working (I used a wired connection for that).
[http://wicd.sourceforge.net](http://wicd.sourceforge.net)
I downloaded the .deb file and double-clicked it to install it.

---

