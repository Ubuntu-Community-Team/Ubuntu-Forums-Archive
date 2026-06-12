---
title: "Is Network Manager required for MythTV to run or only for it to install?"
date: 2008-03-03
forum: Multimedia &amp; Video
---

### Post by DasCrushinator on 2008-03-03
I use Wicd, but would like to install MythTV (frontend and backend on an Ubuntu (GNOME) desktop.  When I went to install it, it wanted to uninstall Wicd, and reinstall Network Manager.  Does it just need it for installation or to run as well?

Can I install MythTV with Network Manager and once MythTV is installed, uninstall network manager again and reinstall Wicd?

---

### Post by OffAxis on 2008-03-03
I believe you can...but have you looked into mythbuntu at all?
The installation and configuration of it is significantly easier than a standalone mythtv IMO.

[www.mythbuntu.org](www.mythbuntu.org)

There's a meta-package in the repos that (I believe) installs everything you need (I've only installed it off the liveCD, so I'm not sure about adding the package later).

```
sudo apt-get install mythbuntu-desktop
```

There are a number of additions to this version that a regular mythtv install doesn't have; scripts that automate a number of tasks, like remote control setup.
If you're installing mythtv for the first time I'd definitely start with it.

---

### Post by DasCrushinator on 2008-03-03
> **OffAxis said:**
> I believe you can...but have you looked into mythbuntu at all?
The installation and configuration of it is significantly easier than a standalone mythtv IMO.

[www.mythbuntu.org](www.mythbuntu.org)

There's a meta-package in the repos that (I believe) installs everything you need (I've only installed it off the liveCD, so I'm not sure about adding the package later).

```
sudo apt-get install mythbuntu-desktop
```

There are a number of additions to this version that a regular mythtv install doesn't have; scripts that automate a number of tasks, like remote control setup.
If you're installing mythtv for the first time I'd definitely start with it.

Yes, I have looked at Mythbuntu, not really anything I need and would like to keep my current install.  I have used MythTV before, but it was in a previous install before I started using Wicd.

I think I might just use my old PC as a MythTV box.

Thanks!

---

