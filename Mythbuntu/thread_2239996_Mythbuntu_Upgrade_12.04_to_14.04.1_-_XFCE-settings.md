---
title: "Mythbuntu Upgrade 12.04 to 14.04.1 - XFCE-settings Bug results in blank screen"
date: 2014-08-17
forum: Mythbuntu
---

### Post by flecki on 2014-08-17
I upgraded and noticed that every time i switch away from Mythtv either on my TV or on the reciever the HDMI connection drops and can´t be resumed without a reboot.

It seemed the HDMI Handshake somehow killed the screen.

Searching the Web brought the solution and i thought i let you know.

Use the Startup/Session behaviour screen and remove xfce-settings daemon from the startup list first and then kill the running daemon in the sessions tap - this solved it for me.

Hopefully this gets fixed in XFCE soon....

---

