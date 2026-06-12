---
title: "External monitor with different resolution"
date: 2007-05-02
forum: Multimedia &amp; Video
---

### Post by lads on 2007-05-02
Hi everyone here's my problem:

I have a laptop with an internal monitor with 1024x780 res and an intel integrated graphics card 82852/855GM. At work I use a bigger external LCD monitor with 1280x1024 res.

On XP I can simply use the Fn key to toggle between 3 modes: both on, just internal on, just external on. With only the external monitor on I can get 1280x1024 automatically. With Ubuntu the Fn key toggles properly between the three modes, but with solely the external monitor on the resolution is kept at 1024x780.

At first I thought that the higher res was simply absent from xorg.conf and edit it to add a &#8220;1280x1024&#8221; line. No results.

Then I tried to create a new xorg.conf with dpkg. Although the new file had the &#8220;1280x1024&#8221; the external monitor kept getting a lower resolution.

I then tried Xinerama, which is announced has functioning with different resolution monitors. I followed all the steps found here: [http://ubuntuforums.org/showthread.php?p=1773624](http://ubuntuforums.org/showthread.php?p=1773624) . With a setting like this X simply won't start.

Can anyone help? I just want my external monitor working at the right res, with or without the internal one on that's not important. I'm sorry if this is a repost.

---

### Post by veloce on 2007-05-03
You need the package 915resolution. That will help with your resolution issues.  

Don't try for dual head unless you really want it.  It is not straight forward.  You will need to edit your xorg.conf file (repeatedly) to get it working.

---

### Post by focus1974 on 2007-05-03
SAme here.
I've got a laptop with an internal screen resolutin of 1024x768. THIs laptop is connected to an external LCD Monitor with a resolution of 1280x1024.  Again, it's a similar INtel GM CHipset. 

NOw, the question is why is there so many people with similar requirements but there is no easy way to do the switching and different resolution setting? 

UBuntu really looks good but a pity that the most critical aspect that matters to a lot of the mobile warriors out there or even home users are ignored.

---

### Post by raober on 2007-05-03
Bumping this because I think have a similar problem and thought explaining it another way could help.

I have a Dell Inspiron 9300 with a 1920x1200 panel.  I also have a Dell 1905FP 1280x1024 external monitor hooked up to the DVI port.

What I am looking for is a xorg.conf setup that will be smart enough to use the proper settings when the external monitor (1280x1024, non-widescreen) is connected, and to use settings for the widescreen laptop display (1920x1200, widescreen) when the external monitor is not connected.  I do NOT want dual head per se...I only need to use one screen at a time.  I just want X to be smart enough to detect the monitor in use and apply the proper settings.  Is this possible?  I've looked at a lot of things...many mention dual head setups, but I'm not sure I've found anything referring to the functionality I want.

Thanks!

---

