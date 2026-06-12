---
title: "Compiz: ATI FireGL 9000 works, but right side does not refresh background..."
date: 2007-07-20
forum: Multimedia &amp; Video
---

### Post by blazko on 2007-07-20
Hello all,

First: ja, I used the search function and googled around also, but I have not found anyone who has that problem.

Okay, I have an IBM Thinkpad R50 with an ATI Mobility Radeon R250 FireGL 9000 (do not know the exact name). When I used the initial X.org driver that came with Feisty installation, compiz worked out of the box.

However, when using the native display resolution of 1440x1050, the right side of the desktop did not draw the background (so, floating windows caused blurry traces where the wallpaper should be). This even remains when killing X - I see windows of the previous session...
Disabling Compiz/GL, everything works just fine.
Also, the GNOME panels only cover the left side of the screen. Any windows however can utilise the entire screen.
When using other resolutions, everything just works okay.

I tried to install the original ATI sdriver but learned that for this card I have to use 8.28 driver which cannot run on Feisty unless you downgrade X.org from 7.2 to 7.1 which I am definetely not going to to.

Does anyone have had similar experiences and got a workaround? Which driver I am using does not matter to me as long basic OpenGL is working and desktop does not render artefacts...

It is like X knows my screen resolution but Compiz does not and limits desktop size (in regards of effects) to maybe 1152 pixels in width).

Thanks+Regards,
Timo

If there were Thinkpads with nVidia, I would have bought one... :-)

---

### Post by Pathfinder_ on 2007-07-20
I had a similar problem and ot solve it you have to change the depth from 24 to 16 in your xorg.conf

---

### Post by blazko on 2007-07-21
Hello pathfinder,

Thanks for your reply! I will try that - maybe it has to do with low memory of 32megs.
I reactivated the "radeon" driver, but I still have to find out what GL libs to use. I used envy etc. and now have no idea how to get back to feisty's initial configuration ;-(
glxinfo tells me I have "SGI", so I reonsta;;ed mesa, but somehow they are not linked yet. I will write back if I had success.


Thanks and regards,
TImo

---

### Post by blazko on 2007-07-21
Rehi,

So, problem solved. A had to re-install xorg-driver-fglrx which repaired a libGL location. That is why a prior installation of libgl1-mesa-dri/libgl1-mesa-glx failed (symlink).
Otherwise, I followed the steps in this HOWTO: [http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon")
regarding the ATI driver parts.

So, thanks for the colour depth tip! After nine years of nVidia I never thought I had to revert to 16 bits ;-) Shame that no IBM thinkpad w/ nVidia was available...

:guitar:

THANK YOU!!!!
Timo

---

### Post by Pathfinder_ on 2007-07-21
always glad to help :)

---

### Post by emid on 2007-08-03
> **blazko said:**
> Rehi,

So, problem solved. A had to re-install xorg-driver-fglrx which repaired a libGL location. That is why a prior installation of libgl1-mesa-dri/libgl1-mesa-glx failed (symlink).
Otherwise, I followed the steps in this HOWTO: [http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon")
regarding the ATI driver parts.

So, thanks for the colour depth tip! After nine years of nVidia I never thought I had to revert to 16 bits ;-) Shame that no IBM thinkpad w/ nVidia was available...

:guitar:

THANK YOU!!!!
Timo

So did you end up having to revert to 16 bits?  That's what I'm currently doing and I would love to be able to put the depth back to 24.  I used to run it in 24 in edgy with no problems,:(

---

