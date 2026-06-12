---
title: "Open VPN apply button greyed out"
date: 2009-12-04
forum: Networking &amp; Wireless
---

### Post by toypilot on 2009-12-04
I am trying to set up OPEN VPN, 

Using preferences -> network connections -> VPN

When I atttempt to set up the VPN the apply button is greyed out.

Help appreciated.

Thanks in advance

---

### Post by toypilot on 2009-12-05
Bump? Anyone know how to run network connections from command line so I can try as sudo in case its permissions problem?

---

### Post by Loopk1n on 2009-12-14
Having the same issue, I can set up all preferences but can't never apply because the button is greyed out. Trying to set up OpenVPN.

---

### Post by stomakmonkee on 2010-01-09
I had this problem myself, and this usually happens when there is not enough information for OpenVPN to go on, or if the information is incorrect for OpenVPN.  OpenVPN is best used for Cisco Anyconnect.  If your VPN is PPTP, which many are, you might just need to use that.  To install that you would use

sudo apt-get install network-manager-pptp.

Hope this helps.

Blake.

---

