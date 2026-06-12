---
title: "ubuntu 12.10 on nexus 7: anyone have it running?"
date: 2012-10-27
forum: Mobile Technology Discussions (CLOSED)
---

### Post by senor_smile on 2012-10-27
When I saw today that Canonical released image and wiki page on loading ubuntu 12.10 on my nexus 7, I knew what I was going to do with my evening. 

As of right now, I haven't gotten very far.   It froze and I restarted my computer and nexus 7. The ubuntu nexus7 program is now stuck for a long time on "erasing boot partition".

Has anyone else tried this?&#12288;Succeeded? Failed?

---

### Post by dummy910 on 2012-10-27
skip it unless you need an excuse to waste a couple hours worth of time, and you want to be disappointed because its laggy to no end, and extremley buggy as it's brandy new...  again, skip it, unless you need an excuse to wipe and reinstall your current droid-os system.

---

### Post by KegHead on 2012-10-28
Hi!

Anyone with positive feedback?

KegHead

---

### Post by KegHead on 2012-10-29
Anyone?

---

### Post by thnewguy on 2012-10-29
Keep in mind the Ubuntu for Nexus project is in the very early stages. It probably won't be ready for serious use until around the time Ubuntu 13.04 arrives.

---

### Post by KegHead on 2012-10-29
Bummer!

I have not rooted yet.

I not sure I can wait for 13.04!

KegHead

---

### Post by gwjvan on 2012-11-01
Can't expect it to run very well at this stage

I installed it, and tried XFCE and KDE along with Unity. KDE works fairly well at this stage (at least with my tests). Unity seems to stop responding to taps after a while and needs a hard-reboot, and XFCE is hit or miss (I think on-board conflicts with some windows?).  A lot of programs don't run well yet (or at all).

I'm interested in doing some mobile audio editing, and this could be a really neat tool once the kinks are worked out- a very portable, mini studio on a tablet with [hopefully] good battery life. (JACK didn't work [and therefore all of the programs which depend on it], audacity doesn't load, but LMMS seemed to work [so that might be something to play with at the moment]).

---

### Post by KegHead on 2012-11-01
Hi!

Thanks for your update and review.

Looks like I may have to wait for 13.04.

KegHead

---

### Post by gwjvan on 2012-11-01
Yeah, even KDE started getting some visual errors/distortion after a while. I guess this release is targeted at developers/etc to help get it running/optimized.

I have to say that using touch (with my finger) for the regular desktop actions was easier than I expected. If I had a stylus with a small tip, I can imagine that some pretty precise interaction could happen.

---

### Post by gwjvan on 2012-11-01
But actually, LXDE is running fairly well (just a few visual distortions at the moment). A lot of the controls are small in LXDE, so I made a make-shift stylus which is working well.

Earlier I said that many apps don't work- but actually it seems that many do. The audio apps I was excited about don't work yet, but I just spent some time with GIMP and it worked fine. Most of the base applications seem to work. So, at the moment, I can see LXDE+OnBoard+stylus maybe being a usable option at the moment. (Though, I haven't spent tremendous amounts of time with it yet, and it all depends on how much you are willing to experiment/tweak I guess)

---

### Post by Copper Bezel on 2012-11-02
Wait a second - it can run KDE? What about Plasma Active? That's the one Gnuish Linux interface meant for this form factor. I'd be very tempted to try Ubuntu on my Nexus 7 if I could run a proper handheld interface. (No stylus needed there! Though I do suggest investing in a nice one - I use one occasionally (in Android) on my Nexus, and it's really worth the few cases it comes in handy.)

---

### Post by gwjvan on 2012-11-02
Yes, it ran KDE fairly well for a while. Though after a period of time, icons and text became a mess of random pixels. I don't know what happened--- this happens with the window decorations in LXDE as well.

I haven't tried plasma active, I briefly looked into tweaking KDE, and I remember reading something about how plasma active wouldn't work on this for some reason (but that might be completely wrong, I haven't looked into it too deeply yet).

Edit: Earlier today I put a fresh installation of Ubuntu on the Nexus 7 wiping out LXDE/KDE/XFCE (I added LXDE back so I'd have that to work with). I just tried installing plasma-active. I'm not sure if I installed it the way it was supposed to be installed, but I simply installed plasma-active from synaptic, and all of its dependencies. When I then try to log into a KDE Plasma session, it just gives me a black screen. So plasma active might not work out-of-the-box (unless I did something wrong, but I think synaptic should have taken care of it).

---

### Post by Copper Bezel on 2012-11-02
Yeah, I guess it would have been too much to hope for. = ) But thank you so much for trying that out and letting me know!

---

### Post by KegHead on 2012-11-07
Hi!

Anyone else w/positive results/comments?

---

### Post by KegHead on 2012-11-12
Hi!

Am I the only one interested in loading 12.10 on my N7?

KegHead

---

### Post by jerrylamos on 2012-11-13
> **KegHead said:**
> Hi!

Am I the only one interested in loading 12.10 on my N7?

KegHead
I'm interested, but at $200 I'll wait a while until people start getting usable results.

I'm comfortable with LXDE on my Thinkpad that Unity doesn't like, so LXDE would be O.K. if it will run reasonably.  I'm usually on the development forums such as raring and can take a certain amount of workarounds.

On raring I'm running unity/compiz though I'm no fan.

I do have a 10.1" tablet, Asus Transformer 101 with factory keyboard, Android is blazes faster than raring ubuntu on my netbook for output.  Input is another matter....note the netbook hardware is 1.6 gHz dual processors and the Transformer is 1.0 gHz dual processors, nominally slower specs for the tablet.  Same size memory.

---

### Post by mythic97 on 2012-11-25
If you want a stable good Ubuntu tablet I am afraid you will have to wait to 14.04 LTS by then bugs and stability should be sorted out hopefully and then Ubuntu for android should be ported over as well so there hate to disappoint

---

### Post by rebel1699 on 2012-11-27
I have been running Ubuntu 12.10 for quite a while now, and while it may have quite a few bug, it can be very useful. the more that use it, the faster it gets ready for primetime. Anyways, there are quite a few workarounds you can use to enhance your current experience. Not to mention there is now a multi boot solution for the Nexus 7, so you dont have to sacrifice a stable android os to test Ubuntu. Now, for a few workarounds. 

1. Accessing the fs on usb devices like thumbdrives or smartphones (if you have an otg cable). As it sits, it cannot access them through nautilus without some work. Here is how--

Insert usb stick and hit cancel when the error appears. Open terminal. Type "su" and enter password (ubuntu). Now type "cd". Type "mkdir /root/.config". Type "nautilus". Nautilus will open as root and drive will be accessible in left pane. Copy to and from as normal. This is the process for the first time. Every time after, just type su, then nautilus. 

2. Bluetooth would not pair to my SGS2 Skyrocket. Known bug, but easy to get around. Open the software center and download "Bluetooth manager". Open and you are set. I transfer files between Ubuntu and my android phone regularly, and in both directions. 

3. No wifi scanner. No problem. Again, open software center and install wifi radar. All set. 

4. No sound. Ubuntu has already stated the workaround for this. Unmute, suspend from power menu (not power button), and exit suspend. Sound will work. 

I use an otg cable and a usb hub, so I use a mouse, keyboard and various other devices at the same time. This alone makes a HUGE difference in functionality. When I do use the touchscreen, the only issues I find is the dash home scrollbar is unusually small and hard to manipulate. The other is no right click with touch, but it is a know issue. 

I also have working adb and fastboot binaries that were compiled for arm, so I can work on my phone from my Nexus 7 when I am not near a pc or laptop. SUPER CONVENIENT!

These things are very basic, but make a very large difference in the experience. I will continue using this to be able to report bugs and help it along as much as I possibly can. I am in no way a dev, so I am limited. But, it still has to be done. We learn as we go. If we can somehow contribute in the process, then it was well worth it. 

So, I hope you all have fun with it. I know I will. Have a great day, everyone.

Edit: If I may make one recommendation to the devs, it would be to add otg+host mode charging commits to the kernel. Many of us use a "y" cable, and being connected to power while still using peripherals via otg would be an excellent addition.

---

### Post by KegHead on 2012-12-07
Hi!

I'm still a little shy.

The Jelly Bean updates are great.

The apps are catching up in quality.

Not sure I can wait for 14.04.

KegHead

---

### Post by senor_smile on 2012-12-07
> **KegHead said:**
> Hi!

I'm still a little shy.

The Jelly Bean updates are great.

The apps are catching up in quality.

Not sure I can wait for 14.04.

KegHead

After so many initial problems, I decided to hold off at least until 13.04.  Plus, I agree that Android 4.2+ has some great features.  I read somewhere that dual booting Android and Ubuntu will be/is possible.

---

### Post by KegHead on 2012-12-07
Hi!

I'm a huge fan of Ubuntu. (since 8.4)

I love 4.2.1!

I'd like to see a dual boot!

KegHead

---

### Post by wojox on 2012-12-19
alright, i rooted and installed Ubuntu. it's fun. :D if you follow the wiki it's super painless. flashing the original image back on is just as easy. if you chose to let google back up your settings, you'd never know it was rooted.

---

### Post by kamelmahdjoubi on 2012-12-19
Thanks for you

---

### Post by Copper Bezel on 2012-12-19
wojox, there's nothing *painless* about that System Monitor. = )

---

### Post by RubenAlonzo on 2013-04-20
Hi there. I just installed 12.10 tonight, it is running fine, everything works, bluetooth, video, flash, sound, using T-bird for mail, youtube is fine, just do the update to it after install and you might be surprised!

---

