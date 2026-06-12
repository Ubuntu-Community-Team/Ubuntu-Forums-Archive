---
title: "Any way to tell ubuntu to auto-reconnect to wireless?"
date: 2013-03-19
forum: Networking &amp; Wireless
---

### Post by dagfooyo on 2013-03-19
I'm running Ubuntu 12.10 on an HP Pavillion.  For some reason both the wired and wifi connections keep crapping out.  It might be a bad network card.  In any case, this computer runs processes for which it needs a constant internet connection.  Recently I've been waking up in the morning only to discover that it's been offline for several hours, and there's a dialog box that asks me if I want to reconnect to the wireless network.

Is there some way to set it to just automatically reconnect to a known wireless network whenever it loses its connection?  I would've thought this would be the default behavior, like it is on Mac and in Windows.

---

### Post by carl4926 on 2013-03-19
> [COLOR=#000000]I would've thought this would be the default behaviour,[/COLOR]It is
Works that way for me

---

### Post by varunendra on 2013-03-19
> **dagfooyo said:**
> Recently I've been waking up in the morning only to discover that it's been offline for several hours, and there's a dialog box that asks me if I want to reconnect to the wireless network.
In nm-applet drop down menu,
goto "Edit Connections" > Wireless tab > double click your connection > check "Connect automatically" check box > goto Wireless Security tab > save the correct encryption type and passphrase > save > close.

Hope it works as expected.

---

