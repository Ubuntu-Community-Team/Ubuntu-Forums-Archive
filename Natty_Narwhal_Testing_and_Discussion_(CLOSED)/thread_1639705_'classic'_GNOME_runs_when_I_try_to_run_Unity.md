---
title: "'classic' GNOME runs when I try to run Unity"
date: 2010-12-07
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Dooglus on 2010-12-07
I upgraded from 10.10 to 11.04 recently.  When I log in, I see the choice of "Ubuntu Classic Desktop" and "Ubuntu Desktop Edition".

If I log on as my usual "chris" user, whichever of the above I chose, I always get the old "Classic" desktop (gnome-panels, etc).

If I log on with a new user, I get Unity or Classic, depending on which I ask for, as expected.

I'm guessing that
/usr/share/xsessions/gnome-classic.desktop
and
/usr/share/xsessions/gnome.desktop
define the two choices, but am confused as to how.  They both have
"Exec=gnome-session" in them, and so I don't see how they are meant to start different interfaces, or why they are failing to for my user.

---

### Post by cariboo on 2010-12-07
Try deleting ~/.config/compiz-1, to see if that helps.

---

### Post by Dooglus on 2010-12-07
> **cariboo907 said:**
> Try deleting ~/.config/compiz-1, to see if that helps.

Thanks.  I didn't have anything called that, but I did have a folder ~/.config/compiz/

I deleted it, but nothing changed.

I had previously deleted ~/.compiz too, on advice of some guy on IRC, but that also had no effect.

---

### Post by seeker5528 on 2010-12-08
Assuming what you are seeing is not compiz+gnome panel.

If you created a .xprofile file in your home directory with a line like ```
export WINDOW_MANAGER="/usr/bin/metacity"
```

or use some other trick to set the WINDOW_MANAGER variable, that would do it.

Alternatively if something else is causing it to come up with the classic desktop, setting the WINDOW_MANAGER variable in .xprofile may override it until you can figure out what is going on. 

To try that create a .xprofile file in your home directory with the contents ```
export WINDOW_MANAGER="/usr/bin/compiz"
``` assuming something else isn't causing compiz to fail that should at least get you a desktop with Compiz running whether you choose the default desktop or the classic one. If you don't get any panels after that you may have to comment out the line in .xprofile or rename .xprofile temporarily so you can get back into the normal desktop and run ccsm to enable the Unity extension.

Later, Seeker

---

### Post by lidex on 2010-12-08
I had that issue. Looks like an old config file got carried over from your upgrade. Unfortunately, I can't make any sense out of them. So I did it the hard way:
[http://ubuntuforums.org/showpost.php?p=10192242&postcount=21](http://ubuntuforums.org/showpost.php?p=10192242&postcount=21)

---

### Post by Dooglus on 2010-12-11
> **seeker5528 said:**
> Assuming what you are seeing is not compiz+gnome panel.
Alternatively if something else is causing it to come up with the classic desktop, setting the WINDOW_MANAGER variable in .xprofile may override it until you can figure out what is going on. 

Setting WINDOW_MANAGER in .xprofile didn't make any difference (other than adding an environment variable, of course).

One thing I've noticed is that if I go into the display properties (right click wallpaper, switch to the 'visual effects' tab, and switch from 'none' to 'normal') then Unity appears, but the bottom GNOME panel stays in place showing open windows, trash can, etc.  The next time I log in, it's back on 'none' again.

When Unity does come up, it's all corrupted and ugly, as below.  The bottom GNOME panel is set to autohide, but it is there, honest!


Perhaps this is why the setting doesn't 'stick' and Unity doesn't work without some fiddling?

Installed packages:

```
$ dpkg -l | grep -e '[^a-z]ati[^a-z]' -e fglrx -e radeon
ii  fglrx-modaliases                      2:8.780-0ubuntu3                           Identifiers supported by the ATI graphics driver
ii  libdrm-radeon1                        2.4.22-2ubuntu1                            Userspace interface to radeon-specific kernel DRM services -- runtime
ii  radeontool                            1.6.1-1                                    utility to control ATI Radeon backlight functions on laptops
ii  xserver-xorg-video-ati                1:6.13.2-1ubuntu2                          X.Org X server -- AMD/ATI display driver wrapper
ii  xserver-xorg-video-radeon             1:6.13.2-1ubuntu2                          X.Org X server -- AMD/ATI Radeon display driver
```

Video card:

```
$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
```

---

### Post by Amroozy on 2010-12-12
maybe try to reinstall graphic driver. and reinstall unity..
btw there is a new version of unity.. 3.2.6-0ubuntu1 maybe you try to install it too if you don't have it..
notice "i had to do update many times to have the new unity available in my software center"
good luck trying

---

### Post by MacUntu on 2010-12-12
If you see gnome-panels in Unity, make sure it says:

```
IsRunnableHelper=/bin/true
```

in '/usr/share/gnome-session/sessions/ubuntu.session'.

---

