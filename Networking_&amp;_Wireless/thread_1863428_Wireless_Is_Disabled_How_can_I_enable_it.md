---
title: "Wireless Is Disabled? How can I enable it?"
date: 2011-10-17
forum: Networking &amp; Wireless
---

### Post by mrgoodfox on 2011-10-17
It seems that my Wireless is disabled. The hard key on the laptop is set to enable. Also I've clicked on "Enable Wireless" in the menu in top right of the desktop and is still checked.

I'm not sure why the wireless is not working right though.

---

### Post by mrgoodfox on 2011-10-28
I finally found the solution.

When typing "*rfkill list*", I was getting the following results:

```

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: ye

```

Which apparently they both should be set to "No". So my wireless was really disabled and not working and it had nothing to do with the wireless card.

I had to type the following command to enable it and everything was working.

```

rfkill unblock wifi

```

---

