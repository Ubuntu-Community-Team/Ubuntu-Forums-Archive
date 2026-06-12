---
title: "mplayer locks up on 'GNOME screensaver disabled'"
date: 2008-05-27
forum: Multimedia Software
---

### Post by arsenic23 on 2008-05-27
Is anyone else having their mplayer stall when when opening files in Hardy?

Every time I try to open mplayer, or just open a file in mplayer it stalls for almost a minute.  Opening the file in a terminal window with gmplayer or even just mplayer shows that I'm staller right after '[COLOR="DimGray"]GNOME screensaver disabled[/COLOR]' every time.

I had to disable '[COLOR="DimGray"]Stop XScreenSaver[/COLOR]' to get my files to load without all ot lag.
Does anyone know what is causing this?

---

### Post by bytor4232 on 2008-08-08
> **arsenic23 said:**
> Is anyone else having their mplayer stall when when opening files in Hardy?

Every time I try to open mplayer, or just open a file in mplayer it stalls for almost a minute.  Opening the file in a terminal window with gmplayer or even just mplayer shows that I'm staller right after '[COLOR="DimGray"]GNOME screensaver disabled[/COLOR]' every time.

I had to disable '[COLOR="DimGray"]Stop XScreenSaver[/COLOR]' to get my files to load without all ot lag.
Does anyone know what is causing this?

You probably have kubuntu installed.  Try starting the "dcopserver" and try again.  Thats what solved it for me.

---

