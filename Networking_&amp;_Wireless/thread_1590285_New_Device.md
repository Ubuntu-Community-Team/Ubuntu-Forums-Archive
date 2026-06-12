---
title: "New Device"
date: 2010-10-07
forum: Networking &amp; Wireless
---

### Post by Colo2 on 2010-10-07
Hello

My ethernet card died, so I put another one in. I booted from the Live CD and the ethernet connected right away, however on my installation, it refuses to see the new card. ifconfig brings up "ham0" (hamachi) and "lo." 

Does anyone know how I can get my new ethernet card configured? I know that it works with ubuntu because of the livecd test.
Thanks ;)

---

### Post by JOHNNYG713 on 2010-10-07
Try shutting down the computer, remove the new card, and reboot to the full desktop with out the card installed, shut down, replace the card, and re-start, I have had this happen with new sound cards as well as new Ethernet cards and this did the trick! Good luck!

---

### Post by Colo2 on 2010-10-07
hey

Doesn't work :(

I guess I'll just have to re-install ubuntu :(

Thanks anyway

---

### Post by Zimmer on 2010-10-07
Have you tried  System>Preferences>Network Connection and tried to add it as a connection?

---

### Post by Colo2 on 2010-10-07
> **Zimmer said:**
> Have you tried  System>Preferences>Network Connection and tried to add it as a connection?

Forgot to mention, I removed gnome-network-settings thing, so I can't do any of that via GUI. Any command line help?

---

### Post by Colo2 on 2010-10-07
network-manager-gnome < (I think) to be precist. So anything I do, is in terminal.

---

### Post by Zimmer on 2010-10-09
If it is still installed..
nm-connection-editor

If NOT installed, re install network-manager-gnome from the Live CD  using synaptic.. see here:
[https://help.ubuntu.com/8.04/add-applications/C/offline.html](https://help.ubuntu.com/8.04/add-applications/C/offline.html)

---

