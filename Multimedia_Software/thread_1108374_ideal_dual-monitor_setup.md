---
title: "ideal dual-monitor setup"
date: 2009-03-27
forum: Multimedia Software
---

### Post by jon23d on 2009-03-27
I am purchasing a new computer and want to get the best hardware possible for dual monitor support.  I use Ubuntu 8.10.  Last time I tried to do dual-monitors I couldn't quite get it working.  This time I can buy whatever hardware I need, so I'd love to hear what hardware other folks have had work easily.

On another note, I was going to use vmware esxi.  Does this cause issues?  Is there any other way to make use of 8g of ram?

Thanks!

---

### Post by markbuntu on 2009-03-27
any 64 bit install will use all your ram.

You should get 24 inch monitors. They do 1920x1080 which is 1080p HDTV which can save a lot of processing power in full screen HD mode. Plus they are really huge so you can have a lot of stuff up at once without changing desktops. I have one 24 inch and a 19 inch and now I really need another 24, lol. I have an ati HD36501GB card, probably not the best if you are a gamer or graphics maker but it works fine for me.

---

### Post by jon23d on 2009-03-27
Can you recommend any particular video card(s)?

---

### Post by markbuntu on 2009-03-27
Some people around here have some very strong opinions about video cards and I just don't want to get involved in recommending anything specific but I will give you the basic scoop on the current situation.

Generally it is between nvidia and ati. ATI is dropping support in their proprietary driver for anything before the Radeon HD3xxx cards after the next driver so they can concentrate on the newer cards. 

ATI has released all the info they can about all their cards to the open source driver writers so great advances are being made with the open source drivers for ati. So while they are not so hot for newer cards now, the latest open source drivers work very well for older cards.

The ati open source drivers already have very good 2D acceleration for all cards and some preliminary 3D for newer cards, They expect to have working 3D for many newer cards within the next 6 months or so and for many cards the open source driver outperforms the proprietary driver already.

Nvidia is being more reluctant so the nvidia open source drivers are suffering but the proprietary drivers seem to be better than ati at the moment.

They both have their problems. The nvidia proprietary driver has crappy 2D acceleration but very good 3D. The ati proprietary driver has good 2D and 3D but has issues with tearing in video playback but this seems to be improving with every release. 

So, your decision.....

---

### Post by ad_267 on 2009-03-27
Dual monitors with an Nvidia 6600 gt (pretty old now, I know) working very well here.

---

### Post by markbuntu on 2009-03-27
One thing about large dual monitors. Some older cards cannot support that large of a display area, ie 3840x1200 for 2 24 inch at 1920x1200.

---

### Post by jon23d on 2009-03-27
Wel, I don't particularly care about much other than work.  The machine will be for work only, and very little 3d anything (except compiz I guess) will be necessary.  I've had good luck with Nvidia since the beginning with Ubuntu, but I could really care less which I use.  The most important thing to me is that I get a model that *works* for dual monitor.  I don't care if I use two video cards, or a dual-head.  I don't want to spend a ton if I can avoid it.  I just want something that works!

---

### Post by questworld on 2009-03-27
Nvidia geforce go 7400 GPU video card does a good job for me. 

I am using my Bravia TV as the second monitor. I use the Nvidia X server setting to use dual monitor. The ubuntu default monitor manager does not work for me.

---

### Post by norwoods on 2009-03-27
i am happily running an nvidia 9600gt with 1920x1200 and 1600x1200 monitors.  i update to the latest nvidia proprietary prereleases for 64 bit Ubuntu 8.10 and nvidia 9600GT, 180.41 currently, from [www.avenard.org](www.avenard.org) (third party software source "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/")using System-->Administration-->Synaptic Package Manager.  i am not sure which programs are needed so i install all six provided:
nvidia-180-libvdpau
nvidia-180-libvdpau-dev
nvidia-180-modaliases
nvidia-180-kernel-source
nvidia-glx-180
nvidia-glx-180-dev

the nvidia-settings program make it very easy to set up twinview, one desktop over the two screens.

---

### Post by Willleung on 2009-03-29
> **markbuntu said:**
> One thing about large dual monitors. Some older cards cannot support that large of a display area, ie 3840x1200 for 2 24 inch at 1920x1200.

running 3840x1200 off a 780G on board graphic (one VGA, one DVI) worked well, but i couldn't get it to run another monitor with a ATi 3450 (ubuntu 8.10 simply wouldn't boot).

XP had no problems, but i am running a lot of Java during the day, and XP just crashes after let's say 10 minutes, Ubuntu since to use much less resource, too bad i can't get the third monitor up..

---

### Post by jon23d on 2009-03-30
How about the difference between dual-head v. dual video cards?  Has anyone had issues with one or the other?

---

### Post by ad_267 on 2009-03-31
> **jon23d said:**
> How about the difference between dual-head v. dual video cards?  Has anyone had issues with one or the other?

I think dual video cards aren't so well supported. I don't have any experience myself but I know there are issues using dual nvidia cards like you can't use TwinView and Compiz.

---

### Post by jon23d on 2009-04-02
Thanks for all the help folks.

I'm typing this on my new rig now.  I ended up getting 2 23" acer monitors and an Nvidia GeForce GTX 260.  Setting them up was much less difficult than the last time I tried this, and it actually works!

There are definitely some oddities.  My taskbars only show on one monitor, and the cube doesn't behave quite like I'm used to, but it is definitely 100% completely functional.  I am very satisfied with the setup and would recommend it to others!

---

### Post by ad_267 on 2009-04-03
> **jon23d said:**
> Thanks for all the help folks.

I'm typing this on my new rig now.  I ended up getting 2 23" acer monitors and an Nvidia GeForce GTX 260.  Setting them up was much less difficult than the last time I tried this, and it actually works!

There are definitely some oddities.  My taskbars only show on one monitor, and the cube doesn't behave quite like I'm used to, but it is definitely 100% completely functional.  I am very satisfied with the setup and would recommend it to others!

If you're using TwinView you should be able to create a new panel and move it over to the other monitor (right click on a panel, select create new, then drag it). I have two panels, one at the bottom of each monitor :)

---

### Post by jon23d on 2009-04-03
ooohhh!  So how do I get windows on the monitor with the new taskbar to show up on that one instead of the other?

---

### Post by ad_267 on 2009-04-03
> **jon23d said:**
> ooohhh!  So how do I get windows on the monitor with the new taskbar to show up on that one instead of the other?

Right click on the new taskbar, select add to panel, and add a window list.

---

### Post by jon23d on 2009-04-03
Thank you so much!  After a little tweaking I think everything is perfect.  I'm having just a little bit of trouble getting emerald to stick, but my windows pals are drooling already :)

---

