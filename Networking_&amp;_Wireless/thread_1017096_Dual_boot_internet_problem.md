---
title: "Dual boot internet problem"
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by scebert on 2008-12-20
I had just XP and installed Intrepid so it is a dual boot system. Now the internet (DSL with an Ethernet connection) works in either OS when the computer is first turned on, but if it is restarted into the other OS, it doesn't work. Even if the computer is turned off and unplugged, then turned back on it still doesn't work except in the OS it was first booted into. This seems to be reset when it is turned off for a few hours and there is internet only in the OS it is then booted into.

---

### Post by pytheas22 on 2008-12-20
That's weird.  Even if you unplug the power (and remove the battery if applicable) for a few minutes, the ethernet won't work again when you reboot unless you wait several hours?

It works if you boot back into the same operating system, correct (i.e., if you're connected in Ubuntu and then immediately reboot back into Ubuntu, you don't lose the connection...only if you booted from Ubuntu into Windows, or vice-versa, would it break)?

If you could please also post the output of this command, we can do some googling to see if others have had this problem with your particular ethernet card.  I suspect that it has something to do with some peculiarity affecting your network card:
```

lspci -nn
```

---

