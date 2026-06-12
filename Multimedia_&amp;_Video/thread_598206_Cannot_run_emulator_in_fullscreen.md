---
title: "Cannot run emulator in fullscreen"
date: 2007-10-31
forum: Multimedia &amp; Video
---

### Post by dark_ixion on 2007-10-31
I've tried running SNES9x in fullscreen on an XFCE desktop with the -fs parameter, but it says something along the lines of "operation not permitted".  I've tried the command chmod 4750 `which snes9x` to resolve this but it still doesn't work, and even tried running as root, but still doesn't work.

What's going on?  There was an additional instruction I read that suggested "Please adjust group and world permissions as necessary to suit your distribution."  I'm not sure what exactly I'm required to do.

Anyone know?

Thanks

---

### Post by picometer on 2007-12-02
Hello.

I played Super Mario RPG in zsnes32 but occasionally faced freezing bug.

so I tried snes9x and had the same problem as yours.

even excuting with root permission didn't work.

(because NVIDIA graphic cards didn't support DGA, I hadn't DGA extensions)

but I found solution finally!

Try using this instead of original snes9x-x.

[http://www.snes9x.com/phpbb2/viewtopic.php?p=22874](http://www.snes9x.com/phpbb2/viewtopic.php?p=22874)

everything seems to be excellent!

---

### Post by picometer on 2007-12-16
updated

---

