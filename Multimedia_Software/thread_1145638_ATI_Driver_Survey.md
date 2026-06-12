---
title: "ATI Driver Survey"
date: 2009-05-01
forum: Multimedia Software
---

### Post by hblaw on 2009-05-01
Hi,

For my card, X1250, the video is so slow.

I am not sure how well the open source driver / fglrx driver has performed on your machine. Can you share the card names and glxgears output? (Like below)

ATI Card name - driver (opensource or fglrx) - 8.10 or 9.04 - glxgears output per second - Visual effects (in your "Appearance").

MINE:
------------------------
Radeon X1250 - open source - 9.04 - 350-380/s - None
------------------------

Thanks.

---

### Post by pme 72 on 2009-05-01
Radeon x1550-opensource-9.04-1275/1300FPS-Custom
Radeon x1550-opensource-8.10-1381FPS-Custom
Radeon x1550-opensource-8.04-866FPS-none
Radeon x1550-fglrx-8.04-2813FPS-Custom

Radeon xpress 200m integrated-opensource-8.10 790-804FPS-Custom

---

### Post by Melcar on 2009-05-01
Glxgears is not a benchmark.  The open source drivers are slow, but things like video playback should not be a problem.  My laptop's 200M plays accelerated videos just fine.

---

### Post by vonti on 2009-05-01
So what do you think the drivers should be for a Radeon HD 3450?
I've got the ATI/AMD proprietary FGLRX drivers, are there any better ones??

---

### Post by rodney757 on 2009-05-01
I have the HD 3200 and am using the latest proprietary driver with Jaunty. I can't watch videos with visual effects enabled. Some programs like blender struggle with effects enabled also. Everything is fine with no effects. Is there any better drivers?

---

### Post by hblaw on 2009-05-01
> **Melcar said:**
> Glxgears is not a benchmark.  The open source drivers are slow, but things like video playback should not be a problem.  My laptop's 200M plays accelerated videos just fine.

Please just give the numbers and do not make subjective assessment. Mine plays video fine, but menu lags, screen flicks, bla bla bla. 

Many thanks.

---

### Post by jrice219 on 2009-05-02
I have the same X1250 card in my Acer Extensa 4420 laptop.


X1250 - fglrx - 8.10 - and I can't enable visual effects because it slows my machine down to much and then I can't watch hulu :(

---

### Post by Melcar on 2009-05-02
> **hblaw said:**
> Please just give the numbers and do not make subjective assessment. Mine plays video fine, but menu lags, screen flicks, bla bla bla. 

Many thanks.


It's not a benchmark, so numbers are useless.  My old x1950xt scored significantly higher that my HD4850.  The test is just to see if you have working 3D acceleration or not.  But fine, I get 270fps with my 200M and the open drivers (KDE4 with effects turned on).
The open drivers are about 1/2 as fast as fglrx when it comes to raw 3D performance.  On top of that, they lack redirected direct rendering (which fglrx has started to implement), which is what allows opengl and other accelerated applications to run on composite managers (Compiz for example) without suffering from blinking.

---

### Post by hblaw on 2009-05-02
Thank you Melcar.

It seems you know a lot about the video card. Is there ANY reliable benchmark that everyone can easily get? I am starting this just to make it easier for everyone to get a sense of how well the opensource and fglrx work in 8.10/9.04, and they can make informed choice / upgrade decision.

Thanks.

---

### Post by Yellow Pasque on 2009-05-02
If you're unsatisfied with the performance of the open-source drivers, you'll need to find a distro that still uses Xserver 1.5.x at the latest, so you can install the Catalyst 9.3 drivers (or whatever Catalyst that distro ships with).

> Glxgears is not a benchmark.
..because it's worth repeating - **glxgears is not a benchmark**

> So what do you think the drivers should be for a Radeon HD 3450?
I've got the ATI/AMD proprietary FGLRX drivers, are there any better ones??
For R600/R700 chips? Open-source drivers with 3D acceleration don't exist yet (unless you like to build your Linux from source code in experimental git branches..) :P

---

### Post by Zoowey on 2009-05-02
Well I for one can say I am VERY happy with the fglrx driver. I have two Radeon HD 4850's running in crossfire on Ubuntu 9.04 working absolutely wonderful. In every single game, including very demanding ones I can max  out the settings and usually find myself getting at least 100 FPS on any game with maxed out settings.

However, it's not flawless. I can't play videos with compiz running as the videos do play and don't blink but my entire desktop just slows down, and when I click the "X" button to close a window it takes 20 seconds for the window to close with any video playing. The 9.3 driver did not do this but it did have blinking videos.

But overall, if I wanna watch a video I just turn off compiz and it works flawlessly. As for driver stability, I've been running Ubuntu 8.10 for 5 months and 9.04 for about a week and haven't had a single system or x.org crash. So it's stable as a rock.

Other then that one problem I really can't complain, I'm very happy with the driver.

---

### Post by Melcar on 2009-05-02
[PTS]("http://www.phoronix-test-suite.com/") is probably the best way to benchmark.
Some time ago I did some comparisons between the open drivers and fglrx.  Let me see if I can find them...

Here:

[http://global.phoronix-test-suite.com/?k=profile&u=melcar-13973-18118-32143]("http://global.phoronix-test-suite.com/?k=profile&u=melcar-13973-18118-32143") 
[http://global.phoronix-test-suite.com/?k=profile&u=melcar-16732-14360-5380]("http://global.phoronix-test-suite.com/?k=profile&u=melcar-16732-14360-5380")

---

### Post by Niniel on 2009-05-02
I guess my cards are not all that interesting since they are old, but they work with the open source driver as well as the proprietary ones used to:
X800 XT - Desktop Effects: Yes
Mobility Radeon 9600 - Desktop Effects: Yes.
Just a few minor issues with the X800 and Compiz on: there's a black border around things overlaying the actual video window in Totem (volume control, menus, other windows... anything), and the drawers on the panel are slow to open. And when I move a window, the contents seem to remain in place and the window gradually turns black - could be a feature/an effect though. 
In any case, none of these bother me.

---

