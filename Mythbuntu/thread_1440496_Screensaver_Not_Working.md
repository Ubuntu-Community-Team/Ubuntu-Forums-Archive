---
title: "Screensaver Not Working"
date: 2010-03-27
forum: Mythbuntu
---

### Post by tracyandskye on 2010-03-27
In Applications > Settings > Screensaver, I set to activate after idle for 1 minute.  The screensaver I choose shows OK & the preview works, but it never comes on.

I have loaded Gnome on this machine as well (I'm not using it) and if I switch to a Gnome session the screensaver works properly.

---

### Post by pu15e on 2010-03-27
It's xscreensaver that doesn't work. Switch to gnome-screensaver - it's going to become the default anyways ;-)

Cheers,
 Mattt.

---

### Post by tracyandskye on 2010-03-27
When I look in Synaptic, xscreensaver is not installed & gnome-screensaver is, though I did see xscreensaver-gl & xscreensaver-data installed.

---

### Post by williammanda on 2010-03-28
> **tracyandskye said:**
> When I look in Synaptic, xscreensaver is not installed & gnome-screensaver is, though I did see xscreensaver-gl & xscreensaver-data installed.

Did you get this issue resolved? I have the same issue.

---

### Post by superm1 on 2010-03-28
> **tracyandskye said:**
> In Applications > Settings > Screensaver, I set to activate after idle for 1 minute.  The screensaver I choose shows OK & the preview works, but it never comes on.

I have loaded Gnome on this machine as well (I'm not using it) and if I switch to a Gnome session the screensaver works properly.

During the 9.10 development cycle the gnome-screensaver guys changed the API they use to detect an inactive sesssion to something that only works on gnome.  We didn't get wind of this until too late, so the screensaver doesn't work for 9.10.

For 10.04, we started installing xscreensaver instead, which still works with XFCE.

---

### Post by Bluberri on 2010-03-28
> **superm1 said:**
> During the 9.10 development cycle the gnome-screensaver guys changed the API they use to detect an inactive sesssion to something that only works on gnome.  We didn't get wind of this until too late, so the screensaver doesn't work for 9.10.

For 10.04, we started installing xscreensaver instead, which still works with XFCE.

Ok, so the resolution is to remove gnome-screensaver completely?

FYI, I am running the netbook edition of 10.04 and have the same issue.

---

### Post by superm1 on 2010-03-28
If you are running a gnome environment (such as UNE), you should continue to use gnome-screensaver generally.  I think there is a different bug about it not working there though too.

---

### Post by williammanda on 2010-03-28
So there is no screensaver possibility using mythbuntu 9.10?

---

### Post by tracyandskye on 2010-03-28
Yes, my question also.

---

### Post by tracyandskye on 2010-03-28
Yes, my question also.  I really want to have the picture slideshow on our TV.

---

### Post by pu15e on 2010-03-28
Oops. My bad - when posting in the early AM hours, I really should double-check the subject matter...

As stated, gnome-screensaver is what fails to work. xscreensaver does. We run it on a pair of 9.10 Mythbuntu boxes to run a photo slideshow during idle times (better than a static menu in case the connected TV has been left on).

Cheers,
 Mattt.

---

### Post by tracyandskye on 2010-03-29
OK so I assume I want to remove gnome-screensaver & install xscreensaver.  But when I select removal for gnome-screensaver in Synaptic, it says it will remove mythbuntu-desktop.

I can try just installing xscreensaver but I don't know if having both installed will mess anything up.

---

### Post by Bucky Ball on 2011-06-22
Get anywhere with this? Having same issue in 10.04 upgrade.

---

### Post by fullmoonguru on 2011-06-22
Can't remember.  I switched to Ubuntu 10.04 server & loaded myth on it long ago.  No problems.

---

### Post by Bucky Ball on 2011-06-22
Cheers. Odd. Xscreensaver is not installed but that pops up now after about 10 minutes rather than the gnome screensaver which is set to go off after 1 minute. Seems to be ignoring that completely now after my tweakings.

---

