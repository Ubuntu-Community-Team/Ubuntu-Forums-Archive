---
title: "VPN from Windows 7 into Ubuntu 10"
date: 2012-05-30
forum: Networking &amp; Wireless
---

### Post by infinitelink on 2012-05-30
Bangin' mi head against the walls here: 

I just received a new machine from Lenovo, a laptop, which I'll be dual-booting, but want to RDP into Ubuntu (10) on a desktop from Windows on the laptop. The Lenovo connects wirelessly to a router into which the desktop is plugged. The desktop, when plugged into that router, has ip 10.0.0.40 while the Lenovo is 10.0.0.42. It is a Netgear wnr1000v.2 and I have gone to port forwarding and added a special service of RDP/UCP with 3389 set as the in- and out- bound port, and an ip address of 10.0.0.40. The problem is that when I go to the Remote Desktop tool on windows and enter either 10.0.0.40 or anon.local (the machine/domain I am given by the Remote Desktop Preferences tool on the Ubuntu machine as what can be used for access, where the ip address is the other thing that can be used). When I try to connect from Windows, the result is always 

"Remote Desktop can't connect to the remote computer for one of these reasons:
1) Remote access to the server is not enabled
2) The remote computer is turned off
3) The remote computer is not available on the network

Make sure the remote computer is turned on and connected to the network, and that remote access is enabled."

My settings under "Remote Desktop Preferences" in Ubuntu are

"[check] Allow other users to view your desktop.
[check] Allow other users to control your desktop.
[...]
[check] Require the user to enter this password: [...]
[check] Configure network automatically to accept connections."

I am also not able to see the desktop machine under "Network" in windows. Curious if others have problems like this, and whether anyone knows how to make this work.

**UPDATES/REPLIES TO REPLIES:**
> **steeldriver said:**
> BTW VPN is something different - you might get more hits if you change your thread title

ACCK! I knew that but mistyped anyways! Dumb dumb...and thanks. :) Also thanks for mentioning the Windows Firewall: didn't think about it, as I haven't used Windows since XP YEARS ago.

-- I ADDED mstsc.exe (the MS RDP utility) to the firewall's "allowed programs" list and tried again: no good.

---

### Post by steeldriver on 2012-05-30
That sounds excessively complicated - what RDP server package are you using on the Ubuntu side?

I usually use VNC rather than RDP but I just installed the xrdp package on 11.10 (Xubuntu) and it worked right out of the box - no config required on either side. I just typed the LAN IP of the Ubuntu box into the Windows Remote Desktop client and it opened a session manager right away. This was from XP Pro.

I wouldn't expect the router to block RDP *within* your LAN - the Windows firewall possibly

BTW VPN is something different - you might get more hits if you change your thread title

---

