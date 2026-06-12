---
title: "How can I enable wireless adapter?"
date: 2010-11-28
forum: Networking &amp; Wireless
---

### Post by thanasis3 on 2010-11-28
I am newbie at linux and Ubuntu and I have some problems enabling my wireless. I have spent many hours searching for solutions and couldn't find one for me (maybe don't apply it right - I am newbie). I have HP Pavilion dv6, dual boot Win7 and Ubuntu. At Win7 wireless is ok but at Ubuntu I can't enable my wireless adapter, so my laptop can't recognise any wireless network.

Plz help me get out of windows!

---

### Post by sikander3786 on 2010-11-28
Welcome to the forums :-)

Which wireless adapter is there?

If you have access to a wired network, plug it in your ethernet and the drivers might automaticlly pop up under system > Administration > Additional Drivers/Hardware Drivers.

---

### Post by thanasis3 on 2010-11-28
> **sikander3786 said:**
> Welcome to the forums :-)

Which wireless adapter is there?

If you have access to a wired network, plug it in your ethernet and the drivers might automaticlly pop up under system > Administration > Additional Drivers/Hardware Drivers.

I opened Additional Drivers, found "Broadcom b43 Wireless Driver" and installed it! The red (disabled) touch wireless button became blue (enabled) and everything is right!

Thank you very much :).

By the way what that drivers are? There is an ATI/AMD proprietary FGLRX graphics driver. Should I install this too? It's for my graphics card, if I'm right...

---

### Post by sikander3786 on 2010-11-28
You are Welcome :-)

Yes that FGLRX driver is intended for ATI graphics cards. Note that restricted drivers are not maintained by Ubuntu developers but we need them to utilize our hardware more efficiently. They are created by ATI or the relative hardware vendor.

[https://help.ubuntu.com/community/RestrictedDrivers](https://help.ubuntu.com/community/RestrictedDrivers)

You can enable them as they will provide 3d acceleration and better graphics.

---

