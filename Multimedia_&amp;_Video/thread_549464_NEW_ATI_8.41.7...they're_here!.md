---
title: "NEW ATI 8.41.7...they're here!"
date: 2007-09-12
forum: Multimedia &amp; Video
---

### Post by carpex on 2007-09-12
Hello, I am downloading the new ATI drivers  8.41.7, which are supposed to increase very significantly the performance on Linux ([http://www.phoronix.com/scan.php?page=article&item=821&num=1](http://www.phoronix.com/scan.php?page=article&item=821&num=1)). Tell me if you try them. I'll try them on my x1400.

EDIT: From the ATI site: "The AMD Proprietary Linux driver version 8.41 is recommended for the ATI Radeon&#8482; HD 2000 family only". So use at your own risk for other cards. 

Release note: 
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.41.7.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.41.7.html)

Installer instructions:
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.41.7-inst.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.41.7-inst.html)

Driver installer:
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8.41.7-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8.41.7-x86.x86_64.run)

Cheers, 

CP

---

### Post by carpex on 2007-09-12
Well, I can't say I wasn't warned. Anything that uses opengl results in a segmentation error for me (x1400 card). Compiz-fusion works fine however. 

$glxgears
segmentation fault (core dumped)
$neverball
segmentation fault (core dumped)
$glxinfo
name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
segmentation fault (core dumped)

:(

I guess I'll have to wait for the 8.42 and AIGLX...

CP

---

### Post by Yellow Pasque on 2007-09-12
Broke my box (with a X1250 Xpress integrated into an AMD 690G chipset)

Gnome display manager won't start now :(

---

### Post by sloggerkhan on 2007-09-12
I must be lucky... it seems to be working fine on my x700 mobility for Enemy Territory and such.

Actually, the only 2 glitches I've noticed are that I can no longer change resolution ingame and that the catalyst control center always gives a message that "you must restart your computer for changes to take effect" after they've already been applied.

---

### Post by rbmorse on 2007-09-13
Works on Kubuntu Feisty with my X1950XTX, but not on Gutsy. Rumor is the new ATI driver doesn't like Xorg 7.3. 

The not-a-benchmark glxgears loses about 1000 fps (from 11500 to 10500) with the new driver.  Could be user error.  

The KDE control center reports the driver in use is ATI Radeon fbdev.  There is an ATI Radeon fglrx driver, but selecting that one and restarting X results in a blinking cursor but no desktop. Fixing that requires the xserver reconfigure routine. 

Image quality good.  Fonts good. colors vibrant.  Stable, except closing an OpenGL window leaves an artifact.

---

### Post by Barbosas on 2007-09-13
> **sloggerkhan said:**
> I must be lucky... it seems to be working fine on my x700 mobility for Enemy Territory and such.

Actually, the only 2 glitches I've noticed are that I can no longer change resolution ingame and that the catalyst control center always gives a message that "you must restart your computer for changes to take effect" after they've already been applied.

Hi!

how did you make the drivers work?
i can't seem to make them work on my x700 mobility.

i execute the .run, it all goes OK, but i after i just get segmentation fault when running fglrxinfo or glxgears.

---

### Post by fizz on 2007-09-13
im gonna attempt to install these on my macbook pro here after im done fixing my bosses laptop.. :)

---

### Post by sloggerkhan on 2007-09-13
I downloaded the file from [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.41.7-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.41.7-x86.x86_64.run)
I then allowed it to be executable and ran from terminal $sudo ./DRIVERNAME
Did a $dpkg-reconfigure xserver-xorg with the new driver after rebooting, and have been good to go since, outside of the minor issues I mentioned.

If I were to be correct about it, I probably should have purged the old driver first, but whatever. Also, I'm on feisty, not gutsy.

---

### Post by NoVista on 2007-09-14
Installed right over the last version without a hitch.
Downloaded, installed, rebooted, brought up ATI Control Center.
Everything properly identified.

Re-installed Google Earth, runs great, no software emulation needed now.

Running Feisty, ATI AIW x800XT

Had to laugh a bit when I noticed ATI/AMD put the Control Panel right on the Main Menu.
C'mon guys, stick it under System Tools or under a sub-folder. After all, this ain't Windowz. Guess the techs still need a bit more training from us all.:)

---

### Post by sloggerkhan on 2007-09-14
It might be there because they 'officialy' support only Fedora and Suse, which have different menu layouts than ubuntu.

---

### Post by Nem1976 on 2007-09-14
Well it looks like the driver is currently designed for the R600 cards while it does work with older cards there are some corruption issues. 

I will wait until they officially release them for the R500 and older cards before installing it.

---

### Post by mbvlist on 2007-09-14
> **carpex said:**
> Well, I can't say I wasn't warned. Anything that uses opengl results in a segmentation error for me (x1400 card). Compiz-fusion works fine however. 

$glxgears
segmentation fault (core dumped)
$neverball
segmentation fault (core dumped)
$glxinfo
name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
segmentation fault (core dumped)

:(

I guess I'll have to wait for the 8.42 and AIGLX...

CP

That's my problem too, after having these drivers installed. Weirdest thing: I de-installed them (because the module couldn't be loaded, maybe user error), and reverted to the radeon-drivers I used to use. Now everything still gives me a segfault :( Seems like they messed up some liberaries...  ](*,) And I really need 3d, even if it is software rendered, for some assignment I have to make :mad:
Seems like I was over-greedy for the performance advantage :(

Has anybody got an idea what might have caused this problem? I first tried the 'regular' installer, without the .deb step in between.

---

### Post by carpex on 2007-09-14
@ mbvlist: What I did is to uninstall the new drivers and re-install the 8.40.4 fglrx drivers and everything is back to "normal" (real old ATI normality). I guess I can wait a month for the new drivers, hopefully just in time for my switch to Gutsy.

CP

---

### Post by mbvlist on 2007-09-15
> **carpex said:**
> @ mbvlist: What I did is to uninstall the new drivers and re-install the 8.40.4 fglrx drivers and everything is back to "normal" (real old ATI normality). I guess I can wait a month for the new drivers, hopefully just in time for my switch to Gutsy.

CP

I reInstalled mesa, and now used the official way to install the drivers (use the apt-package, build kernel-module using module-assistant) and it still didn't work. It seems like the linux restricted modules-package is messing around with things: it mounts /lib/modules/..../volatile as tempfs, and copies all .ko files from /lib/linux-restricted-modules. Unfortunately, that's not where module-assistant puts them. If I manually make a symlink from /lib/modules/.../misc, it works :)

Now find a way to do that automatically on reboot :(

---

### Post by revchris on 2007-09-15
Everything seems fine on my card except the ATI Catalyst Control Center from the menu doesn't do anything.:confused:

---

### Post by NoVista on 2007-09-15
It doesn't? What card do you have?

---

### Post by Manible on 2007-09-15
Will this driver work with an x1100 integrated card?

---

### Post by cmat on 2007-09-15
I desperately need the drivers, but I'm going to wait for it to go into the repos. Installing these things are tricky.

---

### Post by Leftwing Pinko on 2007-09-16
I noticed that there is support for the Radeon HD 2600 card, but I'm wondering if that includes the mobility series or not? I've got a laptop with an ATI Mobility Radeon HD 2600 card...

---

### Post by mbvlist on 2007-09-16
> **Leftwing Pinko said:**
> I noticed that there is support for the Radeon HD 2600 card, but I'm wondering if that includes the mobility series or not? I've got a laptop with an ATI Mobility Radeon HD 2600 card...

It's not that hard, I would give it a shot (certainly if you don't have any hardware-support right now). 
Follow this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)
You probably will find some problems with getting the right version of fglrx.ko in volatile (the ln -s statement), but you can at least try to see if the driver works.

---

### Post by revchris on 2007-09-16
> **NoVista said:**
> It doesn't? What card do you have?

ATI Radeon Mobility X600

---

### Post by l3iggs on 2007-09-24
> **carpex said:**
> Well, I can't say I wasn't warned. Anything that uses opengl results in a segmentation error for me (x1400 card). Compiz-fusion works fine however. 

$glxgears
segmentation fault (core dumped)
$neverball
segmentation fault (core dumped)
$glxinfo
name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
segmentation fault (core dumped)

:(

I guess I'll have to wait for the 8.42 and AIGLX...

CP
Sucks, I'm having the exact same problem too. :(

---

