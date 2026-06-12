---
title: "Natty S video to TV not working"
date: 2011-04-17
forum: Multimedia Software
---

### Post by Hekla on 2011-04-17
This is an Acer Aspire 5720, with a "Mobile GM965/GL960 Integrated Graphics Controller". Although I initially though this was a problem with my installation, so I ran both the Maverick and recent Natty live cds and the s video out only functioned on the Maverick cd.

The computer acts as if there is another monitor, but the TV does not display one. I am not sure how to go forward, having little knowledge of the display options.

---

### Post by marioangler on 2011-04-19
Hello All. Im having the same problem with my DELL Latitude. I had Ubuntu 10.10 for some 6 months and the S-video out to TV had been working great. I am an above average user  but no computer programer, so here is my problem:  when I updated to 11.04 through the synaptic manager everything  worked except s-video out, this BUMS because I cant watch my "You Baby  can Read" videos with my son on the big tv. I hate the fact of having to  use the windows partition again after I explained to my wife how  wonderful Natty Narwhal would be :(, but I know its fixable 'cause it  used to work.

A few details that might give clues to the ones who know:  On Function+F8 the laptop screen does change resolution like before but  the TV screen goes black. If I Function+F8 again for a brief second  there you can see the computers desktop background in the TV but then it  goes black again and the laptop return to full 1600 X 1200 display.   Like our friends here stated, the monitor or display manager does seem to recognize a s-video out  connection because its clickable and I can change display sized, but the  tv screen is just black, except for when, like I said before, click FN +  F8 and for a brief second the desktop bg can be seen on the TV and the  it goes black again.

Im at work right now so will try to post the config specs later today,  any help is greatly appreciated. Im REALLY looking forward to proving my  wife wrong by making this work.  :)

---

### Post by voodoostevie on 2011-04-28
I also am having this issue. Both with an upgrade and a clean install. 

With me in the Monitors preferences it shows the second "monitor" when I have my S-Video plugged in but nothing on the TV but static (I am using a modulator connected to a switch because I switch devices on the TV (gaming consoles, DVD, Satellite Receiver) constantly). 

Looking the issue up via Google search it comes up with some odditties with external monitors under Natty. More like panel issues or resolution issues. With those it looks like some think it's something with the intel driver for X, and others are pointing fingers at Compiz with the issue. The [bug in launchpad]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/723002") also seems more of the oddities of external monitors and not SVid ports not functioning anymore.

What I don't get is under Maverick and previous releases (Lucid, Karmic, etc.) I was using Compiz and the S-Vid out worked fine with my Acer 5720Z. why all of a sudden with this release it doesn't work?

Should we create a new bug in Launchpad?

---

### Post by voodoostevie on 2011-04-29
This [bug report]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/763688") is definitely the right one. Seems like an issue with xserver-xorg-video-intel.

If you see any changes or updates to this, please keep us posted. ;)

---

### Post by wishnoo_84 on 2011-04-29
I have the same problem. The S-video to TV was working fine in earlier version of ubuntu. I have submitted  the system test logs hoping they will be useful

---

### Post by wishnoo_84 on 2011-04-29
[http://ubuntuforums.org/showthread.php?p=10739558](http://ubuntuforums.org/showthread.php?p=10739558)
Looks like this is solved here.

---

### Post by Beanmonster on 2011-05-03
I'm having the same issue here...

---

### Post by voodoostevie on 2011-05-03
> **Beanmonster said:**
> I'm having the same issue here...

Is your graphics card an Intel based chipset? If you are not sure you may want to look at the specifications of your computer if it is an Intel based graphics card, the best thing to do is to mark this bug as affecting you. The more people reporting the bug the quicker it gets noticed :) : 

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/763688]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/763688")

It seems the intel video driver itself is the main issue. Haven't seen it being mentioned with anything but that. 

The workaround mentioned earlier may only work with upgrades from 10.10 to 11.04 but for those of us that do clean installs or are new users of Ubuntu will be doing a clean install which the workaround may not work.

This isn't affecting JUST Ubuntu (Unity default) or Ubuntu Classic, but Kubuntu as well from what I can see with trying it with both the live CD and an install on a separate partition. 

This issue is my #1 reason to not upgrade to natty at the moment because I use the S-Video to watch videos off my laptop with my daughter and the rest of the family as well.

---

### Post by MFaughn on 2011-05-13
ditto that with the family TV thing.  _Really_ annoyed by this.  Do you have any idea how serious it is when a five year old can't watch his daily ration of Scooby Doo?  the horror.

---

### Post by voodoostevie on 2011-05-15
This is definitely an issue with XORG's update drivers. I don't know if it's just the INTEL driver or if some of the others are also having the same issue. But it looks more based on the Intel driver at the moment. 

This being said, it's not just Ubuntu and it's forks and derivatives that are affected. I checked out Fedora 15 Beta and it's having the same issue. I was thinking of giving LinuxMint 11 a shot but the latest RC is based on Ubuntu 11.04 which most likely will have the same issue as well.

If this all is based on the XORG Intel driver, than even switching distros with the latest version drivers will be a mute point. Unfortunately it makes people hold off on updating to the latest version of any distro if one primary thing they use is not looked into. 

The bug on launchpad is still Unassigned at this moment, yet it's been marked as a medium priority. Until more people report it, I think it will be an even longer time before anyone affected by this bug will be going to Natty.

---

### Post by joeoshawa on 2011-05-21
this bug is affecting me as well. Thank god i didn't' upgrade my main box cause i just installed it on a  pc i just picked up got with an ASUS v7100pro 64m video card and the only monitor i have is a 43 inch tv with only rca or svideo. I do EVERYTHING in linux quite literaly. all my appointments are in evolution, its how everyone (including my lawer) gets a hold of me, and my only source of entertainment since its my htpc as well.  Hope they get it sorted soon.

---

### Post by darkwolfalone on 2012-06-21
So was this ever resolved? I held off on upgrading for this very reason before recently installing Xubuntu 12.04, however it seems this bug has not yet been fixed! S-Video with an Intel Chipset works fine on Ubuntu 10.10 but will not display anything on the TV in 12.04, despite detecting the TV. Unfortunately, I did not save my Xorg file from 10.10.

HELP!!!

---

### Post by joeoshawa on 2012-06-21
Unfortunately I have no idea, the computer it was on is no longer functioning and I no longer use ubuntu.

---

