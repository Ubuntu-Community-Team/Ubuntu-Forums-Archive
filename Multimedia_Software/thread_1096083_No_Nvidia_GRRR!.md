---
title: "No Nvidia GRRR!"
date: 2009-03-14
forum: Multimedia Software
---

### Post by Reeman on 2009-03-14
Just got a phone call from my brother (who I built a computer for)
sounds like the kernel upgrades just broke his Nvidia legacy drivers... Now the poor slob will have to hit esc and scroll down to the rt kernel that was working really well with the Nvidia legacy. What would be better [LIST=1]
[*]Remove the offending kernels 2.6.27.7 and .11 through synaptic or
[*]edit grub to let him see the menu?
[*]edit grub to change the kernels order
[*]do nothing and have no connection to X11
[/LIST]
There should be an option to turn off the automatic update somewhere after he has things up and running properly again ...just cannot remember how with Ubuntu.

I am doing his tech support long distance as he is command line ignorant.

---

### Post by norwoods on 2009-03-14
what version of ubuntu?  if you are running 8.04, envyng should deal with kernel upgrades.  if ou are running 8.10, there are repos 0f 180 drivers that do not break with kernel upgrades.

---

### Post by Reeman on 2009-03-14
> **norwoods said:**
> what version of ubuntu?  if you are running 8.04, envyng should deal with kernel upgrades.  if ou are running 8.10, there are repos 0f 180 drivers that do not break with kernel upgrades.
Ubuntu Studio Hardy ....unfortunately with a rt kernel is the problem.
His system is setup to load the Nvidia module which I built against the rt kernel which is now broken by the kernel upgrades. I built the Nvidia driver because Ubuntu tried to install the wrong one for a GForce4 odd ball that used 8x agp but needed the legacy driver because of the chipset. I guess I should have just shutdown the kernel updates!

---

### Post by 67GTA on 2009-03-14
Does it have a TV tuner? Check to see if the cx18 module is being loaded. It comes with the 2.6.27 kernel for the first time. It can conflict with the nvidia module. Look here for more info: [http://ubuntuforums.org/showthread.php?t=1004660](http://ubuntuforums.org/showthread.php?t=1004660)

---

### Post by Reeman on 2009-03-14
> **67GTA said:**
> Does it have a TV tuner? Check to see if the cx18 module is being loaded. It comes with the 2.6.27 kernel for the first time. It can conflict with the nvidia module. Look here for more info: [http://ubuntuforums.org/showthread.php?t=1004660](http://ubuntuforums.org/showthread.php?t=1004660)
problem solved for now...no it has a tv svideo out though.
Got him running the older kernels with the auto-upgrade turned off. Nvidia drivers was only half the trouble though.

I am thinking that I will use Knoppix to dd his complete drive so that he can keep the good setup. Is Ubuntu going to have drive uuid trouble or will it easily clone to a new drive? ...I have never had to do it before.

Unfortunately he is also in fsck purgatory because the drive is starting to corrupt stuff...I will need to do a re-install to a new disk soon. The drive needed two fsck sessions to fix the root file system and who knows how long before it starts to mess up other sectors and partitions. 

Funny thing is that it is not slowing things down yet. I hate hard drives! 

Got him to run out and buy some thumb drives to save his recorded audio and other stuff real quick. 

He has a killer bunch of old vinyl that I helped him record to disk. Things like an original of Zappa's Hot Rats in top shape, some top label Columbia MasterWorks of the Columbia Symphony conducted by Igor Stravinsky (Le Sacre) and many great DGG Archive recordings ie: the incomparable recording they did of great soloists doing Bachs Bminor Mass!

---

### Post by markbuntu on 2009-03-14
Kernel updates do not support "unsupported" items like proprietary drivers etc because it would be very difficult to impossible for them to do so. This can ususally be fixed by reinstalling the drivers after the kernel update but not always. So, the best thing for you would be to blacklist kernel updates on your brothers machine. 

No matter which distro you use this will be an issue. Mandriva seems to handle this better than Ubuntu for now but there is no guarantees on that.

---

