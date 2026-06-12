---
title: "Journal Page: Fixing NV Gforce 440MX low resolution in GLX &amp; beryl install on Feisty"
date: 2007-04-03
forum: Multimedia &amp; Video
---

### Post by dgrafix on 2007-04-03
I thought i would post this for anyone with a geforce4 mx440 AGP8X who has a fresh copy of feisty and wants to get hardware acceleration going.

PLEASE READ BEFORE FOLLOWING BECAUSE I MADE SEVERAL MISTAKES AND HAD TO BACKTRACK! THIS IS MORE OF A JOURNAL PAGE THAN A HOW TO!

Heres what i did and the problems i encountered.

Installed Ubuntu all fresh and feisty,  

then i followed this: 
[http://ubuntuforums.org/showthread.php?t=357501](http://ubuntuforums.org/showthread.php?t=357501)

and beryl-manager was running a white screen with feint gray windows.

did a glxinfo |grep "direct render"
i was getting direct render :no

not good.

So i do system>admin>restricted drivers and enabled HW support for nvidia-glx BIG MISTAKE!! that crashed Xserver, so had to recover /etc/X11/xorg.conf from failsafe using nano from the backup file.

Booted in again

Then however, i noticed 200 odd updates!! (mabe i should have done these first :)

In  system>admin>restricted drivers  i notice i have now GLX legacy drivers in there now instead.
Enabled that and rebooted.

Now im getting 800x600 only. but with full hardware rendering (although glxinfo does spew a message or two about missing screen 0.0??)
Tried 'beryl-manager' start from terminal and works fine.

Resolution woes:

Couldnt work out why I couldnt get more than 800x600 when my LCD is 1280x1024

Even when i removed every other resolution from the conf file, no joy.

Then i realised it was my MONITOR REFRESH RATE! ARGH the reading i did!
I put in the lines:
This is for a fujitsu siemens C19-6 panel 1280x1024:
	HorizSync	30-75
	VertRefresh	30-65

in section monitor and it works fine now in full res and beryl is wicked :)

---

### Post by tseliot on 2007-04-03
the restricted drivers manager installed driver 9755 which does not support your card (but 9631 does).

You might have to install the driver manually. Follow method 2 of this guide of mine (even if it's for Edgy):
[http://ubuntuforums.org/showthread.php?t=281823](http://ubuntuforums.org/showthread.php?t=281823)

---

### Post by dgrafix on 2007-04-05
Thanks, it seems to work well with the nvidia-glx-legacy drivers (whicever that is) Im not going to poke it any more as its working nice and smooth.
:guitar:

---

