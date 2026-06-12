---
title: "Achieve 1600x1200 w Asus M2NPV-VM (GeForce 6150)"
date: 2007-06-04
forum: Multimedia &amp; Video
---

### Post by counterpoint on 2007-06-04
With a new NEC LCD2170NX (capable of 1600x1200 at 60 Hz) I'm struggling to achieve the full resolution.  Using the on-board graphics of the Asus M2NPV-VM which is GeForce 6150.  Having got into a bit of  mess, did a fresh install of Ubuntu 7.04 on all the stated hardware.  When asked to select resolutions, retained all the high ones.  Then installed the Nvidia driver using package manager (nvidia-glx 1.0.9631).  Nvidia driver is definitely running - shows splash screen of Nvidia logo during boot.

But highest resolution offered by Gnome selector is 1440x1050.  As that is not supported by the NEC monitor, it is actually running at 1280x1024 (same as my old monitor, so not getting value from the upgrade!).  So far as I can tell from reading specifications, 1600x1200 at 60 Hz should be well within the capacity of the hardware.  How do I actually achieve it?

---

### Post by blackened on 2007-06-04
My first suggestion would be to reconfigure the xserver, but leave out the (unsupported) resolutions above your monitor's maximum. Just select 1600x1200, 1280x1024, 800x600, and 640x480.

```
sudo dpkg-reconfigure xserver-xorg
```

Select the nvidia driver and use the "Advanced" mode (accept the defaults after that) later in the monitor section. Might have to resort to adding a modeline into the monitor section of xorg.conf, but try the reconfigure first and see if that helps. After you're finished reconfiguring use

```
sudo /etc/init.d/gdm restart
```
to restart the xserver.

---

### Post by counterpoint on 2007-06-04
Brilliant!  Thanks very much :)

Just for the sake of anyone else who has a similar problem, I'll just add a couple of comments on how it went.

The reconfigure asked a lot of questions about things other than display, and I was not certain of the answers.  So after completing the whole thing, I edited the xorg.conf file, restoring everything from the backup except for the new Device, Monitor and Screen sections.

Restarting X seemed to get me into a mess, maybe I shouldn't have done it from a graphical terminal window, but I don't know any other way.  But rebooting worked fine and the screen resolution option then gave me the 1600x1200 option.  Excellent!

---

### Post by blackened on 2007-06-04
Glad to see it worked for you.

---

