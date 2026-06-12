---
title: "fglrx - remove pairmode"
date: 2007-08-13
forum: Multimedia &amp; Video
---

### Post by wblancqu on 2007-08-13
Hi folks,

The problem is as follows:
I want to install Compiz Fusion + Xgl. It doesn't work and I found out why. Looks like my GDM boots up in dual screen mode (but only then, not afterwards). Compiz fusion doesn't work in dual screen mode. So I tried deleting the dual screen entries in xorg.conf.

BUT:

I had a couple of so-called "pairmodes" which I created with aticonfig, so I have to remove them. When I do:

```
sudo aticonfig --list-pairmode
```

I get one entry: 2560x800

When I do:

```
sudo aticonfig --remove-pairmode=0
```

And again the listing, then the pairmode is gone.But when I reboot it's back there again. I searched into my xorg.conf but there is nothing in it anymore that is related to dual head (big desktop). The output of:
```
xrandr
```

still gives me the 2560x800.

So any help? Is there anywhere else than in xorg.conf where resolutions are saved?

Thank you. I really hope someone can help me!!!

---

