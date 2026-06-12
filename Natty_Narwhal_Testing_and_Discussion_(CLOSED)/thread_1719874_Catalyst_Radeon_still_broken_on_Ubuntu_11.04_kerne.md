---
title: "Catalyst Radeon still broken on Ubuntu 11.04 kernel 2.6.38"
date: 2011-04-02
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by hai2lp on 2011-04-02
I'm using AMD catalyst driver but...
Why still not worked, even ubuntu just pre-release the [COLOR=Red]fglrx 8.840[/COLOR] in [COLOR=SeaGreen]Ubuntu Natty 11.04 Beta 1[/COLOR],

On unity it's completely broken , just BLANK SCREEN or if click somewhere the display is broken, compiz also not work

Only working good if you choose [I]Ubuntu Classic (no effects)

Please anyone got luck installing the new fglrx with Natty 11.04 ?


I'm using AMD VISION laptop (AMD E-350 zacate, Radeon 6310) vaio VPC-YB15AG

---

### Post by tcchris on 2011-04-02
Same issue with me. I went back to Radeon drivers.The Radeon drivers are working quite well for me , I may keep them

---

### Post by screaminj3sus on 2011-04-03
same issue here with a mobility hd2600

---

### Post by meanpt on 2011-04-03
Same here with ATI Mobility Radeon 5450. All I get is a black screen - lucky those who can see a classical with no effects

---

### Post by Cam! on 2011-04-03
I had to re-install, and I noticed that a popup for Available Restricted Drivers...well, popped up. Does this mean that ATI has released the drivers for the Radeon HD 6850? The FOSS drivers are alright, but games like Minecraft lag.

---

### Post by Tmcarr on 2011-04-03
While I'm a big free software supporter, sometimes its just better to go with the proprietary stuff, so yes, I would say go for it.

---

### Post by cariboo on 2011-04-03
Have you followed the instructions that I linked to [here]("http://ubuntuforums.org/showpost.php?p=10618166&postcount=1")?

---

### Post by TBABill on 2011-04-03
Proprietary drivers usually manage fans, cooling and performance better in general. I always use them if available.

---

### Post by Harry33 on 2011-04-04
> **Cam! said:**
> I had to re-install, and I noticed that a popup for Available Restricted Drivers...well, popped up. Does this mean that ATI has released the drivers for the Radeon HD 6850? The FOSS drivers are alright, but games like Minecraft lag.

Read this first:
[http://ubuntuforums.org/showthread.php?t=1719874](http://ubuntuforums.org/showthread.php?t=1719874)

---

### Post by Zorgoth on 2011-04-04
If you want to use the very latest proprietary ATI drivers, you can:

sudo apt-get install fglrx - this is in fact newer than what is on ATI's website, and unlike that will work with natty.

But you need to update compiz by adding the ppa ubuntu-daily and installing all the upgrades it provides before you reboot - otherwise unity + fglrx = death.

---

### Post by beew on 2011-04-04
> **Tmcarr said:**
> While I'm a big free software supporter, sometimes its just better to go with the proprietary stuff, so yes, I would say go for it.


Unfortunately NO FOSS driver gives proper 3d supports. You can use the FOSS drivers for things like Compiz and that's the best they can do, but no real hardware acceleration, no h264 gpu decoding, really you don't get most of the functions out of your graphic cards with FOSS drivers and I don't think it is going to change any time soon (doubt that they even plan to implement the advanced features and whether it is technically feasible)

I don't know how good the ATI closed source drivers are but in general the FOSS graphic drivers are only good enough for people who need basic functions, not performance from their graphic cards, so using them is  wasting of the money you pay for the hardware IMO.

---

### Post by meanpt on 2011-04-04
:( big deal ... I can'r even see the desktop, only hear the desktop openig sound, not even with the i386 dvd ... is there a boot code that gives me some desktop to work with?

---

### Post by Cam! on 2011-04-04
I installed the drivers, and Unity won't work. Upon further inspection, Minecraft crashes due to Java failing. D:

---

### Post by Zorgoth on 2011-04-04
Cam! - look at my reply to this post and at this link:

[http://ubuntuforums.org/showpost.php?p=10618166&postcount=1](http://ubuntuforums.org/showpost.php?p=10618166&postcount=1)

---

### Post by P-I H on 2011-04-04
I just installed the proprietary fglrx driver. Unity did not work at first, but after activation of the ppa:unity/daily and upgrade of the system Unity works.
The ATI Catalyst Control Center is working and I am able to set the "Tear free" option to play videos without tearing.
The system has an AMD Radeon 5450 card.

---

### Post by Cam! on 2011-04-04
Hm. So if I follow those terminal commands, I won't have the problems I'm having right now?

---

### Post by azzach on 2011-04-04
I am fairly savvy with Ubuntu as a whole, but the other day when this error came up I had to call for help. Here it is:

I recently downloaded and installed Ubuntu 11.4 Alpha 3. I would assume the architecture to this release is very similar to Ubuntu 10.10 Net-book edition as it runs uTouch. When I activated the  ATI/AMD Propietary FGLRX Driver  I restarted my computer only to find black squares covering my desktop. No words, only a desktop covered in black artifacts that move when scrolled over. I managed to guess click my way to turning off the driver but it wasn't easy. I tried a total of three times with the same results. Any help would be greatly appreciated.

Specs: Inspiron One Touch PC 64-bit, 4 GB Ram, 1000 GB Hard drive, AMD Athlon II X2 250u Processor DUO, Vision AMD Graphics

---

### Post by clhsharky on 2011-04-04
azzach


Welcome to UF.

Natty has its own sub forum here
Development & Programming>Natty Narwhal Testing and Discussion
[http://ubuntuforums.org/forumdisplay.php?f=394](http://ubuntuforums.org/forumdisplay.php?f=394)

> Propietary Driver Failure Black Squares Desktop
ATI Proprietary driver never works right till after OS release.


Sharky

---

### Post by screaminj3sus on 2011-04-04
The ati drivers are b0rked in natty, they only work in classic with no effects.

EDIT:

NVM followed instructions posted to use unity dialy builds, now they work!

Advice to anyone who installs them, make sure you disable "sync to vblank" in compiz if you enable tearing free desktop in ccc, or you will get horrifically slow compiz and scrolling.

---

### Post by ToxicBurn on 2011-04-05
The ATI drivers will 100% mess up your Beta 1 install they need to be removed from the repo who tested this before release ?

11.04 - ATI HD 5770 = Not even close to working

---

### Post by ToxicBurn on 2011-04-05
The ATI drivers in beta 1 will Bork your install its a total 100% mess .

one day i hope drivers are one of the first things done so hardware works through out testing and not a week or two before release .

what would happen if you didnt have good drivers for network cards untill a week before final release ?

my hope is one day linux will get to the point MAC is at now

---

### Post by jfernyhough on 2011-04-05
1) Natty in in beta.
2) The fglrx drivers are in beta.
3) Beta.

Try a mainline kernel. 2.6.38.2 works for me.

(search: mainline kernel ppa)

---

### Post by lucazade on 2011-04-05
> **ToxicBurn said:**
> The ATI drivers in beta 1 will Bork your install its a total 100% mess .

one day i hope drivers are one of the first things done so hardware works through out testing and not a week or two before release .

what would happen if you didnt have good drivers for network cards untill a week before final release ?

my hope is one day linux will get to the point MAC is at now

If you stick with LTS instead of upgrading every 6 months you won't have this kind of issues.
There is no magic in Mac, nothing I'd like to use in my linux box.

---

### Post by osarusan on 2011-04-05
Cam -- I am using the fglrx drivers and the updated Unity ppa, and they work splendidly.

Toxicburn -- maybe something else is wrong on your system? The fglrx drivers are working fine for me.

---

### Post by screaminj3sus on 2011-04-05
> **ToxicBurn said:**
> The ATI drivers will 100% mess up your Beta 1 install they need to be removed from the repo who tested this before release ?

11.04 - ATI HD 5770 = Not even close to working

Did you use the unity daily ppa? Also when you install and ppa and update, don't install the drivers right off. Reboot again and update and you will get a bunch of xorg updates that didn't come through before (at least that happened to me)

I installed the unity ppa, updated, rebooted, installed fglrx and my system booted into cli, so I set my system to use mesa, rebooted, updated and got the xorg updates, reactivated fglrx and everything worked fine.

---

### Post by Mark Phelps on 2011-04-05
Also ... Natty Beta 1 just came out.  Should really be using that, not an old Alpha.

---

### Post by s.fox on 2011-04-05
Thread moved to  [Natty Narwhal Testing and Discussion]("http://ubuntuforums.org/forumdisplay.php?f=394")

---

### Post by screaminj3sus on 2011-04-05
They work fine if you use the unity daily ppa.

---

### Post by DougieFresh4U on 2011-04-05
> **ToxicBurn said:**
> The ATI drivers in beta 1 will Bork your install its a total 100% mess .


Say what?
Seems to be just fine here.

**EDIT:**
AMD Athlon 5200 x2
ATI Radeon HD3200

---

### Post by NIxie on 2011-04-05
Confirmed working with unity daily ppa!

---

### Post by mpnordland on 2011-04-05
You all probably know this, but fglrx is simply horrible with unity. Is there any way to fix it?

---

### Post by Harry33 on 2011-04-05
> **mpnordland said:**
> You all probably know this, but fglrx is simply horrible with unity. Is there any way to fix it?

In a number of other threads here it is said that new fglrx prerelease works in Natty if also Unity Daily PPA is added and system upgraded.

---

### Post by cubeist on 2011-04-05
> **ToxicBurn said:**
> The ATI drivers in beta 1 will Bork your install its a total 100% mess .

one day i hope drivers are one of the first things done so hardware works through out testing and not a week or two before release .

what would happen if you didnt have good drivers for network cards untill a week before final release ?

my hope is one day linux will get to the point MAC is at now

Beta software by its very definition will often 'bork' your system...Precisely so the final release is bug free (or realistically minor bugs only). If you try a developer preview version of Mac OS one month before release, you would find the same thing. Bork!

Your comparing apples to onions...

Anyway, as others have mentioned, and a search would have answered, if you want to use unity/compiz with restricted ati drivers you need the unity daily ppa, OR, use unity 2d.

---

### Post by cariboo on 2011-04-05
This is getting a little ridiculous, If you are having a problem with the ATI drivers, please post in an existing thread. We don't need 10 -15 threads all saying the same thing. 3 threads merged.

---

### Post by wsonar on 2011-04-05
> **cariboo907 said:**
> Have you followed the instructions that I linked to [here]("http://ubuntuforums.org/showpost.php?p=10618166&postcount=1")?


Resolved issue
(This gets me in then theme reverts back to basic looks corrupted when you pull up apperance preferences hass squares for the theme name)


side question

will 11.10 still use evolution since it's  tied to gnome?

---

### Post by wsonar on 2011-04-05
should the default be gnome or unity in 11.04 still looks like gnome but with the single menu which I always use anyway

So yea this is just gnome where is unity?

---

### Post by wsonar on 2011-04-05
fglrx never worked for me in 10.x

I uninstalled and get to desktop but it looks like clearlooks or very basic

basically no themes work

---

### Post by wsonar on 2011-04-05
maybe one of these 267 updates might help lol

---

### Post by cariboo on 2011-04-05
Merged another two threads on the same subject, although the last few posts are looking like they are trying to hijack the thread.

---

### Post by drumour on 2011-04-05
Working now on asus hd 6870, like noted elsewhere, did following

remove os radeon ->
sudo apt-get remove --purge xserver-xorg-video-radeon

remove any /etc/X11/xorg.conf

latest kernel in synaptic->
2.6.38-8-generic

daily unity build as at ->
[https://launchpad.net/~unity/+archive/daily](https://launchpad.net/~unity/+archive/daily)

fglrx as in synaptic ->
2:8.840-0ubuntu1

setup x before reboot ->
sudo aticonfig --initial

= Working and seemingly with power management :)

---

### Post by wsonar on 2011-04-05
> **cariboo907 said:**
> Merged another two threads on the same subject, although the last few posts are looking like they are trying to hijack the thread.

Not trying to hijack original issue was video then I started rambling on which can happen when your trying something new

---

### Post by wsonar on 2011-04-05
fglrx driver still does not work on my machine it was already using that driver

and reverts back to gnome says my hardware will not support unity 

Does it matter that it's a virtual box?

maxed out video ram on the vbox to 128mb still dosen't work

---

### Post by osarusan on 2011-04-05
VirtualBox still doesn't fully support 3d AFAIK so it makes sense it wouldn't be able to run Unity. You need Compiz to have it work. Try installing the Unity2d package in your VB to get a working system.

For everyone else who keeps posting the same complaint:
*Unity. Daily. PPA.*

Once I installed that, I haven't had a single fglrx problem.

---

### Post by ToxicBurn on 2011-04-05
i just do not understand why video drivers are still a problem in linux after years and years of work something as simple as making sure people can see the OS on the monitor and yet linux still cant get it together .

heck even the first Dev preview of Mac os x Lion has new fully working ati drivers and its just a Devlopers preview build.

im starting to think its a waste of my time playing with Linux its juat a hobby OS and not really fun anymore if i cant see the stuff on my screen or boot to a desktop to test the beta.


i give up

---

### Post by Harry33 on 2011-04-06
> **ToxicBurn said:**
> i just do not understand why video drivers are still a problem in linux after years and years of work something as simple as making sure people can see the OS on the monitor and yet linux still cant get it together .
heck even the first Dev preview of Mac os x Lion has new fully working ati drivers and its just a Devlopers preview build.
im starting to think its a waste of my time playing with Linux its juat a hobby OS and not really fun anymore if i cant see the stuff on my screen or boot to a desktop to test the beta.
i give up

Perhaps these two facts should be looked at.

1) Proprieatary drivers generally are the best bet to get proper support. Only original manufacturers know exactly how to build drivers for their products. NVidia is a good example of this. They do themselves the Linux drivers and they do work.

2) For any driver to work in Linux and with new xserver releases it has to be built against the new xserver and its new demands. Using dev cycle versions of Linux distro of course means from time to time you have to wait for new drivers. This is because new dev versions of xserver are pulled in as early as possible. Only open source drivers can keep up the pace of that.

---

### Post by jfernyhough on 2011-04-06
> **ToxicBurn said:**
> beta.
4) Beta.

Looks like a fix was included in 2.6.38-8 to disable fbdev. This was causing issues (again) with fglrx. Weird how it worked fine with the mainline builds, though. Wonder if it's AppArmour getting in the way.

> even the first Dev preview of Mac os x Lion has new fully working ati driversThat's because they have to support about six different cards, not hundreds going back years. Plus only one kernel sauce, one build environment, one desktop API, one stable graphics interface, etc..... It's also in AMD's immediate interest to keep the cards working due to the commercial arrangement they have with Apple.

---

### Post by jfernyhough on 2011-04-06
> **wsonar said:**
> fglrx driver still does not work on my machine it was already using that driver

and reverts back to gnome says my hardware will not support unity 

Does it matter that it's a virtual box?

maxed out video ram on the vbox to 128mb still dosen't workYou can't install fglrx inside VirtualBox as it has a virtual graphics adapter. You have to install the guest additions to get Compiz (and Unity) working.

---

### Post by qamelian on 2011-04-06
> **osarusan said:**
> VirtualBox still doesn't fully support 3d AFAIK so it makes sense it wouldn't be able to run Unity. You need Compiz to have it work. Try installing the Unity2d package in your VB to get a working system.

For everyone else who keeps posting the same complaint:
*Unity. Daily. PPA.*

Once I installed that, I haven't had a single fglrx problem.
I've installed that PPA and updated, which resulted in an even more broken system. Where before Compiz simply failed, now my netbook locks up solid with the display flashing.

---

### Post by wsonar on 2011-04-06
> **osarusan said:**
> VirtualBox still doesn't fully support 3d AFAIK so it makes sense it wouldn't be able to run Unity. You need Compiz to have it work. Try installing the Unity2d package in your VB to get a working system.

For everyone else who keeps posting the same complaint:
*Unity. Daily. PPA.*

Once I installed that, I haven't had a single fglrx problem.

Yea figured that to bad no 3d emulation yet

---

### Post by yourwhiteshadow on 2011-04-07
> **drumour said:**
> Working now on asus hd 6870, like noted elsewhere, did following

remove os radeon ->
sudo apt-get remove --purge xserver-xorg-video-radeon

remove any /etc/X11/xorg.conf

latest kernel in synaptic->
2.6.38-8-generic

daily unity build as at ->
[https://launchpad.net/~unity/+archive/daily](https://launchpad.net/~unity/+archive/daily)

fglrx as in synaptic ->
2:8.840-0ubuntu1

setup x before reboot ->
sudo aticonfig --initial

= Working and seemingly with power management :)

thanks...works beautifully, but unfortunately its extremely laggy/slow. but still, definitely a step in the right direction.

---

### Post by wsonar on 2011-04-07
So essentially you have to have an nvidia or ATI to use Unity how lame

---

### Post by cariboo on 2011-04-07
> **wsonar said:**
> So essentially you have to have an nvidia or ATI to use Unity how lame

No Unity works even better with most recent intel graphics, I just did a fresh install on my netbook with 945 chipset, Unity works out of the box without having to add extra drivers. Even Plymouth works properly at startup, and shutdown.

This install is quite a bit faster than my crufty install from January.

---

### Post by monza on 2011-04-08
I have a problem with video playback on Natty beta, with fglrx and VLC. If i activate tear-free in CCC's settings i do not get tearing but the video feels sluggish and slow...if i turn off tear free, the video is snappy and smooth but i get tearing...i tried messing with various settings in compiz and VLC but without results (if i turn on sync to vblank in compiz it also feels slow/sluggish....) Thanks for any idea.

---

### Post by jfernyhough on 2011-04-08
> **monza said:**
> I have a problem with video playback on Natty beta, with fglrx and VLC. If i activate tear-free in CCC's settings i do not get tearing but the video feels sluggish and slow...if i turn off tear free, the video is snappy and smooth but i get tearing...i tried messing with various settings in compiz and VLC but without results (if i turn on sync to vblank in compiz it also feels slow/sluggish....) Thanks for any idea.It's not us, it's them. As far as I know this us a known issue with 11.3 and the 11.4 pre-release.

---

### Post by rajeev1204 on 2011-04-08
> **monza said:**
> I have a problem with video playback on Natty beta, with fglrx and VLC. If i activate tear-free in CCC's settings i do not get tearing but the video feels sluggish and slow...if i turn off tear free, the video is snappy and smooth but i get tearing...i tried messing with various settings in compiz and VLC but without results (if i turn on sync to vblank in compiz it also feels slow/sluggish....) Thanks for any idea.


You need to turn off the vsync for now in both compiz opengl settings and in fglrx according to the devs  to see if it works faster.
[https://bugs.launchpad.net/ubuntu/natty/+source/fglrx-installer/+bug/748137](https://bugs.launchpad.net/ubuntu/natty/+source/fglrx-installer/+bug/748137)

Right now my biggest problem > firefox stops responding and none of the tabs respond to clicks until i minimise firefox and bring it back again.

---

### Post by jfernyhough on 2011-04-08
> **rajeev1204 said:**
> You need to turn off the vsync for now in both compiz opengl settings and in fglrx according to the devs  to see if it works faster.
[https://bugs.launchpad.net/ubuntu/natty/+source/fglrx-installer/+bug/748137](https://bugs.launchpad.net/ubuntu/natty/+source/fglrx-installer/+bug/748137)

Right now my biggest problem > firefox stops responding and none of the tabs respond to clicks until i minimise firefox and bring it back again.
This may be due to having mipmaps enabled in the various Compiz plugins (I know of static switcher and expo). For me it causes windows to be appear unresponsive, though clicks still register.

---

### Post by rajeev1204 on 2011-04-09
> **jfernyhough said:**
> This may be due to having mipmaps enabled in the various Compiz plugins (I know of static switcher and expo). For me it causes windows to be appear unresponsive, though clicks still register.


Same here,clicks register but i dont see it unless i minimise firefox or do something else then refocus it.

---

### Post by Cam! on 2011-04-09
I haven't checked up on Ubuntu or this specific topic in a while.

Has it been fixed? Can I install the proprietary drivers for my Radeon HD 6850 on Ubuntu 11.04?

---

