---
title: "Vinagre Connects to OS X Machines; grdc/Remmina Do Not."
date: 2010-03-03
forum: Networking &amp; Wireless
---

### Post by AlphaMack on 2010-03-03
I've been trying to wrap my head around as to why grdc or Remmina do not connect to any of my OS X boxes while Vinagre does using the same VNC passphrases.  This problem has persisted since grdc 0.6.0 (older grdc builds from Jaunty used to work without problems).

I have tried combinations of the following to no avail:

machinename.local:5900
IPaddress:5900
machinename.local (no specified port)
IPaddress (no specified port)
User name on OS X (and checked to see if I'm authorized to use ARD)
No user name filled out

I'm not too thrilled about Vinagre and I would really like to use grdc/Remmina, so any help would be appreciated.

Just for kicks I tried installing xtightvncviewer, and that also works with my OS X boxes just by supplying the VNC passphrase.

---

### Post by AlphaMack on 2010-03-03
Never mind...found the reason.  By default the color depth is set to 256.  If I set the color depth to 24-bit, I can access the desktops.

#solved

---

