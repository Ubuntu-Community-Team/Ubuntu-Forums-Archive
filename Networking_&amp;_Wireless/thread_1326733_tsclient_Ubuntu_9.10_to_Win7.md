---
title: "tsclient: Ubuntu 9.10 to Win7?"
date: 2009-11-14
forum: Networking &amp; Wireless
---

### Post by MichaelJohannes on 2009-11-14
Hello,

First off, let me just say I think 9.10 is a great desktop OS. I thoroughly enjoy using it.

However, I do require some programs I use in Windows which do not work well in WINE nor do they work well in Cross Over Linux.

To get around this I've created a virtual machine running Windows7 64-bit Ultimate where I can run my Windows apps. But when I try a remote session to this virtual computer I find it to be extremely slow. I've read that many users have experienced issues going from Windows to Ubuntu 9.10 Karmic via tightvnc, realvnc, etc with slow performance (and that it's generally fixed easily by disabling the desktop effects), but I have yet to read anyone having issues going from Ubuntu 9.10 Karmic to Windows 7 via RDPv5 using the tsclient built-in RDP software.

Has anyone else had issues with this? I should also point out that my servers (running Windows 2008, 2003) have no noticeable performance - it only seems to be happening with Windows 7.

Any suggestions on how to increase the speed / performance going from ubuntu 9.10 to Windows 7 via tsclient (tcp 3389)? Right now it's choppy, slow.

Thanks for your time,
Mike.

---

### Post by MichaelJohannes on 2009-11-15
I've solved this issue.

My first impression was that it had something to do with the tsclient. It didn't.

The issue can be resolved by disabling the theme from the Windows7 desktop. Use the Windows Classic theme instead of the Windows 7 Basic theme. It's not perfect but it's much quicker.

HTH someone else.

Mike

---

### Post by sefs on 2011-05-25
This very same thing has vexed me for months. Thank you for this tip!

P.S. In researching this problem I also came across Remmina (RDP) Client.  It is in the repos, and heads over heals above tslient.

Thanks!

---

