---
title: "ATI S-Video out"
date: 2006-06-02
forum: Multimedia &amp; Video
---

### Post by Tweek84 on 2006-06-02
I'm having some difficulty getting my S-Video out to work with my x1300pro. The television actually displays a clone of the main display right up untill the xserver starts, then it goes dead.

I am using the proprietary driver from the ati website, and currently have dual monitors working just fine. I realize I'll have to disable one of the monitors to make the TV out work.

However the problem is if I do an aticonfig --query-monitor i get this:

```

  username@compy2600:~$ aticonfig --query-monitor
  Connected monitors: crt1, crt2
  Enabled monitors: crt1, crt2

```

or with the second monitor unplugged

```

  username@compy2600:~$ aticonfig --query-monitor
  Connected monitors: crt1
  Enabled monitors: crt1

```

I haven't even started to try and configure the xorg.conf yet since it doesn't look like the video card is even detecting the tv out. 

I'm not even really sure where to start troubleshooting this one so any input would be greatly appreciated.

---

### Post by Tweek84 on 2006-07-01
Bump.

Any ideas anyone?

---

### Post by evil_elman on 2006-07-02
Taken from ATi's release notes on the current drivers:

> 
TV Out is currently not supported on the ATI Radeon® X1x00 products. Further details can be found in topic number 737-22057


Document can be found here: [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.26.18.html#181179](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.26.18.html#181179)

I don't have any further information, though.

---

### Post by Mastus on 2006-07-02
aticonfig --enable-monitor   may do the trick.

Or not... In my case, TV is not recognized either, but when I add the 
line "ForceMonitors crt1,tv" on xorg.conf, I get an corrupt display, and no signal on TV when enabling monitors...

Stupid ATI control panel, because it does not have the TV out tab...

---

### Post by Tweek84 on 2006-07-15
Not supported, that'll do it. I just assumed it was somethin i had done.

Thanks!

---

