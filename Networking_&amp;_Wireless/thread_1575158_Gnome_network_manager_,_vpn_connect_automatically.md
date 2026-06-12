---
title: "Gnome network manager , vpn connect automatically"
date: 2010-09-15
forum: Networking &amp; Wireless
---

### Post by sonicb00m on 2010-09-15
I have ticked the box Connect Automatically in the OpenVPN setup I configured in the gnome network manager but it doesn't connect on startup.

It connects perfectly ok if I manually select the VPN but i'd like it work immediately on launch.

I have autologin on Ubuntu but since there is no VPN password to decrypt I don't see why it should be a problem.

---

### Post by Cabalbl4 on 2010-09-16
Try my solution from here, [http://art.ubuntuforums.org/showthread.php?t=800330](http://art.ubuntuforums.org/showthread.php?t=800330)
it may help )

---

### Post by sonicb00m on 2010-10-03
Thanks a lot that worked perfectly.

Instead of creating another script I put the following the command in the gnome session startup

sh -c "sleep 20 && nmcli VPNAME start"

---

