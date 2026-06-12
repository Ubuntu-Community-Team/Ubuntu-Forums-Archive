---
title: "Nvidia card possibly burnt out"
date: 2008-05-03
forum: Multimedia Software
---

### Post by ChameleonDave on 2008-05-03
Whoa.  I just turned on my computer and went off to make a cup of tea.  When I got back, the screen was still black.  I had to reboot it, and it was still black — not even any messages from the graphics card or BIOS.

I was scared.  I rebooted, and this time put in a Puppy Linux live-CD, because I can safely do a hard reset on Puppy, without worrying about hard-drives being mounted.  This time it worked.  Phew!

I rebooted into Ubuntu.  It seemed OK, until KDE started up, and errors started to appear.  Compiz failed to start (so I had no window manager), and the Styleclock kicker applet complained that it could not start because of a lack of OpenGL support.  Games such as Scorched3D refused to start for the same reason.  Oh dear.  It was as though I had put in an antiquated video card instead of my quite reasonable NVidia 7900 GS.

I decided the card was burnt out.  Damn.

To make sure, I booted into my rarely-used XP installation.  Everything worked fine!  I was able to use 3D software such as Google SketchUp and Europa Barbarorum just fine.

Perplexed, I rebooted into Ubuntu.  Same errors.  Now, it is impossible that it is simply a Linux driver screw-up, because the problem initially occurred at the earliest stage of the boot process, way before Grub even suggests handing over control to the Linux kernel.  But then on the other hand, the problems is not (at least, any longer) purely physical, because it does work on Windows now.

I tried to reinstall all Nvidia- and Compiz-related packages in Synaptic, but there was an error when it tried to reinstall the main Nvidia driver, no doubt due to a lack of a functioning NVidia card.

I've pulled out the receipt for the 7900 GS, and it is dated 12/5/2007.  I assume I have a year's warranty, although that piece of paper doesn't mention it.  It's now 3/5/2008, so I may have little more than a week to sort this out.

If I do take it back, and manage to prove I have the right to do so, it will be tricky to prove it is defective if it works perfectly on Windows!  And meanwhile I can't use any Linux software requiring 3D acceleration.  If only I had the money to just upgrade my card right now.

What on earth should I do?

---

### Post by tamoneya on 2008-05-03
since the card works in windows I dont see what you will accomplish by replacing the graphics card.  What happens when you boot from the liveCD.  Do you get graphics there?

---

### Post by SICCpenguin on 2008-05-03
I agree, it would make more sense to back up needed stuff on a seperate partition and then re-install the OS. Then you should be able to re-install nvidia drivers and compiz with no problem -

---

### Post by ChameleonDave on 2008-05-03
> **SICCpenguin said:**
> I agree, it would make more sense to back up needed stuff on a seperate partition and then re-install the OS. Then you should be able to re-install nvidia drivers and compiz with no problem -

That assumes that the card is physically fine, and that reinstalling Ubuntu will make it work fine.  

The problems with that are (a) that's a big assumption (there may be a physical fault that Windows is managing to ignore but Ubuntu is picking up on); (b) surely if that is the case we'd be better off working out how to reinstall these drivers, rather than wiping out my highly customised Ubuntu installation.

-------

After having another try in Synaptic, I notice that the main Nvidia driver package actually does reinstall without reporting errors, but nvidia-glx-new-dev_169.12 does tell me:

```
dpkg-divert: rename involved overwriting '/usr/lib/nvidia/libGL.so.xlibmesa' with different file '/usr/lib/libGL.so', not allowed.
```

I'll now test the 3D acceleration on a live-CD.

---

### Post by tamoneya on 2008-05-03
i never said you had to install ubuntu.  Just put in the liveCD and see whether it works.  If it does then that means something is wrong with your install and you should consider reinstalling.  If the liveCD doesnt work then what you said may be true and the graphics card may be at fault.  It wont harm you at all to run the liveCD.  The more information you have the better.

---

### Post by ChameleonDave on 2008-05-03
> **tamoneya said:**
> i never said you had to install ubuntu.  Just put in the liveCD and see whether it works.  If it does then that means something is wrong with your install and you should consider reinstalling.  If the liveCD doesnt work then what you said may be true and the graphics card may be at fault.  It wont harm you at all to run the liveCD.  The more information you have the better.

I never said you said so.

And I never refused to try a live-cd.

------------

Anyway, back to the point.  I was very worried by the fact that the NVidia driver refused to install.  I thought it meant that it was goodbye to 3D effects on Ubuntu for me.  However, I then examined the error messages a bit, and decided to run *sudo mv -T /usr/lib/nvidia /usr/lib/nvidia.bak* and then try Synaptic again.  This time, the drivers installed correctly.  I rebooted, and now Compiz is working fine.  Phew!

I assume that the previous hardware failure caused the NVidia configuration to be so screwed up that all this was necessary.  The fact that the screen was black at boot time proved that this did not start with an error on Ubuntu itself, but in the video card (unless we posit that, by amazing coincidence, my monitor was malfunctioning slightly when I first switched the system on).

This would seem to indicate that I have an intermittent problem that I will not be able to prove to the shop where I bought this.  My warranty is about to expire.  If this problem becomes non-intermittent in a couple of months' time, I will be up a creek without a paddle.

Oh well, at this stage no one can help me any longer.  Thanks.

---

