---
title: "Tearing everywhere (ATI)"
date: 2009-12-16
forum: Multimedia Software
---

### Post by hachre on 2009-12-16
Hi Guys,

I just installed Ubuntu 9.10 after a long break from Desktop-Linux and I'm quite happy with it however there is one huge problem: I have video tearing everywhere.

I installed the fglrx drivers Ubuntu suggested right after the installation.
With or without the drivers, with or without Compiz, there's always tearing. I can see it by moving windows sideways.

When Compiz is on, it's especially apparent when menus are fading in for example.

Of course the same issue exists full scale in movies. Totem, mplayer, vlc all have the same problem. I found out that I can set VSync to forced on in the ATI Control Panel and when switching the Movie Players to gl that I can get rid of the tearing in Full Screen (but only then).

GL, however means that I can not use any context menus or any on screen controls those players provide, so it's not a perfect solution.

Also this doesn't solve the tearing I see when I move windows, open menus, playback flash stuff, etc.

Is there any solution for this, besides buy NVIDIA? I hate NVIDIA ever since they managed to put manufacturing defects into 90% of their 8xxx cards both for desktops and laptops and then even lied about it to cover it up. I had several laptops fail because of that personally and I'm sick of them.

If there is I would appreciate being pointed in the right direction,
thanks
Hachre

---

### Post by greg963 on 2009-12-16
fglrx is really bad about tearing, 
I have used nvidia exclusively since I about lost my mind trying to make ati work when building my first mythtv box in 2002. Recently I upgraded my mythtv hardware so I could run hulu desktop at 1080p (flash is a cpu hog at 1080p fullscreen). I decided to give radeon another shot since I had heard their linux support had improved and they seemed to have more inexpensive hdmi options.  After trying the fireGL driver I switched to the radeonhd and I have been using it with some success. I have minimal tearing using hulu desktop at 1080p, the tearing is still annoying but it is watchable and I don't notice any tearing in my 720p hd recordings. I would definitely still recommend nvidia but I am impressed with the radeonhd driver.

[https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)

---

### Post by hachre on 2009-12-16
> **greg963 said:**
> fglrx is really bad about tearing, 
I have used nvidia exclusively since I about lost my mind trying to make ati work when building my first mythtv box in 2002. Recently I upgraded my mythtv hardware so I could run hulu desktop at 1080p (flash is a cpu hog at 1080p fullscreen). I decided to give radeon another shot since I had heard their linux support had improved and they seemed to have more inexpensive hdmi options.  After trying the fireGL driver I switched to the radeonhd and I have been using it with some success. I have minimal tearing using hulu desktop at 1080p, the tearing is still annoying but it is watchable and I don't notice any tearing in my 720p hd recordings. I would definitely still recommend nvidia but I am impressed with the radeonhd driver.

[https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)

Thanks, I'm also running radeonhd now; it indeed seems to do a bit better. However the GL workaround is completely gone now. 

Also my card seems to have its fan on a much louder setting than before...

Hopefully the RadeonHD driver will improve soon :)

---

