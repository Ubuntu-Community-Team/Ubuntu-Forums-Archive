---
title: "Mandriva 2009 does not recognize wireless card and crackiling sound"
date: 2008-10-21
forum: Mandriva/Mageia
---

### Post by shuttleworthwannabe on 2008-10-21
I just freshly installed Mandriva 2009 Gnome on my acer travelmate 6292

Intel chip built in graphics card
Sound card is Intel HDA
Wireless card is Intel PRO/WIRELESS 4965 AG

The strange thing is that wireless signal was working and LED light was on when in LIVE CD mode. Sound however was still crackiling,

Anyone can help me fix this?

BTW, I also updated immediately after installing,

S

---

### Post by TeaAge on 2008-10-22
Wireless issue:
Maybe the wireless modul was removed during after-install process, when the installer asks you to remove unneeded software, although the modul is needed on your system.

Sound issue:
Did you try to disable pulseaudio (Mandriva Control Center -> hardware -> Sound)?
Or maybe a strange mixer setting?

Regards,
TeaAge

---

### Post by AdamWill on 2008-10-22
For the first point I think TeaAge is on to something; I'm fairly sure there's a bug where One's post-install driver removal system removes the firmware for the 4965. Using a wired connection, re-install the iwlwifi-4965-ucode package, if it got uninstalled.

For the second point, run a mixer - kmix or alsamixer - and disable / mute the 'Analog Loopback' channel.

---

### Post by shuttleworthwannabe on 2008-10-22
thanks, wireless issue---that was itl
Sound: Sound is now working, but flash sound is off; I have this issues in Ubuntu as well, but recent flash update solved that.

Thanks all
S

---

### Post by AdamWill on 2008-10-23
My personal advice would be to install Flash 10 (just using the RPM on Adobe's site is fine) and remove libflashsupport.

Unfortunately we couldn't ship Flash 10 with 2009 as it was still an RC at the time, and our agreement with Adobe does not allow us to ship pre-releases. But Flash 10 is a lot better at working with Pulse than Flash 9 was: it works properly natively, no need for libflashsupport.

---

### Post by shuttleworthwannabe on 2008-10-23
In ubuntu Ibex flash 10 works fine; I will try your suggestion MDV 2009,
again thanks
S

---

