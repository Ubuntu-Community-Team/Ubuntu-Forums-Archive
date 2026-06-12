---
title: "Tried installing nvidia drivers, then X would not restart"
date: 2006-10-07
forum: Multimedia &amp; Video
---

### Post by roncrump on 2006-10-07
Its Saturday, so I thought I'd play about a bit.

I fancied trying out xgl and compiz/beryl, so the first step would be to install the NVidia drivers. I have a GeForce4 420 Go in a Toshiba Satellite TE2100 laptop, running Ubuntu 6.04.

When Breezy was the standard, I did try this and had a problem with a line down the side of my screen, but thought I'd try again anyway.

So, I installed nividia-glx and nvidia-glx-dev (you never know when you might want to compile something) and ran "sudo nvidia-glx-config enable".

Sadly, my X-server would not re-start. Turned the power off (how do you shut it down nicely when it is hung with no X and no prompt?), and X didn't come up when I rebooted.

Had to edit /etc/X11/xorg.conf and revert to the nv driver.

Any suggestions welcome. I have the 2.6.15-27-386  kernel, and am pretty sure I have the right linux-restricted-modules running (synatpic shows a whole heap installed including linux-restricted-modules-386 and those with above kernel number).

Cheers,
Ron.

---

### Post by tseliot on 2006-10-07
Try Method 1 of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

IF and ONLY IF even that doesn't work you can have a look at point 4 of the Problems Section

---

### Post by roncrump on 2006-10-07
Method 1 worked, thanks.
Ron.

---

