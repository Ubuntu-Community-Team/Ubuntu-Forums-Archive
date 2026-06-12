---
title: "2nd monitor broke with NVidia 302.17 on update."
date: 2012-07-03
forum: Multimedia Software
---

### Post by SimonLyall on 2012-07-03
I'm running Ubuntu 10.04 and have 2 monitors.

Yesterday I upgraded to the 302.17 nVidia packages from ubuntu-x-swat ppa for Lucid.

However which my second screen to still there and shows the backgrounds, desktop and I can drag windows other things can't see it.

I right click the desktop and the menu shows up in the main screen. Also Preferences->Monitors only shows one screen (with one screen's resolution). I regenerated my xorg.conf , restarted X etc but no luck. 

Any help would be appreciated.

My xorg.conf:

[http://paste.ubuntu.com/1072668/](http://paste.ubuntu.com/1072668/)

My /var/log/Xorg.0.log

[http://paste.ubuntu.com/1072676/](http://paste.ubuntu.com/1072676/)

---

### Post by BicyclerBoy on 2012-07-03
AFIAU nVidia 30x. drivers have made big changes to twinview, xinerama & overscan compensation.

I believe the new xinerama now works with openGL & is on by default & deprecates twinview(?) & separate X screens.

The new overscan comp by viewport appears more flexible but there is no GUI interface (yet).

I have pinned the 295 driver on a lucid HTPC box so not to have to reinvent the wheel.

Did you re-gen the xorg.conf by using nvidia-settings ?
{Edit: can see in log that you used 302 nvidia-settings}
I have never had to disable composite to have tear-free desktop/video etc with 10.04 or 12.04..

GnomeMenu-->preferences-->monitors has never worked with the proprietary drivers..

---

