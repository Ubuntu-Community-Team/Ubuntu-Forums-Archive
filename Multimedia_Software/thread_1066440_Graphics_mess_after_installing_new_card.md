---
title: "Graphics mess after installing new card"
date: 2009-02-10
forum: Multimedia Software
---

### Post by 5circles on 2009-02-10
I hope someone can help me with some instructions (hopefully short of reinstalling as I then I'd have to contend with reinstalling Apps).

I'm running Hardy on an HP Pavilion.  I was using the onboard video without any problem, with the monitor (wide screen LG2252TQ connected via its second - VGA - input).

I installed an NVidia 9400GT.  I don't recall exactly what I did as did the install several weeks ago, and regrettably didn't take good notes.  But I know that I installed the nvidia drivers and configuration tool and that the new card was working at one time.

But now the card and monitor doesn't seem to get detected.  I was too busy with other things, and mostly using the system to run local LAN applications, so I didn't attend to it right away.  I've just spent some time trying to figure out the issues and got nowhere.  The resolution seems to be 800x600, which means that I can't even select and use graphical tools using the mouse - so it is hard to change the resolution on the fly with System | Preferences | Screen Resolution.  I was able at one point to get to some kind of window that showed resolution, monitor, and card settings, but nothing seemed to work when I tried to change it.

I ran dpkg-reconfigure xserver-xorg, but wasn't presented with any options for screen resolution.  The xorg.conf file didn't seem to have complete information in, that's probably why.

I've gone through quite a few forum postings, but nothing seems to make any difference.

I finally gave up and changed the graphics default back to the onboard video.  Now everything works fine again.  (Resolution is OK, and I generally don't worry about performance, so I'm asking myself why I bothered with the card in the first place).

Any ideas greatly appreciated.

Thanks
Mike

---

