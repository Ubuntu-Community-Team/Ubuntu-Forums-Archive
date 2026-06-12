---
title: "Please help me change graphics drivers/modules"
date: 2010-05-15
forum: Multimedia Software
---

### Post by timkoop on 2010-05-15
I'm trying to change my graphics driver, a.k.a. "module".  Can someone please help me?

In Ubuntu 9.04, my graphics works great!  In 10.04, not so much.  So I want to make 10.04 as slick as 9.04.  These are the modules that get loaded in 9.04:

[FONT="Courier New"]grep "LoadModule" /var/log/Xorg.0.log
(II) LoadModule: "extmod"
(II) LoadModule: "dbe"
(II) LoadModule: "glx"
(II) LoadModule: "record"
(II) LoadModule: "dri"
(II) LoadModule: "dri2"
(II) LoadModule: "radeon"
(II) LoadModule: "vgahw"
(II) LoadModule: "int10"
(II) LoadModule: "ddc"
(II) LoadModule: "i2c"
(II) LoadModule: "fb"
(II) LoadModule: "ramdac"
(II) LoadModule: "exa"
(II) LoadModule: "theatre_detect"
(II) LoadModule: "evdev"
[/FONT]


And these are the modules that get loaded in 10.04:

[FONT="Courier New"]grep "LoadModule" var/log/Xorg.0.log
(II) LoadModule: "extmod"
(II) LoadModule: "dbe"
(II) LoadModule: "glx"
(II) LoadModule: "record"
(II) LoadModule: "dri"
(II) LoadModule: "dri2"
(II) LoadModule: "ati"
(II) LoadModule: "radeon"
(II) LoadModule: "vesa"
(II) LoadModule: "fbdev"
(II) LoadModule: "fbdevhw"
(II) LoadModule: "fb"
(II) LoadModule: "ramdac"
(II) LoadModule: "exa"
(II) LoadModule: "evdev"[/FONT]

I guess I need to unload some stuff on 10.04 and load instead some stuff that was in 9.04.  Can someone please tell me how?

And a line from my lspci says this:

[FONT="Courier New"]01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE][/FONT]

Thank you very much!

--
Tim

---

### Post by lidex on 2010-05-16
For binary driver:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

Open Source:
[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by timkoop on 2010-05-17
> **lidex said:**
> For binary driver:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

Open Source:
[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

Thanks for this reply, lidex.  I looked over these pages.

However, from what I can see the open source driver called "radeon" fully supports my card.  And my 9.04 installation is already using it and not fglrx, so I may as well use radeon in 10.04 too.  I think I am using radeon in both my installations, so why is 10.04 so much slower?

Maybe it has something to with "theatre_detect" or "int10", whatever that stuff is.

Does anybody know what's going on?

Thanks.

--
Tim

---

### Post by timkoop on 2010-05-19
Bump.

Anyone have a clue why 10.04 is slower than 9.04 with the same video driver?

---

### Post by timkoop on 2010-05-23
I think I've found an answer, and I'll post it here in case anyone else wants it.

I noticed that in 10.04, there were a few things loading that I might not want.  So I blacklisted them.  I created a file "/etc/modprobe.d" called "blacklist.mylist.conf".  It contains this:

```
# I'm guessing that we don't need the ati module or radeon.
# Let's try to not load them.
blacklist ati
blacklist radeon
```

Then I restarted.

That seems to fix the problem.

---

