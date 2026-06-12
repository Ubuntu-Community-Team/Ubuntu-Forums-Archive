---
title: "refreshing view of smb shares"
date: 2009-07-27
forum: Networking &amp; Wireless
---

### Post by sites on 2009-07-27
Here's my scenario.

My Hardy box is running.  I turn on my Mac, and the Hardy pc shows up as a shared system in Finder.  I then open a file browser on the Hardy pc and look for samba shares, expecting to see the Mac.  At network:/// i do not see the Mac, but i can go in to Windows Network, then into the WORKGROUP network, and there is the Mac along with the Hardy pc.  Both computers are using WORKGROUP as the netBIOS name, so the Mac should be showing up at the network:/// window.  Sometimes it does, but in this sequence of events it does not.

Aside from restarting smb services on my Hardy pc, how else can i get the Mac to show up at network:/// ??  Actually, restarting smb services is a hit and miss workaround & i wind up having to restart all the computers. Clicking "refresh" in my file browser doesn't do the trick.  This same issue arises with Windows pc's, too, so i think it's a problem with smb in ubuntu.  I know it sounds a bit nit-picky, since i can browse to the computer through the Windows Network link in the file browser, but sometimes they don't show up there either.

edit: I'm using a WRT54G running Tomato firmware, fyi, and there are two other Hardy computers on this network via wireless. The Hardy pc i've referred to in this post is connected to the network via AirportExpress set up in WDS with the Linksys.

cheers
sites

---

