---
title: "Remote Desktop Access"
date: 2010-02-19
forum: Networking &amp; Wireless
---

### Post by kerrydeare on 2010-02-19
Running Ubuntu 9.10.  In the Remote Desktop config dialog I get: "Your desktop is only reachable over the local network. Others can access your computer using the address 127.0.0.1 or tabatha.local."  I understand this means only the loopback ip address is available.  All my other machines show their true local ip address (e.g., 192.168.1.104) in this dialog.  Thus I cannot log on to this desktop from other machines.  When I try to do a remote logon from another Ubuntu 9.10 box (or from an XP box using a VNC viewer), I get: "Connection to 192.168.1.102 has been closed."  What steps are needed to make this machine show its actual ip address?  All file sharing between the various machines is working properly and all windows shares back and forth between XP and 'nix, and among the the vaious XP boxes and linux boxes are available as designed.

---

### Post by kerrydeare on 2010-02-19
By editing gconf (gnome/desktop/remote access) I discovered that "lo" was the only allowed listener. I removed this restriction and the system now listens on all network devices, and consequently can display a remote desktop when requested.

---

