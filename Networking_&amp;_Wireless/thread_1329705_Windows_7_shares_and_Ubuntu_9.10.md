---
title: "Windows 7 shares and Ubuntu 9.10"
date: 2009-11-17
forum: Networking &amp; Wireless
---

### Post by mhouston100 on 2009-11-17
Guys, after searching multiple forums and following multiple threads I finallyfound a solution to my issue of accessing Windows 7 shares from Ubuntu 9.10 (and more specifically XBMC.

I had tried all combinations of security and connections, passwords, no passwords etc and nothing worked.  Then I came across this thread here:

[[COLOR="Blue"]IRPStackSize[/COLOR]]("http://linux.derkeiler.com/Newsgroups/comp.os.linux.networking/2006-10/msg00629.html")

And followed the steps to adding/increasing the IRPStackSize and now shares are working flawlessly.  I can browse through Nautilus, I can mount using CIFS and I can access no problems through XBMC.

Basic instructions:

On the Windows 7 machine find the registry key:

**HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\LanmanServer\Parameters\IRPStackSize**

and increase the number (decimal) to 15.  If it is not there create it.

This is now working fine without changing any other settings on W7 or Ubuntu.

Thought it might be handy as the question seems to be asked a fair bit.

For instructions mounting with CIFS:

[[COLOR="Blue"]Mount Windows shares with CIFS[/COLOR]]("http://ubuntuforums.org/showthread.php?t=288534")

---

