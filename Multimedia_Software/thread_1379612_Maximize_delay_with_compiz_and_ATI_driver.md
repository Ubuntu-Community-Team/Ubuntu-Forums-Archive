---
title: "Maximize delay with compiz and ATI driver"
date: 2010-01-12
forum: Multimedia Software
---

### Post by amdalex on 2010-01-12
I installed the ATI driver from ATI's website and there is a noticable delay when maximizing windows from the task bar and when minimizing and maximizing windows. How can I fix this bug? thanks

---

### Post by amdalex on 2010-01-12
Anyone else have this issue?

---

### Post by amdalex on 2010-01-13
After I left my computer ib all night in the morning the graphics and mouse pointer were extremely laggy. Somebody has to know how to fix this?

---

### Post by amdalex on 2010-01-13
bump

---

### Post by amdalex on 2010-01-13
I installed Ubuntu Karmic a couple days ago and I have been fighting a bug with compiz and the ATI driver. I went to ATI's website and downloaded the 64 bit driver version 9.12 and installed it according to the directions. Everything works fine except for when I restore a window from the taskbar, minimize, or maximize a window there is a couple second delay. I have just turned off visual effects to get around this, but is there a way to fix this bug? thanks, my system specs are below

OS-  Ubuntu Karmic 64 bit
CPU- Amd Athlon x2 at 3ghz
2gb of DDR2-800 memory
Sapphire Radeon 4870 video card
22 inch Acer LCD monitor

thanks for you help

Also I made a thread about this in the desktop enviroments forum, but no one has replied, so if a mod reads this please delete the other thread.

---

### Post by overdrank on 2010-01-13
Hi and please do not create multiple threads on the same issue. Threads merged.

---

### Post by amdalex on 2010-01-13
Thanks for merging the threads.

---

### Post by amdalex on 2010-01-14
bump

---

### Post by amdalex on 2010-01-15
bump

---

### Post by amdalex on 2010-01-15
bump

---

### Post by ronni on 2010-01-18
Hi,

I also have this problem.

I have a Lenovo T500 with an ATI Technologies Inc Mobility Radeon HD 3650 256 mb memory.

When maximizing a window, there's a delay ~1 second, or if I use fullscreen using F11, there's a delay ~2 seconds.

If I remove the driver everything works fine, except that one of my two external samsung screens is blurry - I have tried to use different setups, and it's not the resolution or refresh rate.

---

### Post by ronni on 2010-01-18
I've also just noticed that if I disable all visual effects, there is no problem.

System -> Preferences -> Appearance -> Visual Effects => None.

---

### Post by amdalex on 2010-01-18
If I use the ATI driver and the computer is on for more than around 12 hours everything becomes extremely laggy and the CPU usage goes way up. Just another issue.

---

### Post by thethimble on 2010-01-21
Having a similar issue with an Asus F8V running an ATI HD3650. Minimize, maximize, and fullscreen all have noticably annoying delays.

I managed to fix the issue earlier (last week). Unfortunately, I updated packages and it began to happen again. Even more unfortunatly, I forgot how I fixed it :(

---

### Post by electric-c on 2010-01-29
Hi, 
had the same problem with my F6V and my ATI HD 3470.
Found a solution here: [http://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/381003](http://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/381003)

It's basically the Xserver with no backfill functionality.
Worked for me, hope this will help!

---

### Post by shockandawe on 2010-03-09
I added the repository.

Now what/where is the package I have to install? the xserver no backfill thing..


Cheers

---

### Post by shockandawe on 2010-03-09
OK. I figured out. You just have to add the repository and then run the update manager, this adds the package for you.

Now,

After doing this, it broke my system. After boot I was greeted with a black screen and could not go into my desktop.

Thank god I found the fix. Had to uninstall my ATI drivers and then re-install them.

------

Now for the best part: **the maximize delay is gone!**

------


Cheers! Now I can show off my Ubuntu desktop with pride!


**Just to add: Now the show desktop function is lighting quick, without delay! Excellent fix!**

---

### Post by madscientist032 on 2010-03-09
Look below for details and whatnot. It's how I got Compiz to work FLAWLESSLY on my Lenovo T400 with ATI Radeon HD 3450 256mb card.

Should be the third post from the top of the page. 

_[ATI Radeon Fixes]("http://ubuntuforums.org/showthread.php?t=1145967&page=3")_

Hope this helps.

---

### Post by hamidoo on 2010-04-03
yea got the same problem with Radion 3650 and karmic drivers version 10.3 from AMD-ATI downloads.
will probably switch back to my built-in intel.

I heard that ATI drivers for linux is all screwed then this proved it, what a shame AMD.

On my other PC the nvidia drivers is superb thumbs up nivida!

I really discourage ATI cards for linux users

---

### Post by madscientist032 on 2010-04-05
Based on my personal experience with ATI, it's usually (60 - 70%) an issue when it comes to graphics issues. NVIDIA's stuff is never this troublesome.

---

### Post by kamikazi on 2010-04-30
hmm, any ideas how to install this on lucid?

---

### Post by Boombino on 2010-04-30
There is another solution. In Ubuntu 10.04 with fglrx driver from its repository this command

sudo aticonfig --set-pcs-str=DDX,Direct2DAccel,TRUE

eliminated delay on minimizing/maximizing windows with compiz on my machine.
For details read this: [http://www.webupd8.org/2010/04/how-to-enable-direct2d-acceleration-in.html](http://www.webupd8.org/2010/04/how-to-enable-direct2d-acceleration-in.html).
Note, that using this method you don't modify your XServer (who IS NOT the guilty) but use some
new features from ATi driver (who IS the reason of this annoying bug).

---

### Post by cottfcfan on 2010-04-30
I managed to solve the ATI Min/Max issue.
If your using 9.10 and prior add the backfill ppa from here:
to your repos and update.

[https://launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill](https://launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill)

Then open Synaptic, look for "xserver-xorg-core"
Highlight it and press CTRL + e.
Then from the dropdown box look for "nobackfill".
Highlight it and click "force version" and apply the downgrade.
Log out and problem solved.

If you using 10.04 use the ppa from here:

[https://launchpad.net/~info-g-com/+archive/xserver-xorg-1.7.6-gc](https://launchpad.net/~info-g-com/+archive/xserver-xorg-1.7.6-gc)

update and upgrade.
Logout/In.

---

### Post by Rellix999 on 2010-05-01
delete me

---

### Post by gonchs on 2010-05-04
> **cottfcfan said:**
> I managed to solve the ATI Min/Max issue.
If your using 9.10 and prior add the backfill ppa from here:
to your repos and update.

[https://launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill]("https://launchpad.net/%7Eubuntu-x-swat/+archive/xserver-no-backfill")

Then open Synaptic, look for "xserver-xorg-core"
Highlight it and press CTRL + e.
Then from the dropdown box look for "nobackfill".
Highlight it and click "force version" and apply the downgrade.
Log out and problem solved.

If you using 10.04 use the ppa from here:

[https://launchpad.net/~info-g-com/+archive/xserver-xorg-1.7.6-gc]("https://launchpad.net/%7Einfo-g-com/+archive/xserver-xorg-1.7.6-gc")

update and upgrade.
Logout/In.

Thank you very much, sir. Problem solved.

---

### Post by cottfcfan on 2010-05-04
Glad I could help.
Although I have to admit it took me hours of trawling the web to find a solution easy enough to follow.

---

### Post by request_another on 2010-07-30
Sorry to bump this old thread, but i have tried the fix posted here and it works, but now the game Quadrapassel glitches bigtime. The fix seems to have broken some things as well. Can anyone check if this happens to them? Is there a way to fix it?

---

