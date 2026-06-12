---
title: "About screen brightness on laptop"
date: 2008-10-13
forum: Multimedia Software
---

### Post by tsurko on 2008-10-13
Hello,
I've seen some threads about this problem but they seem a bit outdated so I'll start a new one.
I have Dell Inspiron 1525 running Ubuntu Hardy Heron, but I've experienced the same troubles on Toshiba Satellite U300. When Ubuntu loads it increases the brightness to the maximum. I can decrease it back manually via the Fn key (in BIOS it's decreased to minimum). But I have to do this every time I turn my laptop on or start a virtual machine either with qemu ot virtualbox. This is not a critical issue, but it's rather annoying. Have you got any solution for this?
Thank you in advance!

---

### Post by blackSP on 2008-12-24
I also have recent screen brightness problems but it seems nobody has an answer... See mine: [http://ubuntuforums.org/showthread.php?p=6416898#post6416898](http://ubuntuforums.org/showthread.php?p=6416898#post6416898)

---

### Post by auberginepop on 2008-12-24
I have a Toshiba laptop and had this problem with the brightness.

In my case it was solved for in four steps:

Run the command: modprobe toshiba_acpi

Install the package: fnfxd

Edit the config file for fnfxd, /etc/fnfxd/fnfxd.conf and uncomment the lines for brightness action keys

Restart fnfxd.

And that's it! My Toshiba laptop now has functioning brightness hotkeys. I hope it works for you.

From my reading of the fnfxd documentation the toshiba_acpi is the only dependency. However, will trying to fix the problem and before I had discovered fnfxd I did install various packages like toshutils, toshiba-hotkeys. On their own none of these fixed the problem and I do not think fnfxd needs them to work but if the steps above do not work perhaps you should try loading these packages as well.

I'd like to thank Timo Hoenig for the fnfxd package.

[http://fnfx.sourceforge.net/](http://fnfx.sourceforge.net/)

---

### Post by auberginepop on 2008-12-24
Forgot to mention...

The /etc/fnfxd/fnfxd.conf file also controls default brightness.

In my case it was a number from 1-8. AS you say it usually defaults to full brightness which in most cases is too much. After editing this line with a lower number the laptop now boots with a more sensible brightness.

---

