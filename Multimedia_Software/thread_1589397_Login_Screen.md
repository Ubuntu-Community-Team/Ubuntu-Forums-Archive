---
title: "Login Screen"
date: 2010-10-06
forum: Multimedia Software
---

### Post by eanema on 2010-10-06
Hi all,

I have an ATI Radeon 5450 and have been using the proprietary driver downloaded from the web site. It was giving me problems so I decided to use the proprietary provided by ubuntu. It seems to work better but I have one serious problem - the login screen.

When I first turn on the computer and the login screen first appears, it is in extremely low resolution. It doesn't just look funny, its hardly readable. But if you hit enter and type in your password and hit enter again, you will be logged in. 

Once we are logged into gnome, the resolution is changed to the res. selected by System->Preferences->Monitors and allis good again. But if I select logout to switch users, then the monitor says that the input signal is invalid and I can't see any thing. Although I can still hit enter, type my password and then hit enter again to log back in.


Question, can this be fixed some how? I've played around with the xorg.conf file, adding different mode lines, but nothing seemed to have any effect on the behaviour.

---

### Post by Claus7 on 2010-10-06
Hello,

check this out:
[http://n00bsonubuntu.com/content/install-ubuntu-1010-plymouth-theme-ubuntu-1010-maverick-meerkat](http://n00bsonubuntu.com/content/install-ubuntu-1010-plymouth-theme-ubuntu-1010-maverick-meerkat)

just take care that on step:
For this line: GRUB_CMDLINE_LINUX_DEFAULT...

you need to put " at the end.

Hope this helps,
Regards!

---

### Post by eanema on 2010-10-07
excellent, thanks for the reply. I'll give this a try when I get home

---

### Post by eanema on 2010-10-08
Well, I just tried the instructions mentioned above and no luck (although the initial loading screen is much prettier and the boot menu is gone) 

Any other ideas what might be causing this problem? It seems as though Ubuntu is changing the resolution at the beginning and then again after the user loges in, then a second time when the user loges out. 

Thanks

---

