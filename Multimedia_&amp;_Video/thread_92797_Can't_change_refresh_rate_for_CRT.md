---
title: "Can't change refresh rate for CRT"
date: 2005-11-20
forum: Multimedia &amp; Video
---

### Post by RonDeen on 2005-11-20
Hi list,
Installed Breezy on a vanilla PC detect all hardware just fine. I do have a rather absurdly high resolution of 1600x1200 and 60 Hz.
Now I can change the resolution but not the refresh rate (60Hz or 56 for some other resolutions) under Preferences/Resolution. This is not workable, it gives me headaches :-(
Now I'm a Mandrake user so I probably am looking in the wrong places. Where do you configure this stuff?
Another silly one: what is the "root" password? I don't remember this was asked during install. I think I need it for some system settings.

Thanks in advance

Ron

:( :(

---

### Post by aysiu on 2005-11-20
Ordinarily, you'd go to System > Preferences > Screen Resolution, but if that doesn't work, try [this](http://ubuntuforums.org/showpost.php?p=129379&postcount=21).

Oh, and read this, too: [http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

---

### Post by RonDeen on 2005-11-20
Thanks for the fast reply.
Though the "root" thingy was very helpfull (new for me, not sure if I like it thought)

I do not feel good about modding files on the system. Never had to do this for video stuff in a very long time (Running Linux for about 4 years now) Breezy is NOT going to get me started with that now.

There must be a more elegant way to do this I'm sure

BTW did a re-install just now to make sure and results are the same. The videoa card is a plain GForce MX440.

Ron

---

### Post by aysiu on 2005-11-20
[QUOTE=RonDeen]
I do not feel good about modding files on the system. Never had to do this for video stuff in a very long time (Running Linux for about 4 years now) Breezy is NOT going to get me started with that now.[/QUOTE] It's not a big deal if you back up your work. A simple ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
``` takes care of all your worries. If you modify xorg.conf and screw things up, then all you do is ```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
``` and you have your old xorg.conf back the way it was before.

Ubuntu is elegant for use, but it's still quite rough around the edges for setup.

---

### Post by RonDeen on 2005-11-21
I know what a "cp" does, I just don't like what comes after that. Never liked Xconfig files a lot.
Last time I had to do that was during the days of RedHat 4.2. That file has a different layout if I remember. After that there was a change from XFree 3.x to 4.x.
I will check the config files and report my findings.

Regards,
Ron

---

