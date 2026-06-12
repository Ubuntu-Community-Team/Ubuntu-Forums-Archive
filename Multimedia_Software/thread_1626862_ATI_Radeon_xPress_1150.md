---
title: "ATI Radeon xPress 1150"
date: 2010-11-20
forum: Multimedia Software
---

### Post by spark0uk on 2010-11-20
Hey,

I've just installed Ubuntu v10.10 on a Dell Inspiron 1501 - the specs are as follows:

AMD Turion 64 x2 TL-50 1.6GHz
2GB DDR2 RAM
ATI Radeon xPress 1150 Graphics
250GB SATA HDD

When I start the computer, I get multicoloured vertical bars down the screen, and the entire operating system is completely unusable. I've no idea what to do, as I can't even get to the login screen to do anything about it - has anyone any ideas?

Kind regards,
Phil

---

### Post by kpetrie77 on 2010-11-28
Having an identical issue with a Dell Inspiron 1501 and ATI Radeon xPress 1150 card. Just installed 10.10 and get grey horizontal stripes with colored vertical stripes after GRUB loads.

Hooked up a second monitor and it showed just fine. FN+F8 will cycle through the different display settings and eventually set the 1501 display to something I can use and set as default. From this I have determined the 50Hz setting is the cause.

Next issue is after setting to 1280x800 at 60Hz as default, it does not stick on reboot and I need to repeat the external monitor thing again.

Best Regards,
Kevin

---

### Post by kpetrie77 on 2010-12-28
> **spark0uk said:**
> I've just installed Ubuntu v10.10 on a Dell Inspiron 1501 - the specs are as follows:

AMD Turion 64 x2 TL-50 1.6GHz
2GB DDR2 RAM
ATI Radeon xPress 1150 Graphics
250GB SATA HDD

When I start the computer, I get multicoloured vertical bars down the screen, and the entire operating system is completely unusable.

Phil,

Found the solution on another board, this prevents the screen mode from changing during boot. Open terminal and enter

```
sudo gedit /etc/default/grub
```

Now change **GRUB_CMDLINE_LINUX=""** to **GRUB_CMDLINE_LINUX="nomodeset"**

Close gedit to return to the terminal window. Now we need to update grub.cfg

```
update-grub
```

No more grey lines!

Kind regards,
Kevin

---

