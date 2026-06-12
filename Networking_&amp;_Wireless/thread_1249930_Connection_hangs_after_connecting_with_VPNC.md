---
title: "Connection hangs after connecting with VPNC"
date: 2009-08-25
forum: Networking &amp; Wireless
---

### Post by onlinespending on 2009-08-25
I am desperately trying to get a working VPN connection to my work's Cisco-based VPN server on Ubuntu 9.04.  Using Cisco's own vpnclient works well, besides for the fact that there's a known bug with it and dual-core machines.  I'm not willing to disable one core while using VPN.

So I've been trying to get VPNC to work.  I actually had vpnc working well without issue in a previous build of Ubuntu (perhaps Gutsy).  I can connect othe VPN server fine and can even establish an SSH connection to my work Linux box.  However within seconds the connection freezes.  I cannot type anything into the SSH terminal.  The web doesn't work.  I am forced to issue 'vpnc-disconnect' and close the SSH window.

I have tried adjusting the MTU (to the same value, 1300, used by the Windows Cisco VPN Client, which by the way works just fine) but that did not work.  I'm out of ideas.  I appreciate any possible suggestions.  Thank you.

---

