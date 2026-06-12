---
title: "Ubuntu doesn't display 1280x1024 on new LCD TV"
date: 2008-05-29
forum: Multimedia Software
---

### Post by ssjwolf on 2008-05-29
Hi,

Sorry if this has been asked before, I'm still new to Linux/Ubuntu. 

I got this new LCD TV for my Ubuntu box (generic cheap brand, manual doesn't say much for specs), and I cannot display its maximum resolution of 1280x1024. I've messed around with the xorg.conf file, "dpkg-reconfigure xserver-xorg", as well as downgrading the xserver-xorg. Nothing seems to work thus far, though it should be taken into consideration that I "may" have done the above incorrectly. Any suggestions?

Basic specs for the Ubuntu box:

Pentium 4 2.4GHz
Intel D865GLC mATX
512MB DDR
Onboard 865G Graphics
Onboard SoundMAX4

Thanks to all.

---

### Post by agreppi on 2008-05-29
Have you tried setting the subsection Display in XXXX like this:

SubSection "Display"
Depth 24
Modes "1280x768" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection

Also, have you add the HorizSync values in the Monitor section, like this:

Section “Monitor”
...
HorizSync 30-70
EndSection

There's an excelent tutorial to fix this, but it's in Spanish. In case you speak Spanish, here it is:
[]("http://mamelonsetigero.wordpress.com/2007/06/08/el-raro-problema-de-la-resolucion-en-ubuntu/")
The comments here are also helpful.

By the way, you said that it is a LCD TV. Do you mean that you will use it a Monitor, and also watch TV like in a regular set?

---

### Post by agreppi on 2008-05-29
The URL didn´t appear. Here it goes again:

[http://mamelonsetigero.wordpress.com/2007/06/08/el-raro-problema-de-la-resolucion-en-ubuntu/]("http://mamelonsetigero.wordpress.com/2007/06/08/el-raro-problema-de-la-resolucion-en-ubuntu/")

---

### Post by JEDIDIAH on 2008-05-29
> **ssjwolf said:**
> Hi,

Sorry if this has been asked before, I'm still new to Linux/Ubuntu. 

I got this new LCD TV for my Ubuntu box (generic cheap brand, manual doesn't say much for specs), and I cannot display its maximum resolution of 1280x1024. I've messed around with the xorg.conf file, "dpkg-reconfigure xserver-xorg", as well as downgrading the xserver-xorg. Nothing seems to work thus far, though it should be taken into consideration that I "may" have done the above incorrectly. Any suggestions?

Basic specs for the Ubuntu box:

Pentium 4 2.4GHz
Intel D865GLC mATX
512MB DDR
Onboard 865G Graphics
Onboard SoundMAX4

Thanks to all.

1280x1024 doesn't sound like a proper resolution for a new TV.

Perhaps you should be trying something like 1280x720?

Check your Xorg log in /var/log. See what resolutions and modelines
are being autodetected when X starts up. You can also look at MythTV
wiki at mythtv.org and see if your TV is in their modeline database.
You can also try standard modelines for different TV standards.

TVs can be tricky and sometimes they broadcast faulty PnP information too.

...also you need to be install/run xserver-xorg-video-intel. You have to
install device specific "drivers" as well as the main packages for X.

Dunno if the 865G is too new or not. I run 945s myself.

---

### Post by ssjwolf on 2008-05-29
**@agreppi** - Yes I did try that initially, but it didn't seem to work, maybe I just did it wrong. But thank you anyway.

**@JEDIDIAH** - Yeh well it has got a VGA input, so I suppose 1280x1024 isn't that strange, right? The Intel drivers seem to be installed right in Synaptic.

But anyway thanks for the suggestions, but it seems I managed to fix it by deleting the xorg.conf file, rebooting, and getting that low-resolution mode configuration screen. Seems to work great now. :D

---

### Post by JEDIDIAH on 2008-05-30
> **ssjwolf said:**
> **@agreppi** - Yes I did try that initially, but it didn't seem to work, maybe I just did it wrong. But thank you anyway.

**@JEDIDIAH** - Yeh well it has got a VGA input, so I suppose 1280x1024 isn't that strange, right? The Intel drivers seem to be installed right in Synaptic.

But anyway thanks for the suggestions, but it seems I managed to fix it by deleting the xorg.conf file, rebooting, and getting that low-resolution mode configuration screen. Seems to work great now. :D

It's a TV, not a monitor. You can't expect it to support resolutions
and refresh rates that aren't part of some national broadcast standard.
Now every panel can be different. You can't really assume anything. My
last panel supported 1280x720 pretty easily but my current panel won't
do anything by "normal" resolutions through the VGA. 

So I use DVI->HDMI these days.

With my old SD set, I can get 640x480 through DVI->svideo just by letting
Xorg sort itself out on it's own.

Both TV's are connected to machines that run MythTV.

---

### Post by ubuntu-freak on 2008-05-30
Just to let you know, you can set resolutions in Hardy with:
 
**sudo xrandr -s 1280x1024** 
 
If that doesn't work, enter this command:
 
**sudo xrandr -q** 
 
Have a look to see what the highest resolution supported is, try that, then once that's set, try setting the resolution you know should work with your screen.
 
Nathan

---

