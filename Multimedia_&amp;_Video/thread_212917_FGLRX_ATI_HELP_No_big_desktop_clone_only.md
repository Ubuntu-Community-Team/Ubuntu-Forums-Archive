---
title: "FGLRX ATI HELP No big desktop clone only"
date: 2006-07-10
forum: Multimedia &amp; Video
---

### Post by bpickel on 2006-07-10
I have an Thinkpad Z60m with a ATi x300. I have fglrx working. I have cloned desktops but cannot switch to "Big Desktop" I open fireglcontrol and the change to Big Desktop. When I resart xserver then my changes are ignored and I am still in clone. It will not accept any change. ie Single or anything. I LOVE Ubuntu and will continue to use it. I just wish I could figure this out. Any Ideas?

---

### Post by whatever on 2006-07-10
aticonfig --help

---

### Post by bpickel on 2006-07-10
UPDATE

 I understand the setup. It seems that the issue is that the control app cannot replace the xorg.conf (which is how it makes the change) unless you are logged in as root. I can bypass this by simply saving two files and the manually replacing the file. This works, however it would be nice if it could make the change with the control!. Should I just stay logged in as root? I have changed permissions but, since the file is replaced every time you run the control, any changes are lost. Does anyone have a solution to this. I am new to Linux but already a convert. I find with a little effort there isn't alot you can't do.

---

### Post by Yfrwlf on 2007-04-17
I tried this in Feisty, and when you run fireglcontrol as a normal user of course you do not have permission to modify the xorg.conf file, nor does it prompt you in order to do so.  When you run it as root it says it "uses" xorg.conf, and it does save a backup of the file.  However, upon restart, it still did not give me an expanded desktop.  Clone is pretty useless when you are using dual monitors.  I would say this is a bug with ATI's driver control program, and the Nvidia control program has the same inability to correctly save changes to xorg.conf for me on my other computer.  You may have to tinker around with xorg.conf using any guides you find for setting up dual monitors with an expanded desktop on ATI cards.  Just be sure to make a backup of xorg.conf (using sudo, or logging in as root at a terminal) so that if you make bad changes you can revert back.

---

