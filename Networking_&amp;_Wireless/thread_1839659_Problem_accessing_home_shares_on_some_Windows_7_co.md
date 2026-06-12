---
title: "Problem accessing home shares on some Windows 7 computers"
date: 2011-09-06
forum: Networking &amp; Wireless
---

### Post by KeithLM on 2011-09-06
I previously was running Fedora, set it up some years back, and had Samba configured to provide several public shares and home shares.  I have two Windows 7 computers, a laptop and desktop (which just had Windows 7 reinstalled the other day).  They both were accessing the samba shares fine.

Today I wiped the Fedora box and installed Ubuntu 11.04.  I set up the public shares using the gui tools fine.  Then I edited smb.conf to add the home shares.  I had several failed attempts from the desktop and then remembered the smbpasswd command and added a corresponding user on the Ubuntu server.  The desktop still failed to connect.  I then tried the laptop and it connected to all shares, including the home (after providing user and password of course), just fine. Desktop still can't connect.  I've rebooted the server and desktop since then, desktop still can't connect to home shares, public shares are fine, laptop still connects to all.

I suspect that either Ubuntu is running a firewall (I've yet to figure out if that's in the install or not) and blocked my desktop from accessing that share after multiple failed attempts, or something is wrong on the desktop with the firewall or something preventing it from access a protected share.  The laptop I configured over a year ago, so I could've forgotten some settings that I changed on it, although the desktop was able to access the Fedora home shares just fine.

---

### Post by KeithLM on 2011-09-06
Well today I tried connecting using the ip address instead of the hostname, and it connected.  Still can't connect to the private share with the hostname, but public shares work that way.  I highly suspect something is cached somewhere that is causing a problem.  I just wish I knew what I had to do to clear it.

---

