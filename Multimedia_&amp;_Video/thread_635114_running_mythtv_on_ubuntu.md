---
title: "running mythtv on ubuntu"
date: 2007-12-08
forum: Multimedia &amp; Video
---

### Post by yinglcs2 on 2007-12-08
Hi,

I am using ubuntu 7.10. And I would like to have mythtv installed.
Can you please tell me what do I need to install if I want to run mythtv as a program in my ubuntu environment?  I see screenshot of mythbuntu, it 'takes over ' my current ubuntu desktop. That is NOT what i want to setup.

For example, I want to run mythtv and browser the web (via firefox) at the same time.

Thank you.

---

### Post by srhlefty on 2007-12-09
I recently installed mythtv, and at first I was afraid it was going to 'take over' as well, but that's not the case. 

It did change my login screen to mythbuntu's, and set the default WM to xfce, but both those things are easy to revert back to gdm/gnome.  

You can also run the mythtv frontend in a window instead of fullscreen; somewhere in the many layers of configuration you can set the window size and window position.  I have mine set to 800x600.  You're not allowed to resize the window while it's running, but it can be moved around just like any ordinary window.

I've attached a screenshot showing the behavior that I think you're desiring.

---

### Post by yinglcs2 on 2007-12-09
Hi,

I am trying to setup MythTV with  HauppaugeWinTV- HVR 950 on ubuntu
7.10 by following this article:

[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

During the "Input Connection" configuration, it looks like it can find
a number of channels.

However, when i go to start 'mythtv-frontend', and then go to watch
live tv (I don't have recording yet), ubuntu. 7.10 logs me out  automatically.

But when I use TVTimes in my environment to watch live TV, I see video.

---

### Post by hey_ygbsm on 2008-01-07
I installed Mythbuntu on top of Gutsy and have not yet figured out how to revert back to my standard gnome Ubuntu desktop as srhlefty describes...
> It did change my login screen to mythbuntu's, and set the default WM to xfce, but both those things are easy to revert back to gdm/gnome. 

Could you please share how you did this?

---

### Post by srhlefty on 2008-01-10
> **hey_ygbsm said:**
> I installed Mythbuntu on top of Gutsy and have not yet figured out how to revert back to my standard gnome Ubuntu desktop as srhlefty describes...

Could you please share how you did this?

After I did the installation procedure, and upon restarting, I was left with a login screen with a different background, the mythbuntu default.  I logged in to see what it was going to do, and up popped a normal xfce desktop.  I logged out again, then changed it back to gnome by pressing the 'Sessions' button, selecting Gnome, and selecting Yes when it asks if you want to make that the default session.  

The other way to mess with those settings if you're logged into a Gnome session is:
System->Administration->Login Window
The General tab lets you change which window manager, and the Local tab lets you change the background image, which is just tied into the theme you choose.

If this is different than what happened with your setup, maybe we installed from different methods?

---

