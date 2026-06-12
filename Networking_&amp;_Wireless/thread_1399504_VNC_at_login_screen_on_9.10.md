---
title: "VNC at login screen on 9.10"
date: 2010-02-05
forum: Networking &amp; Wireless
---

### Post by sbussy89 on 2010-02-05
I followed the instructions here ([http://jakeyoon.com/2008/11/19/enable-vino-vnc-server-for-login-manager-gdm-in-ubuntu/](http://jakeyoon.com/2008/11/19/enable-vino-vnc-server-for-login-manager-gdm-in-ubuntu/)) to get vino running at my login screen. (I skipped step 7 because I could not find the file, but this stp is not necessary). I tried to connect immediately after making the required changes, and it worked. I rebooted the machine from the VNC window, and tried to connect at login, but it didn't work. Now I cannot connect no matter what, even after I log in to the box with an attached keyboard. If I have an open VNC attempt and shut down the box, I get a notification saying that the VNC was cut off by the remote machine, so it must be getting to the box, but for some reason it's not showing up... Using RealVNC viewer, I enter the IP address of the box and it disappears, but the password prompt never shows up. Any help?

UPDATE: If I remove the line "/usr/lib/vino/vino-server &" from Default, I can connect to the box, but only after a user is logged in. I want to be able to log in to the box without a user logged in already, so I don't need a monitor and keyboard connected to the box.

---

### Post by Nerflander on 2010-07-23
i know it sounds stupid and im looking for same solution , maybe youve found it but make the user auto log in!

cheers

---

### Post by SubCool on 2010-07-31
> **Nerflander said:**
> i know it sounds stupid and im looking for same solution , maybe youve found it but make the user auto log in!

cheers

I have been considering the same thing, although not a very nice security idea. There has to be a way to VNC into the login prompt, without a hassle. i keep running into peoples "working" templates. Although i havent gotten a single one to work, and im running off a clean installation.

---

