---
title: "Teamviewer on vnc clients only"
date: 2012-12-12
forum: Networking &amp; Wireless
---

### Post by 0xicl33n on 2012-12-12
How can i have it so teamveiwer starts up inside vnc desktops only instead of on my main monitor? Add it vncstartup or something?

So when i start up vnc, teamveiwer is told to run in that vnc session instead of my desktop.

i would be using tightvncserver.


I know you usually use one or the other, but teamviewer is so much easier to allow friends to connect over the internet, port forwarding for vnc is quite a pain.

---

### Post by ahallubuntu on 2012-12-12
I don't think what you have in mind is possible.  Either use VNC or use Teamviewer.  One or the other.

You might look into Hamachi for an easy-to-setup VPN that doesn't require you to forward ports.  Hamachi works with Windows, Mac, and Linux.  It's owned by the same company that owns LogMeIn dot com.  Hamachi has an easy control interface so you can enable/disable your connection to it as needed.  If you want your friend to be able to VNC to your desktop, just login to Hamachi, and if your friend also connects you'll be on the same network and they can VNC to your computer.

VNC isn't secure in itself when used point to point over the internet, because it's not encrypted.  Use VNC over a VPN or SSH to be secure.

---

