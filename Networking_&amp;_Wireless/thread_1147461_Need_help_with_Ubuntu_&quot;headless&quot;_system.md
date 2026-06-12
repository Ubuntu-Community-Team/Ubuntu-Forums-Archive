---
title: "Need help with Ubuntu &quot;headless&quot; system"
date: 2009-05-03
forum: Networking &amp; Wireless
---

### Post by jimbo6846 on 2009-05-03
Hi guys, I'm incredibly new to Linux (2nd day working with it, hehe) and I'm having some trouble getting my Ubuntu set up to work without a monitor and keyboard/mouse.
 
A little background:
 
I have multiple other systems in the house that I want to use to connect to this Linux box, all of which have windows Vista or XP installed.  On my Ubuntu machine, I have installed and configured vncserver as well as enabled the XDMCP protocol.  On my windows machines, I have installed UltraVNC (TightVNC would simply NOT work.  Nothing but a gray desktop that was not functional at all.  after hours of troubleshooting, I gave up and installed UltraVNC on my Vista machine and it worked just fine.) as well as Xming.  UltraVNC connects just fine, but requires that the machine already have a VNC user logged in, otherwise it won't connect.  Xming doesn't require that a user be logged in, but it creates it's own sessions and as far as I can tell, there is no way to get those sessions to stay open when closing the Xming window.  
 
What I basically want to do is this:  I want to be able to remotely connect to this linux box no matter if someone is logged in or not and I want that session to remain open if I close the remote window, just like RDP for the Windows environment.  Is there any way to do this, because it seems like neither vncserver nor Xming are capable of this.
 
Do I need a different OS?  I installed the "desktop" version of Ubuntu 9.04.  Should I install the "server" version instead?  Any help/suggestions are very much appreciated.  Let me know if any more info is needed.  Thanks in advance.

---

