---
title: "ATI Radeon X300 SE on Gibbon 7.10"
date: 2008-02-06
forum: Multimedia &amp; Video
---

### Post by jaltenburg on 2008-02-06
I've been cruising around the forums looking for a good answer to this question.

I've been trying to install Ubuntu and get the desktop effects working, and keep bricking my machine.

When I install Ubuntu, I am allowed to choose a popup that installs the restricted ATI drivers, but this bricks my machine after the required reboot, it does not come back up at all.

I'm running a Dell Dimension 5100

I've tried quite a few things, and don't really feel like jumping through hoops to get this to work.  I'm mainly trying to get the graphics working as my recent 7.4 install was working flawlessly a few days ago, and now that I've installed 7.10 it seems to not be able to recognize my display hardware anymore.

RADEON X300 SE 128MB HyperMemory [Display adapter]
RADEON X300 SE 128MB HyperMemory Secondary [Display adapter]
DELL E173FP [Monitor] (17.1"vis)

Thanks!

Jason Altenburg

---

### Post by wolfen69 on 2008-02-06
i wish you the best of luck. unfortunately you may never get it going with gutsy. the same thing happened to me when i switched to gutsy. but thankfully i dont care about desktop effects and dont need the nvidia drivers. sorry i cant be of more help, but ive personally given up trying to get it going. good luck, you'll need it.

---

### Post by jaltenburg on 2008-02-06
That's very discouraging.

With Envy I got it to the point where Compiz's advanced desktop effects were working awesome, I and my friends were very impressed with the various eye-candy.

But it seems every time I get this working, I get the Ubuntu loader going after reboot, then blank screen of death.

Jason Altenburg

---

### Post by CyDharttha on 2008-02-08
I'm having this same problem on someone's PC that is using a X300 from a Dell temporarily. Comes up fine with radeon driver, but after enabling fglrx with restricted drivers manager, machine boots then goes to blank screen when X should load. I can ssh into the machine, everything looks fine in dmesg and Xorg.0.log. I'm currently messing with monitor sync values and allowed resolutions in Xorg.conf, came on the forums, and am thinking I should try the radeon driver. Looking for enough performance to play Warcraft (again, just a temp replacement card). I'll post back with any results.

---

### Post by jaltenburg on 2008-02-09
Well, I think I'm going on about installation number 4 here.  About to revert back to 7.4, as I was having better luck with it with stability on the graphics end.  Any progress you have made would be GREATLY appreciated!

Jason

---

### Post by jonfenton on 2008-02-09
I have the same card and display. I ignored the Restricted Drivers option and installed as per the instructions in the BinaryDriverHowTo/ATI section of the Wiki section. I have not got visual effects to work but I am not bothered by this. Apologies if I have directed you to something you have already tried.

---

### Post by forrestcupp on 2008-02-09
I was under the impression that the x300 card worked fine with the Radeon drivers.  If not, I know the latest ATI drivers support the x300.  If you used Envy the first time, then upgraded, it breaks your drivers.  When upgrading, follow the instructions on what to do from the Envy web site.  But since it is too late, that doesn't matter.  If you haven't gotten to where you can boot to your desktop,  boot to the recovery console and type:
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and revert to the vesa drivers.  Then 
```
sudo apt-get --purge remove xorg-driver-fglrx
```

Then use [Envy](http://albertomilone.com/nvidia_scripts1.html) to install the latest ATI drivers.  You may have to do some other tweaking to get Compiz to work if you don't want to use Xgl.

---

### Post by AmericanYellow on 2008-02-09
What exactly happens when you install the restricted drivers and reboot? Do you get a completely black screen when you reboot?

---

### Post by jaltenburg on 2008-02-28
Just figured I'd let you all know that through a combination of rebooting, and perhaps some recent updates, I have gotten this to work beautifully.

The 3D support for most games is all messed up, but most of the Compiz Desktop effects are rendering quite nicely now, I have the burn transition enabled and I love minimizing and moving windows more than ever before.

I'd also like to say that while the cube is nice, I really do get a lot more of a sense of productivity when I use the desktop Wall plugin with a 2x2 grid.

Anyways, Again, this is not a lost cause, as I got it working

Thanks all!

---

### Post by jonnyreadsnews on 2008-03-03
How did you do it? I'm having the same problem.

Thanks,
Jon

---

