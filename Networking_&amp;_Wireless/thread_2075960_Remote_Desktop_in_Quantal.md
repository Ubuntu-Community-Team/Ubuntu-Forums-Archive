---
title: "Remote Desktop in Quantal"
date: 2012-10-25
forum: Networking &amp; Wireless
---

### Post by nwngeek212 on 2012-10-25
Now that FreeNX is no longer supported under 12.10, what are other alternatives I can use for remote desktop control? I don't need to use VNC, I can use anything that's available (and free :D )

Thanks!

---

### Post by QIII on 2012-10-25
Something I never got around to testing on QQ is NoMachine NX.  Give it a try.  Version 3.5 is good, but audio just doesn't cut it.

But I think you may have a problem trying to NX into a machine running Unity because there is no 2D any more.

---

### Post by relol on 2012-10-26
Hi!
I'm facing the same but i'm workarounding this by using lxde for remote connections. You just have to specify to execute lxsession on your nx client. For me it's enough :P
sorry for my english :P
Cheers

---

### Post by Zoide7777 on 2012-11-07
Is anyone having a problem with NX + 12.10 where the text is invisible?

---

### Post by ahoro on 2012-12-28
> **Zoide7777 said:**
> Is anyone having a problem with NX + 12.10 where the text is invisible?

yes - it affects me too - but only on reconnect.
If I start fresh session fonts are fine and nx works like charm.

there are some suggestions about  disabling Render Extension in nomachine client:
   [http://askubuntu.com/questions/214580/nx-client-win-fonts-not-rendering-after-ubuntu-upgrade](http://askubuntu.com/questions/214580/nx-client-win-fonts-not-rendering-after-ubuntu-upgrade)
   [http://ubuntuforums.org/showthread.php?p=12345996#post12345996](http://ubuntuforums.org/showthread.php?p=12345996#post12345996)
but is does not work for me

some people recommend downgrading libcairo (but it is such fundamental package that it seems risky):
     [http://askubuntu.com/questions/198790/nomachine-nx-text-missing-on-all-gtk-interface-unity-and-gnome-classic](http://askubuntu.com/questions/198790/nomachine-nx-text-missing-on-all-gtk-interface-unity-and-gnome-classic)

here are links to some semi-successful attempts that other people tried:
    [http://community.spiceworks.com/topic/272414-nx-issues-with-12-10](http://community.spiceworks.com/topic/272414-nx-issues-with-12-10)
and
[https://bbs.archlinux.org/viewtopic.php?id=141444](https://bbs.archlinux.org/viewtopic.php?id=141444)


Does anybody have a better fix?

---

