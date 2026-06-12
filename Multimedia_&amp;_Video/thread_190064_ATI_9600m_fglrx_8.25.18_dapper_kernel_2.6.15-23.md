---
title: "ATI 9600m fglrx 8.25.18 dapper kernel 2.6.15-23"
date: 2006-06-05
forum: Multimedia &amp; Video
---

### Post by Vincent_Lin on 2006-06-05
Just to add to the frustration I share with others

I have IBM T42 with 9600 mobile, and I am trying to install fglrx driver, with no success.

I tried both Synaptic fglrx installation first, and failed.  

Then I tried method 2 out of [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

but failed at compiling kernel module (* sudo module-assistant build,install fglrx *), asking me to check up and buildlog file.  I glanced the log file and saw only the warning: 

Warning: could not find /usr/src/modules/fglrx/.libfglrx_ip.a.GCC4.cmd for /usr/src/modules/fglrx/libfglrx_ip.a.GCC4

Obviously aticonfig could not give me any sensible results.

My glxinfo | grep rendering  is a big "no" after restarting the x-server.

I tried the same routine on both 2.6.15-23-386 kernel and 2.6.15-23-686 kernels.
Both failed at the same spot.

However, I did remember I had fglrx driver installed properly once, along with xgl/compiz goodies, while my T42 was still on Flight4 /or 5 status, with 686 kernel.

Frustrated.  Really.

Vincent

---

### Post by lexxonnet on 2006-06-05
hmm... I'm no expert at this... and I'm probably wrong... but did you install linux-restricted-modules ?

---

### Post by KiLLeR_WoMBaT on 2006-06-05
I feel you pain!!!

I too have a 9600 Mobility and cannot get 3D/DRI to work for anything.  I have tried every how-to and suggestion on these forums over the last three days and I get nothing.  Everything goes great and installs fine (so it seems...no errors) and upon reboot I get two drum sounds at the login screen instead of one.  Upon login I get just a blank brown screen with my cursor and that is it.

The only way to recover is to ctrl-alt-bkspc back to the login screen and do a failsafe terminal login and dpkg-reconfigure xserver-xorg to change the xorg.conf file driver back to VESA.  Then everything will login fine...but still with MESA and no DRI or 3D.

What is the deal?  Hopefully someone will have insight to what we are doing wrong (even though I have followed everything suggested to the letter and even re-installed Dapper TWICE); or how to fix/work around the bug.

---

### Post by DonQuixote on 2006-06-08
Same here.  ATI 9600 Radeon Mobility.

I tried installing the v8.19.10 ATI driver that worked with Breezy, but got an incompatibility error.  xorg 690 was needed for this driver.  Evidently 700 is installed with Dapper.  I tried the v8.24.8 AND the v8.25.18 drivers with no luck.

Any insight would be greatly appreciated.

---

### Post by DarthGroznii on 2006-06-08
I tried the driver supplied in the repositories and then the driver from ATI's site for my ATI Radeon Mobility 9200.  No luck - just a black screen.

The "ati" driver works all right - I await ATI to release a proper driver so I can actually do 3D acceleration.

---

### Post by Vincent_Lin on 2006-06-08
Hi Guys,

Check out this thread:

[http://ubuntuforums.org/showthread.php?t=191944](http://ubuntuforums.org/showthread.php?t=191944)

I have fglrx and xgl/compiz installed now.

Vincent

---

