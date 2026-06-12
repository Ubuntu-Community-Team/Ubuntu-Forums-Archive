---
title: "mythtv-setup just hangs"
date: 2007-02-07
forum: Multimedia &amp; Video
---

### Post by kperrier on 2007-02-07
I have just installed mythtv from this guide: [https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend](https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend)

Everything appears to be working ok, except when I try to run mythtv-setup.  When I run the command I get this output:

> 2007-02-06 23:12:53.134 Using runtime prefix = /usr
2007-02-06 23:12:53.158 DPMS is active.
2007-02-06 23:12:53.224 New DB connection, total: 1
2007-02-06 23:12:53.242 Connected to database 'mythconverg' at host: localhost
2007-02-06 23:12:53.247 Total desktop dim: 800x600, with 1 screen[s].
2007-02-06 23:12:53.254 Using screen 0, 800x600 at 0,0
2007-02-06 23:12:53.287 Current Schema Version: 1160
2007-02-06 23:12:53.318 Total desktop dim: 800x600, with 1 screen[s].
2007-02-06 23:12:53.321 Using screen 0, 800x600 at 0,0
2007-02-06 23:12:53.326 Switching to square mode (G.A.N.T.)
libGL warning: 3D driver claims to not support visual 0x4b
2007-02-06 23:12:53.458 Using the Qt painter
and no gui opens up.  I have tried this as my auto-login user and as the mythtv user, with similar responses.  

I did have one other error but I saw a post about wacom entries in the xorg.conf file.  I commented those out, restarted X and now I do not get those.  For what its worth, my PC is on old Dell Dimension with with a PVR-350 capture card. 

Thanks for the help!

---

### Post by barney_1 on 2007-02-07
I don't have a solution for you, but you should try to set your resolution higher.  For some reason I can't get my mythtv frontend to start when I have the resolution set to 800x600.

---

### Post by kperrier on 2007-02-07
Yea.  I change my display resolution to 1024x768 I now starting mythtv-setup causes X to crash and restart. :( 

Any other ideas?

---

### Post by kperrier on 2007-02-07
Update.

Instead of using the mga driver for my Matrox card, I reconfigured X to use the vesa driver at 1024x768.

It appears to be working! woohoo!

---

### Post by realflash on 2007-04-14
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/edgy-backports/+bug/58721](https://bugs.launchpad.net/edgy-backports/+bug/58721) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This is due to a bug in the mga driver in edgy. Go to the URL above and install the deb linked there. Then it all works OK.

If you change to the vesa driver you end up with choppy video later on.

---

### Post by kperrier on 2007-04-16
Thanks for the thread necro!

I'll check this out.  Yeah, I can't watch video on my machine, but I though that was because I was lacking in the processor, not because of the video driver.

---

