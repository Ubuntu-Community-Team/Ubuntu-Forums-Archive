---
title: "Please Assist With Monitor Configuration"
date: 2008-06-28
forum: Multimedia Software
---

### Post by ttoolin on 2008-06-28
Hi, folks-

I am a newcomer to Ubuntu, and I'm using 8.04 on an AMD Athlon machine.  I am using an S3-Virge video card with a HP pavillion v50 monitor.  When I installed ubuntu, the OS opted to use a generic low resolution mode, which I accepted on the basis that I would fix it after installation.  I fought other battles for a few days (like trying to network with my vista machine, a battle I'm still losing), and revisited the video problem.

I ran the following in the terminal:

     sudo displayconfig-gtk

and I set (and the system retained) my video card type.  My monitor is not specifically listed as an option, but I tried other HP monitor types that worked for me in some windows configurations.  When I rebooted, I got a warning screen saying that I can only run in low resolution mode, and I found that I was reset from the HP monitor back to a low resolution plug and play monitor.

Okay . . . so I used a generic driver that seemed to work well with the "test" button, and clicked "OK".  When I rebooted - same thing:  low resolution plug and play monitor.

Okay , , , I go into my computer's boot-up options screen, and set the toggle for "O/S detects plug and play" to the 'NO' state.  I reboot,  Same thing again:  low resolution plug and play monitor.

*I found that if I saved the revised monitor configuration three times in succession, without exiting the configuration utility, the new configuration stuck.*

terry

---

