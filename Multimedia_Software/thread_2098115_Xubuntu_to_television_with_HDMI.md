---
title: "Xubuntu to television with HDMI"
date: 2012-12-25
forum: Multimedia Software
---

### Post by d3fau1t on 2012-12-25
For whatever reason, I thought it would be cool to get my brother and his family a netbook and install XBMC on it so they could use it as a complement to their home entertainment system. Unfortunately,  connecting it via hdmi just shows a black screen (although the Acer logo appears at boot). So now I look totally stupid, the gift is worthless, and Christmas is ruined.

The underlying system is Xubuntu, but it's set to log in to XBMC. Logging into Gnome Shell makes no difference,  the screen is black.

This is the first time I've seen my brother and his family in years, and it's kinda sad that this happened.  I don't know why, it outputs fine to my projector at home.

Help!!!!1

---

### Post by d3fau1t on 2012-12-26
The netbook is an Acer Aspire One D270-1466, with an Intel GMA3600 graphics card. When it boots, the Acer logo shows on the television, and then the screen goes black. If I start it in recovery mode, all of the boot text appears on the TV screen.

The TV is a Sharp Aquos 60 inch. I was able to get an xorg.conf generated, but it didn't seem to help, so I deleted it.

Why does the logo show and the boot text in safe mode, but not X?

---

### Post by fdrake on 2012-12-26
which version of xbuntu do you have?

post the results of:
```

less ~/.xsession-errors

```

> 
Why does the logo show and the boot text in safe mode, but not X?
you mean console mode?

---

### Post by d3fau1t on 2012-12-26
Thanks.

It gives "no such file or directory".

I just was asking why it showed text output when it booted in recovery mode, but not in X.

It sure would be nice if I could get this working!

---

### Post by fdrake on 2012-12-26
> **d3fau1t said:**
> Thanks.

I just was asking why it showed text output when it booted in recovery mode, but not in X.

well it's easy for the driver to handle simple txt that advance graphics, or it can be that is not conf right

also the code was ```

less ~/.xsession-errors

```
i corrected my post

---

### Post by d3fau1t on 2012-12-26
Hi,

It still says "no such file or directory."

---

### Post by fdrake on 2012-12-26
what about updating?
```

sudo apt-get update

```
restart.

also what version of xbuntu do you use?

---

### Post by mörgæs on 2012-12-26
Changed the title to a more informative one.

---

### Post by d3fau1t on 2012-12-26
Quanzal. It has all the latest updates.

---

### Post by xc3RnbFO8P on 2012-12-26
Try this:
[http://ubuntuforums.org/showthread.php?t=1613132]("http://ubuntuforums.org/showthread.php?t=1613132")

---

### Post by d3fau1t on 2012-12-26
Booting with nomodeset option didn't help, unfortunately. 

Thx anyway.

---

