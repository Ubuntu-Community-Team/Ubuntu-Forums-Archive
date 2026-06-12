---
title: "MythTV frontend wil not start on UmbuntuStudio"
date: 2007-11-19
forum: Mythbuntu
---

### Post by harvey186 on 2007-11-19
Hi toegether,

I have isnstalled MythBuntu on my existing UbuntuStudio. I can run the MythBuntu setup, but the frontent will not start. 

What can I do ?

Thanks, Harvey

---

### Post by superm1 on 2007-11-19
Remove ~/.mythtv/ and try again.  Try starting the frontend from command line.

---

### Post by harvey186 on 2007-11-22
> **superm1 said:**
> Remove ~/.mythtv/ and try again.  Try starting the frontend from command line.

Hi, yes, that works, but it shows only the TV screen, now way the enter the recording menu or the setup of the audio interface.

---

### Post by superm1 on 2007-11-22
Can you post the output of the command line launch?

---

### Post by harvey186 on 2007-11-23
> **superm1 said:**
> Can you post the output of the command line launch?

Attached you will find the output. I have to split it, because it was to big for one upload. I hope you will find my problem.

Thanks, harvey

---

### Post by superm1 on 2007-11-23
Um.  I meant to start it using the 'mythfrontend' command.

Nonetheless:

2007-11-23 17:23:02.651 VideoOutputXv: Pixel dimensions: Screen 1600x1200, window 1600x1200
2007-11-23 17:23:02.652 VideoOutputXv: Estimated display dimensions: 406x305 mm  Aspect: 1.33115
2007-11-23 17:23:02.652 VideoOutputXv: Estimated window dimensions: 406x305 mm  Aspect: 1.33115
2007-11-23 17:23:02.653 VideoOutputXv: XvMCTex: Init failed
2007-11-23 17:23:02.654 VideoOutputXv: @ j=3 Looking for flag[s]: XvInputMask XvImageMask 
2007-11-23 17:23:02.654 VideoOutputXv: No suitable XVideo port found
2007-11-23 17:23:02.654 VideoOutputXv Error: Could not find suitable XVideo surface.
2007-11-23 17:23:02.655 VideoOutputXv: Falling back to X shared memory video output.
                              *** May be slow ***

That means that your video driver isn't enabled for video output.  You will need to enable a proprietary graphics driver (and if you already have one enabled, Xv output for it)

---

### Post by harvey186 on 2007-11-24
> **superm1 said:**
> 
That means that your video driver isn't enabled for video output.  You will need to enable a proprietary graphics driver (and if you already have one enabled, Xv output for it)

I would be happy if I would know, how to do that. I have a Matrox Parhelia DL256 PCI-X. 

When I use Termianl: mythfrontend, I get the setup. Thanks.

---

### Post by clubsoda on 2007-11-27
Do you have the mga_hal driver installed?

Search [http://matrox.tuxx-home.at](http://matrox.tuxx-home.at) for more information on that.

---

### Post by harvey186 on 2007-11-28
> **clubsoda said:**
> Do you have the mga_hal driver installed?

Search [http://matrox.tuxx-home.at](http://matrox.tuxx-home.at) for more information on that.

No, I have installed the latest mtx driver from tuxx-home, because my Parhelia needs the the mtx driver.

---

