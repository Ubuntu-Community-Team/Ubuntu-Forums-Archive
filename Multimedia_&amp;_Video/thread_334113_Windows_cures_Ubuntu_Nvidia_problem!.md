---
title: "Windows cures Ubuntu Nvidia problem!"
date: 2007-01-08
forum: Multimedia &amp; Video
---

### Post by SteveHil on 2007-01-08
Well...not quite.

I have a dual-boot Win XP/Ubuntu system and have been using Ubuntu more and more lately.  I have recently been having an issue where Ubuntu does not completely boot-up. Just when I would expect to see the login screen, all I get is a completely blank screen. I can do nothing here, ctrl-alt-f1 does nothing. I have to hit the reset button. 

After reading a number of posts here it seems clear that it's a problem with the nvidia driver, (I don't get the Nvidia splash screen when this issues ocurrs) and I will spend some more time reading them. I have a GForce 550MX and loaded the Nvidia driver with Automatix. And this all worked perfectly.

 :confused: But now the strange bit. If I boot into Ubuntu after having first booted the machine into Windows, all is well. But if the first boot of the machine is Ubuntu - then I get the blank-screen-of-death. 

I have no idea how to diagnose this problem, to my unskilled eyes the Xorg.conf looks ok:

---

### Post by scrooge_74 on 2007-01-08
If you change the driver from "nvidia" to "nv" you should go back to the open source drivers (with no 3D)  until a solution can be found.

Since I am no expert on the subject probably someone will come along and give a solution for you and maybe I will learn something new today :D

---

### Post by SteveHil on 2007-01-11
Scrooge, thanks.
Changing to nv does circumvent the issue.

It's very strange though, with nvidia I get a Blank screen if I boot into Ubuntu first. But it's all magically OK if I have previously booted into windows.

I've attached the xorg.0.log file from a failing boot. I can't see anything wrong with the Nvidia load section. Baffled.

---

### Post by scrooge_74 on 2007-01-11
Try checking the [guide for Nvidia drivers]("http://albertomilone.com/latestrepo.html"), maybe you miss a step somewhere, I myself had some troubles setting it up, I even installed the wrong set a couple of times

---

### Post by medley on 2007-01-13
> **SteveHil said:**
> Scrooge, thanks.
Changing to nv does circumvent the issue.

It's very strange though, with nvidia I get a Blank screen if I boot into Ubuntu first. But it's all magically OK if I have previously booted into windows.

I've attached the xorg.0.log file from a failing boot. I can't see anything wrong with the Nvidia load section. Baffled.

Steve, I was wrestling with NVidia driver woes for a week until I found tseliot's envy utility. Go to his website ([www.albertomilone.com)](www.albertomilone.com)), to his project area and get it. D/L it to your desktop, or wherever you save your stuff, run the file (i use kde, so i right clicked and used the package installer). After it's installed, ctrl-alt-f1 to kill off X. If you only get a blank screen with a blinking cursor, you can press that key combo again to get a prompt. Login. Type sudo envy, select 1 and watch the magic begin. I had some serious dependancy problems that no one could help me with. It fixed all that up, downloaded the latest driver from his repository, configured X and voila.

Good luck. I know these kinds of things can be maddening.

Phil

---

### Post by SteveHil on 2007-01-15
Thanks Medley.
Envy certainly did some impressive looking things. I used it uninstall the drivers first then re-installed it. Had a few problems because I needed to install some build-tools. But I kinda get the same problem: everything works perfectly as long as I boot into Windows XP first. If I don't, then what should be the login screen is unreadable: the driver is obviously messing up the resolution/colour depth/synch in some way.

I then unistalled the driver with Envy and tried the latest version of Automatix. That also gives me a driver that works perfectly as long as I boot into Windows first.

So, I'm beginning to think I have a hardware problem. Somehow Windows is resetting something in the physical card or Bios that the Ubuntu driver can't do.

There must be a logfile somewhere that shows what is happening, but I don't know where to look.

---

### Post by Trab on 2007-01-16
yes, the bios seems to me to possibly be a cause of this problem (how else could windows somehow "magically" effect ubuntu?). if you're feeling brave, i would suggest reflashing, or resetting your bios (mine has an "optimal" option which i use, then set the thing i need to set). also it would be intersting to see how a liveCD would work in your situation. it could help cut down the problem.
personally one of the few things i very much dislike about ubuntu is the nvidia driver issue. i dont blame them though, and i prefer to know something is wrong and trouble shoot it than get a BSoD, but urgh, trying to get gaming working on Ubuntu can be a PAIN!.

cheers,
Trab

---

