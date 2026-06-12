---
title: "Got wireless to work! YES! Except for one thing..."
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by greatn on 2009-11-08
I finally got my wireless issues to work. I have a Dell inspiron 1525 with a minipci card that was giving me a lot of trouble in Karmic. I got to the point where I could see networks but not connect. Now I finally got to the point where I can connect.

I used ndiswrapper, my problem was I had the wrong driver. I had a slightly older one. What I needed(and what you may need if you have a 1525 with the non-intel mini-pci) was "Dell_multi-device_A17_R174292". After I got ndiswrapper running pointed to the relevant .inf file for that driver, and used Hardware Drivers to get the Broadcom STA driver, it all finally worked.

That is, until I rebooted. If I reboot, all wireless disappears. If I go back into Hardware Drivers, Broadcom STA Driver says it is enabled but not in use. I do not know how to put it "in use" so I simply remove it, and then re-enable it, everything works again. From what I can figure I have to do this every time I restart the computer. Does anyone know what might be the cause of that?

---

