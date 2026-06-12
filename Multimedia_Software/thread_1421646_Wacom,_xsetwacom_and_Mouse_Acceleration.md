---
title: "Wacom, xsetwacom and Mouse Acceleration"
date: 2010-03-04
forum: Multimedia Software
---

### Post by ola on 2010-03-04
I'm trying to configure my Wacom tablet in Ubuntu (9.4) and it's working pretty well!

I have one issue though. 

In Windows (with the Wacom drivers) I have the option to set both *Mouse Speed* and *Mouse Acceleration* (see attached screen shot). I normally like to increase acceleration and decrease speed.

In Linux (with [xsetwacom]("http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom")) I can only find one, *SpeedLevel*. Is it so, or are there any other way to configure it?

Thanks in advance!

//Ola

---

### Post by ola on 2010-03-06
Just found out about the option *Accel*. It can be used like this:

```
xsetwacom set "Wacom Graphire4 6x8" Accel 7
```

where you can set values between 1 and 7.

Haven't had a chance to really try it out just yet but I think that's what I need.

---

