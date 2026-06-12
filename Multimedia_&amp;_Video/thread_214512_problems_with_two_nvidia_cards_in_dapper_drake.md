---
title: "problems with two nvidia cards in dapper drake"
date: 2006-07-12
forum: Multimedia &amp; Video
---

### Post by gfxcoder on 2006-07-12
Previously, I had Kubuntu Breezy up and running great.  I have two video cards: AGP GeForce4 MX 460, PCI GeForce4 MX 420, and was using the latest NVidia drivers.

Now, I've installed Dapper (2.6.15-26-386) on a different harddrive (same machine), and I'm having a strange problem.  I followed tseliot's How-To on installing the drivers.  The "nvidia" driver works great for either my AGP card or my PCI card.  However, I cannot use it for both at the same time!  I have to use "nv" for one of them.  If I try to use it on both, I get as far as the login screen, then the computer either hardlocks, the screen blanks but things are still running in the background (ctrl-alt-del beeps and starts the shut-down/restart process), or it will restart the XServer and plop me back at the login.  Although it seems a crapshoot which of the three I'll "win", I tend to get a lot of the third choice.

I've searched a bit on several forums to see if somebody has had a similar problem, but I didn't find anything...

Thanks for the help!

---

### Post by Schluppy on 2006-07-12
[It's a bug in X.org]("https://bugs.freedesktop.org/show_bug.cgi?id=2597"). (unavailable ATM)


I'm having the same problem with two ATI cards. [newb]If I understand correctly X fails to properly detect the secondary card then tries to apply the primary cards settings to the secondary card, which fails.[/newb]

It's quite the showstopper for me. I've been searching daily for more information - fixes, workarounds, etc., but there doesn't appear to be any. I believe, perhaps incorrectly, that our only hope is that it will be addressed in a future release.

---

### Post by thecavemaster on 2008-03-07
I'm having the a very similar problem. I have An AGP Nvidia MX 420 and A PCI Nvidia Geforce 5500 on two Dell M783s's. I can get them both to work using the "nv" driver or the "vesa" driver. I can get them to work one at a time with the "nvidia" driver. I am using both the GUI screen editor and manually editing xorg.conf . I am getting better at the syntax. I rarely crash X anymore. The only X error I ever get it "no screens detected". I now have 23 backup xorg.conf's for different configurations I've tried. Also every time I enable the nvidia drivers in the GUI and select the VGA outs (screen1 and screen1 respectively) It says logout which is normal. When I log back in, every time my MX420 Is set to the S-video out. So every time I open the GUI screen editor my MX 420 is selected on the S-video out or "screen2" no matter how many times I select the VGA out or (screen1) and save the settings or test the settings. The Geforce 5500 usually stays set to screen1 when I tell it to. Thats the closest I've been able to get to my goal of having both monitors work with the proprietary drivers so I can have desktop effects enabled.If anyone knows how to get both cards working with the proprietary drivers and desktop effects or knows where to go to find out as I might not of found the resource yet I would be extremely grateful.

---

### Post by thecavemaster on 2008-03-07
Also I'm using Gutsy 7.10 with all of the Ubuntu studio packages except ubuntustudio-look

---

