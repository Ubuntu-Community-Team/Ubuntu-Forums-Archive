---
title: "taskbar Visible"
date: 2012-02-16
forum: Mythbuntu
---

### Post by bensuffolk on 2012-02-16
Suddenly the task bar is always visible over the top of mythfrontend. I find that if I right click on the mythfrontend in the task bar, I can select always on top, which fixes the problem, but I need to do it every time I start mythfrontend.

Is there a fix?

I did find this link [http://askubuntu.com/questions/75150/taskbars-unity-are-visible-in-the-mythtv-frontend-even-when-the-frontend-is-full]("http://askubuntu.com/questions/75150/taskbars-unity-are-visible-in-the-mythtv-frontend-even-when-the-frontend-is-full"). It talks about installing compizconfig-settings-manager and selecting the unity plugin. I installed it, but there was no unity plugin option when I ran it, so I was unable to set the transparency option.

The interesting thing is it was all working fine, then I installed the kernel sources to try and fix the ati remote control, and after a reboot with that is when it started. It could be complete coincidence though. I tried disabling that new kernel module and it made no difference.

Regards

Ben

---

### Post by bensuffolk on 2012-02-16
Setting it to auto hide seems to do the trick, although it does leave a 1 pixel bar but that's not noticeable from the sofa!

---

### Post by goffa on 2012-02-16
> **bensuffolk said:**
> Suddenly the task bar is always visible over the top of mythfrontend. 

did you change anything in mythtv frontend settings? i'm not in front of my box right now but somewhere in the frontend settings, probably under general or display, there is an option to run in window mode. Untick this if it is ticked.

---

### Post by bensuffolk on 2012-02-17
> **goffa said:**
> did you change anything in mythtv frontend settings? i'm not in front of my box right now but somewhere in the frontend settings, probably under general or display, there is an option to run in window mode. Untick this if it is ticked.

I went to bed with it working, didn't turn the TV on in the morning, and then from work VPNed into the box and did the updates for the remote, rebooted it and then when I got him and turned on the TV I noticed it.

I had a look and the setting I think you are referring to is about a bordered window, which is turned off.

---

