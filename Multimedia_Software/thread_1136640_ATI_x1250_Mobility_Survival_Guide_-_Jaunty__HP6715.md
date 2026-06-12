---
title: "ATI x1250 Mobility Survival Guide - Jaunty / HP6715b"
date: 2009-04-25
forum: Multimedia Software
---

### Post by drplix on 2009-04-25
The following hard won information might help someone else out.  Installed Jaunty on a HP Compaq 6715b with ATI x1250 mobility chip. (Previously I was running Hardy with ATI propietary fglrx catalyst 9.3 driver - never had 3D compiz work well so was living with 2D - put this down to crappy ATI chip).

Didn't expect any problems with the migration to Jaunty since this chip has been around for a couple of years. Wrong.  After a clean install the display is operating in 3D with compiz. I guess its chosen the open source ATI x.org driver.  *But* this gives horrible screen breakup / flicker when moving a window or scrolling etc with occasional random blocks of other windows flickering in the wrong place.  All together completely unusable.  Tried switching from compiz to metacity but still see the same artifacts so its not just the 3D.

Tried installing xserver-xorg-video-radeonhd  - but this is even worse - X refuses to start and machine crashes completely.

So I thought "OK back to proprietary fglrx". But it turns out that ATI last month dropped support for "older" chips in the catalyst 9.4 driver. Worse yet the perfectly functional 9.3 package refuses to install on Jaunty - version mismatch!  [Now the x1250 is not a high-end chip but its not old and its used in a lot volume to mid-range platforms - seems like ATI doesn't give a damn about this market! Note to self: never buy ATI platform again its been a complete pain in neck.]

OK so now I'm getting desperate - have done a full rebuild of my machine - had a perfectly functional 2D desktop Hardy installation - but Jaunty is between stools for this graphics chip no 2D or 3D - open source is not ready and ATI has abandoned us.

Searched and searched and finally tripped over this...

[http://www.phoronix.com/forums/showpost.php?p=32602&postcount=1](http://www.phoronix.com/forums/showpost.php?p=32602&postcount=1)

This fella has current builds of the radeon and radeonhd x.org drivers.  Thank you!!!

Follow the instructions to add the repository.  Then install with

sudo apt-get install xserver-xorg-video-radeonhd

Reboot and you'll have working flicker free 2D X again.

Be warned that the radeon driver gives you 3D but it still has the same flicker issues.

Hope this helps someone.   Maybe one day I'll get a 3D desktop ;-(

---

### Post by Renan Decarlo on 2009-04-26
Same problem here with my X300... I installed xserver-video-radeonhd too, but not i can't even turn on my computer :( (typing from windows mom's computer)...

I'm going to try to get my machine back and then try to install this new build you offered... thanks

---

### Post by thisweb on 2009-04-26
Newbee with a question re atix1250 if this is the right place...

I have the open drivers working fine on jaunty with my x1250 and 19inch monitor but when I connect HDMI to TV - display settings says the TV is Toshiba 47 inch but it is only a toshiba 42 inch so the resolutions available don't work -the image is all weird.  Does anyone know if there is a way to force the resolution and bypass the monitor detection settings.  It worked fine with the proprietry driver in Ubuntu8.10.  If not It looks like I'll have to switch  to windows 7 - i love ubuntu but ATIs not going to do drivers for this card now so if i can't fix it I'm lost.  Its only 1 year old too.

Any help would be great.  Or could someone point me in the right direction.

Many thanks

---

### Post by nibbana84 on 2009-04-26
> **drplix said:**
> The following hard won information might help someone else out.  Installed Jaunty on a HP Compaq 6715b with ATI x1250 mobility chip. (Previously I was running Hardy with ATI propietary fglrx catalyst 9.3 driver - never had 3D compiz work well so was living with 2D - put this down to crappy ATI chip).

Didn't expect any problems with the migration to Jaunty since this chip has been around for a couple of years. Wrong.  After a clean install the display is operating in 3D with compiz. I guess its chosen the open source ATI x.org driver.  *But* this gives horrible screen breakup / flicker when moving a window or scrolling etc with occasional random blocks of other windows flickering in the wrong place.  All together completely unusable.  Tried switching from compiz to metacity but still see the same artifacts so its not just the 3D.

Tried installing xserver-xorg-video-radeonhd  - but this is even worse - X refuses to start and machine crashes completely.

So I thought "OK back to proprietary fglrx". But it turns out that ATI last month dropped support for "older" chips in the catalyst 9.4 driver. Worse yet the perfectly functional 9.3 package refuses to install on Jaunty - version mismatch!  [Now the x1250 is not a high-end chip but its not old and its used in a lot volume to mid-range platforms - seems like ATI doesn't give a damn about this market! Note to self: never buy ATI platform again its been a complete pain in neck.]

OK so now I'm getting desperate - have done a full rebuild of my machine - had a perfectly functional 2D desktop Hardy installation - but Jaunty is between stools for this graphics chip no 2D or 3D - open source is not ready and ATI has abandoned us.

Searched and searched and finally tripped over this...

[http://www.phoronix.com/forums/showpost.php?p=32602&postcount=1](http://www.phoronix.com/forums/showpost.php?p=32602&postcount=1)

This fella has current builds of the radeon and radeonhd x.org drivers.  Thank you!!!

Follow the instructions to add the repository.  Then install with

sudo apt-get install xserver-xorg-video-radeonhd

Reboot and you'll have working flicker free 2D X again.

Be warned that the radeon driver gives you 3D but it still has the same flicker issues.

Hope this helps someone.   Maybe one day I'll get a 3D desktop ;-(

I do not understand this. I have X1400 and 3D works perfectly in Jaunty with open drivers. The problem is that S-video out does not work...

---

### Post by thisweb on 2009-04-26
ATI HDMI/Hi-power graphics problems have been around forever in Ubuntu/linux (and now windows) its just becoming a joke (thats mostly down to ATI not ubuntu of course).  There are a lot of small cheap media centre /barebones  pcs with integrated ATI graphics with built in HDMI ports -Ideal for linux/ubuntu/mythbuntu media centre setup but there seems to be very little progress with HDMI software compatibility, especially with ATI cards. (both linux and windows)  The card manufacturers are mostly responsible for this but this kind of user  should be a real focus for development.  Cheap low end computers will only really run Linux well and there are some great open source media centre softwares that work in linux . XBMC is superb with the right skins.  These small cheap setups are becoming more and more popular and are likely to surpass the rise in popularity of low powered netbooks, also very Linux friendly.

I an't stress enough to newcomers that I really think they should avoid buying an ATI over NVIDIA where you have the choice.  ATI have stopped support for loads of cards for Linux (and windows) since the Jaunty release. Their drivers have always been poor alpha quality since as long as I can remember.  In fact I don't think any of their cards/drivers worked properly before they were phased out of production.  Now as of this month, unless you have a top end card your stuck with old software I'm afraid - and the list is big:

 [http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English](http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English) 

Nvidia aren't exactly ace but they are miles ahead with compatibility issues and addressing bugs compared to AMD/ATI.

Keep up the good work.  Open source drivers are an absolute must for a good PC.  I suspect a good open source driver hinders the marketing of new hardware just as linux does for marketing new pcs.  My old pcs with new linux always out perform modern windows pcs except for the 3d graphics cause of the closed source restrictions!

;-)

---

### Post by JeSTeR7 on 2009-04-27
The problem is apparently in the timing when the CPU is at a low frequency.  [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/351291](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/351291)

There is a pretty nice workaround I'm currently using listed on the bug report.

While the listed fix using the sysfsutils package cuts the flickering down to a manageable level, it's hard on battery life since the CPU is running higher most of the time.

---

### Post by drplix on 2009-04-28
Thanks for pointing this out.  Its certainly the bug I'm seeing.

I switched back to the radeon driver and tried the workaround CPU scaling fix...

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/351291/comments/5](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/351291/comments/5)

This does seem to improve things but still get flicker/breakup.

Hopefully this bug gets some attention and we, the "ATI-condemned", can move forward.

---

### Post by drplix on 2009-04-28
Here's my temporary workaround.  Switch to the radeon open source driver.

apt-get install sysfsutils

then edit /etc/sysfs.conf

put in the following lines...

devices/system/cpu/cpu0/cpufreq/scaling_governor = ondemand
devices/system/cpu/cpu0/cpufreq/scaling_min_freq=1600000

Now the CPU stays at 1.6GHz as its minimum which seems to give bearable results with the radeon driver - I even have an ok 3D desktop.

---

### Post by flip09 on 2009-04-30
another workaround:

I turned off compiz' desktop effects and switched from the EXA acceleration method to the XAA method. Added the following line in the device section of my xorg.conf:

Option        "AccelMethod"    "XAA"

gives me the same fps in 3d applications and all flickering is gone!!! with compiz you'll still get a flickering screen, so don't forget to turn it off.

works with radeon and radeonhd open source drivers. i'm using the radeonhd one, videos seems to be a little bit faster, but could be imagination ;)

not a perfect solution though! kinda slow in comparison with old fglrx.

btw, i'm also using a hp 6715b. don't want to switch back to ubuntu 8.10, because wlan and energy saving works great in 9.04 now, 8.10 always had problems with these things.

---

### Post by flip09 on 2009-05-03
using the settings i mentioned (and maybe also without them) on a HP6715B, the system temperature sometimes was to high, so jaunty did an automatic shutdown.

don't forget to use powertop to change some settings to fix these problems.

---

### Post by dE_logics on 2009-05-03
Yeah...that guide worked for me too...I'm on ATI x1270...it doesn't even get mentioned on ATI's website so forget the drivers (even for windows).

However considering what pains you have gone through, I'm lucky!...I'm atleast getting 3-d though at 1/5th the pace and very much buggy!...but it is usable.

Lets see what those proprietary drivers can do for me.

---

### Post by drplix on 2009-05-05
Seems like the latest driver build has fixed the problem...

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/351291/comments/19](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/351291/comments/19)

I just tried using these packages (from the repo I mentioned in the first thread post) and all seems to work at lowest CPU setting.

Great stuff!

---

