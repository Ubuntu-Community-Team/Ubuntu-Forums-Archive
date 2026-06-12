---
title: "ATI 8.1 Drivers -- Post Your results"
date: 2008-01-18
forum: Multimedia &amp; Video
---

### Post by NoVista on 2008-01-18
Anyone install these yet?
Who will be first?

---

### Post by hedgebox on 2008-01-19
I installed them quite easily. Direct rendering and all worked without any tinkering. Hibernate /suspend does not for me (IBM Thinkpad T60). My graphics card is the Mobility X1400 and I am using Ubuntu 7.10. I also have not been able to get compiz to work with it yet.

---

### Post by rcmn on 2008-01-19
Just tried it.That was amazingly easy .removed the old  8.1 . build the  fglrx*.deb installed the new fglrx*.deb restarted X and it worked .
 My ati 9800 pro with my 1.680x1050 resolution welcomed me . Now i don't have the screw up 1600x1200 resolution.I can clearly see ,for the first time, the new KDE4 nice and clean.
Impressive ... what am i going to do this week end?... humm enjoying lifeeee.

---

### Post by daniel of sarnia on 2008-01-19
The driver is 8.01, not 8.1 which would be the tenth driver of 2008. The same way ubuntu is numbered.

Anyways I tried, compiz works well and my resolution is right, 1680x1050. But video playback acceleration is still essentially broken and some 3D apps don't work ie. quake 4. Back to 8.40.3 for me... At least the open source driver is making good progress.

---

### Post by sloggerkhan on 2008-01-19
Seems to work for me.
I haven't tried suspend or hibernate.
Works well in games, it seems.
Haven't tried with compiz-fusion, my dual monitors are too high res to run it unless I use clone mode.
However, I think my video playback has stopped working.

---

### Post by samase on 2008-01-19
HD2600PRO AGP doesn't work. still i get black screen. does anyone know if it is even supposed to work with AGP???

---

### Post by samase on 2008-01-19
here it says that it should work... has anyone got hd2600pro agp working?

[http://ati.amd.com/products/catalyst/linux.html](http://ati.amd.com/products/catalyst/linux.html)

and here:
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat81-inst.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat81-inst.html)

it says:

"If a Linux 2.6.11 or newer kernel was built with CONFIG_AGP enabled, the kernel AGP frontend is required to load the fglrx kernel module. To identify whether your kernel was built with CONFIG_AGP enabled, look for CONFIG_AGP=y in the kernel config file, or if the 'agpgart' module loaded."

 grep CONFIG_AGP .config 
CONFIG_AGP=m
CONFIG_AGP_INTEL=m
CONFIG_AGP_ALI=m
CONFIG_AGP_AMD=m
CONFIG_AGP_AMD64=m
CONFIG_AGP_ATI=m
CONFIG_AGP_EFFICEON=m
CONFIG_AGP_NVIDIA=m
CONFIG_AGP_SIS=m
CONFIG_AGP_SWORKS=m
CONFIG_AGP_VIA=m

is this ok?

in the xorg.0.log i get:
Fatal server error:
Caught signal 11.  Server aborting

(II) AIGLX: Suspending AIGLX clients for VT switch

---

### Post by sloggerkhan on 2008-01-19
> **sloggerkhan said:**
> Seems to work for me.
I haven't tried suspend or hibernate.
Works well in games, it seems.
Haven't tried with compiz-fusion, my dual monitors are too high res to run it unless I use clone mode.
However, I think my video playback has stopped working.

update: Only opengl video output seems to work.
This sucks for me because with 2 1680x1050 monitors, I can't seem to get full screen video on the right hand monitor with the opengl video driver. 
I think I need a way to move the opengl overlay to screen 1 instead of screen 0, maybe.

PS: man aticonfig is now missing.
Anybody have a link or know where documentation is available online?

Oh, and one last note: 
ctrl-alt-bkspc freezes the computer now, for some reason.

---

### Post by samosamo on 2008-01-19
I installed using the wiki's guide (not Envy this time) and here's my results:
Anything Before 7.12 - Incompatible with Gutsy kernel's power management
Catalyst Drivers 7.12 - couldn't do my native res 1280x768
Catalyst Drivers 8.10 - Suspend works, and my resolution is working

I'm pretty happy.  My full screen video is still choppy as addressed by this thread: [http://ubuntuforums.org/showthread.php?t=671811](http://ubuntuforums.org/showthread.php?t=671811)  Can anyone offer any advice ?

---

### Post by sloggerkhan on 2008-01-19
Try
a) turning off compiz
b) using opengl overlay
(xv seems broken with this release)

Oh, and with opengl video overlay, only hard coded subtitles seem to work.

---

### Post by NoVista on 2008-01-19
Ahhhh .. 
It all sounds like another month with a BIG dissapointment then.

---

### Post by frogotronic on 2008-01-19
**BASIC INSTALL QUESTION:**

I installed Gutsy and then followed this [guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_7.12_Driver_Manually") to install 7.12 drivers.

_I'd like to upgrade to the 8.1 (or 8.01) drivers._

**Door #1)** Do I just download the 8.1 package and follow the same guide, overwriting my 7.12 debs?

or

**Door #2)** Manually uninstall the 7.12 debs, and use the same method to build new debs for the 8.1 package and then install them?

or

**Door #3)**  Remove my 7.12 debs, download ATI's new [autoinstaller]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat81-inst.html") and use it?

or

**Door #4)**  Download and run ATI's new installer and run it (assuming it will overwrite the old 7.12 debs)?



Which door do I choose?


Thanks in advance,
CH

---

### Post by idanool on 2008-01-19
how do I install the new 8.1 driver on gutsy?
is it possible throw "Restricted Driver Manager" or manually?
do I need to use the guide on :[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide) ?
what driver will be installed if I use  "Restricted Driver Manager"?

thanks.

---

### Post by owhno on 2008-01-19
I installed ATI 8.1 last night. 
Installation is the same as 7.12 if you have it installed dont bother to delete something just install the new one.
cchtml is update so head over to [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.1_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.1_Driver_Manually)

And install it

if you have 7.12 installed then in my case it was installed with these commands

```
sh ati-driver-installer-8-01-x86.x86_64.run --buildpkg Ubuntu
sudo rm /usr/src/fglrx-kernel*.deb (didnt have files there but to be sure)
sudo dpkg -i xorg-driver-fglrx_8.452.1-1*.deb fglrx-kernel-source_8.452.1-1*.deb fglrx-amdcccle_8.452.1-1*.deb
sudo reboot
```

---

### Post by frogotronic on 2008-01-19
> **owhno said:**
> I installed ATI 8.1 last night. 
Installation is the same as 7.12 if you have it installed dont bother to delete something just install the new one.
cchtml is update so head over to [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.1_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.1_Driver_Manually)

And install it

if you have 7.12 installed then in my case it was installed with these commands

```
sh ati-driver-installer-8-01-x86.x86_64.run --buildpkg Ubuntu
sudo rm /usr/src/fglrx-kernel*.deb (didnt have files there but to be sure)
sudo dpkg -i xorg-driver-fglrx_8.452.1-1*.deb fglrx-kernel-source_8.452.1-1*.deb fglrx-amdcccle_8.452.1-1*.deb
sudo reboot
```

Okay, Thanks...**DOOR #1 it is!**


- CH

---

### Post by Polygon on 2008-01-19
i had some problems....i tried to use envy to install the new ones but that didnt work out so well

so i used envy to uninstall the new ones... but i had to manually delete /etc/xdm/compiz/compiz-settings because apt was throwing a hissy fit on how it couldent rename it to have a .ubuntu extension afterwards

but after that, i just ran the ati installer with --buildpkg Ubuntu/Gutsy , then installed fglrx-kernel-source, xorg-driver-fglrx and the amdcccle debs, ran "aticonfig --initial" in terminal, restarted, and now it works fine and dandy. and suspend works too now!

*is happy camper*

but like slogger said, ctrl+alt+backspace freezes my computer....not a huge deal as i dont use it unless my computer freezes xD

so...instead i just do alt+sysrq+REISUB to restart my computer

---

### Post by frogotronic on 2008-01-19
what's REIUSB?

- CH

---

### Post by rhc on 2008-01-19
I want a clean install.
I'm using restricted drivers now. i think it s 7.1 version.
How can i upgrade to 8.1 with a clean install?

---

### Post by lemonicetea on 2008-01-19
> **hedgebox said:**
> I installed them quite easily. Direct rendering and all worked without any tinkering. Hibernate /suspend does not for me (IBM Thinkpad T60). My graphics card is the Mobility X1400 and I am using Ubuntu 7.10. I also have not been able to get compiz to work with it yet.

Hi, I use the same laptop as you do. I can installed the ATI driver successfully, and direct rendering is Yes as well. But I can't use compiz fusion. I followed a post which remove xgl first before install the ati driver. some posts suggest install xgl after install the driver..How did you manage that? Thanks a lot.

---

### Post by ndtfl on 2008-01-19
I have Dell Inspiron 6400 w/ X1400, this driver, I must say, is the first release that I could get it to work correctly in the last 4 months (I tried every single one).  Without compiz, it works fine, easy installation (I ran into problem when running the binary install file directly, so end up using the buildpkg method but then it works fine)

Without compiz-fusion: Driver loads correctly, 2D apps seems to be decent, suspend/resume works (after twisting /etc/default/acpi-support).  Also I had some problem w/ system hang when trying to shutdown/reboot/logout, but I think it started working fine when I set teh overlay option to off in xorg.confg.

With compiz-fusion on: Works but suspend/resume no longer works, same problem as before, google around and still can't figure out how to fix it.

---

### Post by frogotronic on 2008-01-19
> **rhc said:**
> I want a clean install.
I'm using restricted drivers now. i think it s 7.1 version.
How can i upgrade to 8.1 with a clean install?


Hi,

Use Method 2 from this WIKI: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.1_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.1_Driver_Manually)

- CH

---

### Post by rhc on 2008-01-19
thanks cement_head.
I installed with that way too.
I'm curious about something now.
Can i disable Xgl and also get 3d desktop effects?
Because with Xgl i can't play games.

---

### Post by olskar on 2008-01-19
> **rhc said:**
> thanks cement_head.
I installed with that way too.
I'm curious about something now.
Can i disable Xgl and also get 3d desktop effects?
Because with Xgl i can't play games.

I think that is the point with aiglx that should now be supported with the new driver..I dont get it to work though.. : /

---

### Post by frogotronic on 2008-01-19
> **rhc said:**
> thanks cement_head.
I installed with that way too.
I'm curious about something now.
Can i disable Xgl and also get 3d desktop effects?
Because with Xgl i can't play games.

Yeah, this still seems to be a bit buggy.  For example, GoogleEarth is choopy and video is bad with COMPIZ enabled.

What I do is go to System>Preferences>Appearance>Visual Effects; then I just choose "No Effects" and I get full acceleration, good video, dual head and can play any games (ie QUAKE2).

I do have the following parameters for my xorg.conf:

```
Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "off"
	Option	    "OpenGLOverlay" "on"
	Option	    "useInternalAGPGART" "no"
	Option      "KernelModuleParm" "agplock=0"
	Option	    "DesktopSetup" "horizontal"
	Option	    "Capabilities" "0x00000800"
	Option	    "PairModes" "1280x800+1280x800,0x0+0x0,1280x800+1024x768"
EndSection
```

So I'm using OpenGL rather than Xv.  Seems to work better with DVDs in XINE player.

- CH


:guitar:

---

### Post by mzw! on 2008-01-19
I also have problems when shuting down, logging off, and restarting my computer since I upgraded to this version.
My computer is an ACER aspire with an ATI x700 and I running Kubuntu.

---

### Post by sloggerkhan on 2008-01-19
> **cement_head said:**
> Yeah, this still seems to be a bit buggy.  For example, GoogleEarth is choopy and video is bad with COMPIZ enabled.

What I do is go to System>Preferences>Appearance>Visual Effects; then I just choose "No Effects" and I get full acceleration, good video, dual head and can play any games (ie QUAKE2).

I do have the following parameters for my xorg.conf:

```
Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "off"
	Option	    "OpenGLOverlay" "on"
	Option	    "useInternalAGPGART" "no"
	Option      "KernelModuleParm" "agplock=0"
	Option	    "DesktopSetup" "horizontal"
	Option	    "Capabilities" "0x00000800"
	Option	    "PairModes" "1280x800+1280x800,0x0+0x0,1280x800+1024x768"
EndSection
```

So I'm using OpenGL rather than Xv.  Seems to work better with DVDs in XINE player.

- CH


:guitar:

I can't even run a video player trying to use XV, and on my computer, I don't think opengl playback is that great. As I mentioned before, subtitles seem to not work with xine, there's a clear video vsync problem using open gl for video, and mplayer throws error messages every time I start to play something. Mplayer at least shows subs, but they seem stuck at 14pt point font or something. Just really odd.

---

### Post by snl2587 on 2008-01-19
I tried out the new drivers following ATI's directions and,well, it failed. Fortunately I was able to do a quick rollback and I'm right back where I was. Kinda sucks, though...

Oh yeah, and I'm using the ATI XPRESS 200M.

---

### Post by darkpark on 2008-01-19
I'm running Gutsy 32bit with my shiny new HD3870 pci-express and the 8.01 drivers.
My method of installation was to create the .debs from the ATI installer, install them and use 'aticonfig' to generate a new xorg.conf.   After that, I rebooted and when gutsy was back up I noticed a few things:   dragging a window (web browser, nautilus, text editor, etc...) all over the screen is sluggish and causes cpu usage to spike up big time.  If I move the windows around fast enough than the contents of the window become scrambled/corrupted.  It goes back to normal as soon as I stop moving it.
Other than that, things seem fine but I haven't tried video playback yet.

system specs:
Intel Core 2 Duo E6750  2.66Ghz
Gigabyte P35-DS3L
4 GB RAM
Sapphire HD3870 PCI-E  512MB

---

### Post by sloggerkhan on 2008-01-19
> **darkpark said:**
> I'm running Gutsy 32bit with my shiny new HD3870 pci-express and the 8.01 drivers.
My method of installation was to create the .debs from the ATI installer, install them and use 'aticonfig' to generate a new xorg.conf.   After that, I rebooted and when gutsy was back up I noticed a few things:   dragging a window (web browser, nautilus, text editor, etc...) all over the screen is sluggish and causes cpu usage to spike up big time.  If I move the windows around fast enough than the contents of the window become scrambled/corrupted.  It goes back to normal as soon as I stop moving it.
Other than that, things seem fine but I haven't tried video playback yet.

system specs:
Intel Core 2 Duo E6750  2.66Ghz
Gigabyte P35-DS3L
4 GB RAM
Sapphire HD3870 PCI-E  512MB

Every ati driver I've used has a CPU spike and scrambled/unrefreshed window contents if you wave them around, unless using compiz, where things tear instead of scramble, so I didn't even think about that part.

---

### Post by Polygon on 2008-01-19
> **cement_head said:**
> what's REIUSB?

- CH

[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

To perform a safe reboot of a Linux computer which has otherwise locked up, the mnemonic "**R**aising** E**lephants **I**s **S**o **U**tterly **B**oring" is often useful. It stands for **R**aw (take control of keyboard back from X), t**E**rminate (kill -15 programs, allowing them to terminate gracefully), k**I**ll (kill -9 unterminated programs), **S**ync (flush data to disk), **U**nmount (remount everything read-only), re**B**oot. These keystrokes should be entered a few seconds apart. This should prevent a fsck being required on reboot; it also gives some programs a chance to save emergency backups of unsaved work.

---

### Post by rhc on 2008-01-20
Problem problem problem.
No way better than Restricted Drivers.
Com. becomes choppy,laggy with new Ati drivers.
Either mouse scrolling and youtube videos.

---

### Post by nasov on 2008-01-20
I had a look at the realse notes on these drivers!
As with the last release THEY ARE TAKING A MICKEY!!!
i know, making suspend work is one big improvement but c'mon its way OVERDUE!

i am seriously thinking of buying a nvidia card and I do hope ati guys are reading this!
btw, i hope that Phenom will fail!

---

### Post by sloggerkhan on 2008-01-20
If AMD gets out of the picture, it will be bad for consumers. So I hope they get their act together. 

And ATI employees are more likely to be browsing phoronix.

---

### Post by frogotronic on 2008-01-20
> **Polygon said:**
> [http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

To perform a safe reboot of a Linux computer which has otherwise locked up, the mnemonic "**R**aising** E**lephants **I**s **S**o **U**tterly **B**oring" is often useful. It stands for **R**aw (take control of keyboard back from X), t**E**rminate (kill -15 programs, allowing them to terminate gracefully), k**I**ll (kill -9 unterminated programs), **S**ync (flush data to disk), **U**nmount (remount everything read-only), re**B**oot. These keystrokes should be entered a few seconds apart. This should prevent a fsck being required on reboot; it also gives some programs a chance to save emergency backups of unsaved work.

Thanks!

---

### Post by frogotronic on 2008-01-20
> **nasov said:**
> I had a look at the realse notes on these drivers!
As with the last release THEY ARE TAKING A MICKEY!!!
i know, making suspend work is one big improvement but c'mon its way OVERDUE!

i am seriously thinking of buying a nvidia card and I do hope ati guys are reading this!
btw, i hope that Phenom will fail!


ummm....no.

ATI drivers are not that bad.  I had an nVIDIA card THAT WOULD NEVER SUSPEND OR HIBERNATE.  They are about 1.5 years behind nVIDIA, but they are improving MUCH faster than nVIDIA did.  I think in 6 months (6 more iterations) the drivers will almost perfectly comparable, and if the rate continues, ATI will surpass nVIDIA in about a year.

At least they (both nVIDIA and ATI) are much better on Ubuntu than on WindowsXP!

Phenom won't fail - they had a bug or two and its been fixed.

Chill out - I feel your pain, but it less of an issue with nVIDIA or ATI and more of an issue with the hardware (MOBO) manufacturers.  

:popcorn:

---

### Post by sloggerkhan on 2008-01-20
> **cement_head said:**
> ummm....no.

At least they (both nVIDIA and ATI) are much better on Ubuntu than on WindowsXP!

:popcorn:

Don't know what planet you live on. 
My card got much better performance on most games under XP-pro.

---

### Post by rhc on 2008-01-21
I don't know their development acceleration but i know the acceleration of scrolling in Firefox with Ati Drivers.
They are unusable for now.

---

### Post by Dreamlocked on 2008-01-21
I get a nice (EE) fglrx(0): Failed to initialize CMMQS driver, on my ATI Mobility Radeon 9700.
Oh well, back to 7.12.

[quote=daniel of sarnia]
The driver is 8.01, not 8.1 which would be the tenth driver of 2008. The same way ubuntu is numbered.

Anyways I tried, compiz works well and my resolution is right, 1680x1050. But video playback acceleration is still essentially broken and some 3D apps don't work ie. quake 4. Back to 8.40.3 for me... At least the open source driver is making good progress.
[/quote]

Btw, the driver version is indeed 8.1 and not 8.01.
That is because software versions don't necessarily follow the decimal system. For instance, you can have 8.1, 8.2, .... 8.9, 8.10, 8.11, ... and even 8.100 (though 100 wouldn't be the case for fglrx drivers, since the number after the first dot is the month's number). And you can even add more dots! 8.10.1 or 8.10.67

It just happens that Ubuntu chose to add a 0 for, say, 7.04.
To each his own...

---

### Post by angels on 2008-01-21
I installed a new driver ... but ... when I try to 'logout' the computer freezes ... why that? I never had the problem like that before :confused:

other things works fine - 3D works but if they are enabled, I cannot watch the videos (as with previous version of driver)

I hope someone can help me

---

### Post by ykpaiha on 2008-01-21
For info
on a fresh install the new drivers didn't work at all
ati radeon 3850 512 mo + 22 inch
as I tried all the trick here and there I insulted my choice of ati card
Then back to the envy driver (previous version with the screen size bug) then reinstall over it the new 8.1 and here it worked ?!!!!!
1680x1050 with compiz great I still have a bug when I restart or user change but at least it is usable for me.
try out it worth!
And if someone have an explanation.....

---

### Post by frogotronic on 2008-01-21
> **sloggerkhan said:**
> Don't know what planet you live on. 
My card got much better performance on most games under XP-pro.


Well, I can't say about games.  I don't play many at all, so I'll take your work for that.  But is that the card & drivers which are poorly performing, or is it the hack trying to make a windows game run natively in Ubuntu that's the culprit?

I do know that most OpenGL stuff (molecular modeling) works well and can be more easily adjusted (tweaked) with Ubuntu.

I have an ATI Radeon X2300 card on an HP 6910p laptop and have had almost no problems at all (without COMPIZ).  The X11 does freeze on logout with the 8.01 drivers...but it will likely be fixed next month.  With COMPIZ, its a different story.  But I consider COMPIZ an interesting diversion and can be easily disabled.  I'd rather have core things like the the video drivers and other bugs dealt with as opposed to bell & whistles.

- CH

---

### Post by angels on 2008-01-21
> **cement_head said:**
>  The X11 does freeze on logout with the 8.01 drivers...but it will likely be fixed next month.  With COMPIZ, its a different story.  But I consider COMPIZ an interesting diversion and can be easily disabled.  I'd rather have core things like the the video drivers and other bugs dealt with as opposed to bell & whistles.

- CH

I hope it will really be fixed (X11 that freezes) next month .. this is my bigger concern. Thanks :)

---

### Post by Onimae on 2008-01-21
Everything installs fine. Here is what happens with and without Compiz enabled:

_**Without**_
1. System suspends and hibernates
2. Xv Playback is smooth
3. GL playback is smooth
4. Life is good,  pretty much.

_**With_**
1. System does not suspend or hibernate succesfully.
2. Xv Playback sucks (it flickers)
3. GL playback sucks (it flickers)
4. Life is bad.

Peter wants his Compizy goodness! :mad:

**Peter**

---

### Post by nasov on 2008-01-21
> **cement_head said:**
> ummm....no.

ATI drivers are not that bad.  I had an nVIDIA card THAT WOULD NEVER SUSPEND OR HIBERNATE.  They are about 1.5 years behind nVIDIA, but they are improving MUCH faster than nVIDIA did.  I think in 6 months (6 more iterations) the drivers will almost perfectly comparable, and if the rate continues, ATI will surpass nVIDIA in about a year.

At least they (both nVIDIA and ATI) are much better on Ubuntu than on WindowsXP!

Phenom won't fail - they had a bug or two and its been fixed.

Chill out - I feel your pain, but it less of an issue with nVIDIA or ATI and more of an issue with the hardware (MOBO) manufacturers.  

:popcorn:


Well,
just to do justice to ATI, With ubuntu 7.04 and the 8.41 drivers absolutley everything worked for me!
Compiz, video playback in fullscreen, games etc. (not to mention the fact that I spent weeks trying to get it all running as I wanted plus I was really new to ubuntu back then, im not so new now, still green)
After updating to gutsy and the 8.42 drivers i started having problems and just couldn't understand why would someone alter something so it starts doing one thing right at the expense of something else that is equally useful or important? 
all that im on about is that I paid for my card, my hardware and I can't use it for tasks it was created!
Wouldn't you be pissed off if let's say you bought a car and it's head lights, gearbox and air con wouldn't work?
would you say... ahh well.. at least i can sit inside it!!?

PS
Sorry for sounding like im attacking you but i couldn't get the drivers running properly from day one when i got ubuntu and Im a bit frustrated with every version being a mock. But if you say that they are still doing better than Nvdia that's fine! its a shame that it will take them six months to get there (from now) and I think its a optimistic estimation.

---

### Post by nasov on 2008-01-21
double posted myslef by accident - sry

---

### Post by muecker on 2008-01-21
The new install is easy.  There is no longer a step for manually running the module-assistant to build the driver as it is done automatically now.

The driver seems to be working fine, but I've had a few minor inconveniences.  I don't know if this is due to the new ATI driver, or something else (maybe the xorg fixes today).  The biggest one is my fingerprint reader isn't quite working right today, the little GUI fails to run so I get prompted for a password or things like Synaptic take two tries.  I haven't tried troubleshooting it yet.

For compiz, I had to manually update /usr/bin/compiz as follows:
COMPIZ_BIN_PATH="/usr/bin"
PLUGIN_PATH="/usr/lib/compiz"
COMPIZ_NAME="compiz.real"
WHITELIST="fglrx"

I'm not sure why those settings changed, could be due to other things I did but I noticed a new /etc/xdg/compiz.compiz-manager was trying to install with the fglrx driver (it wasn't there afterwards) so maybe AMD is trying to automatically add fglrx to the whitelist.

---

### Post by frogotronic on 2008-01-21
> **muecker said:**
> The new install is easy.  There is no longer a step for manually running the module-assistant to build the driver as it is done automatically now.

The driver seems to be working fine, but I've had a few minor inconveniences.  I don't know if this is due to the new ATI driver, or something else (maybe the xorg fixes today).  The biggest one is my fingerprint reader isn't quite working right today, the little GUI fails to run so I get prompted for a password or things like Synaptic take two tries.  I haven't tried troubleshooting it yet.

For compiz, I had to manually update /usr/bin/compiz as follows:
COMPIZ_BIN_PATH="/usr/bin"
PLUGIN_PATH="/usr/lib/compiz"
COMPIZ_NAME="compiz.real"
WHITELIST="fglrx"

I'm not sure why those settings changed, could be due to other things I did but I noticed a new /etc/xdg/compiz.compiz-manager was trying to install with the fglrx driver (it wasn't there afterwards) so maybe AMD is trying to automatically add fglrx to the whitelist.


Could you post (or email me) how you got yuor fingerprint reader working?  I haven't tried that yet.

Thanks,
CH

---

### Post by frogotronic on 2008-01-21
> **nasov said:**
> Well,
just to do justice to ATI, With ubuntu 7.04 and the 8.41 drivers absolutley everything worked for me!
Compiz, video playback in fullscreen, games etc. (not to mention the fact that I spent weeks trying to get it all running as I wanted plus I was really new to ubuntu back then, im not so new now, still green)
After updating to gutsy and the 8.42 drivers i started having problems and just couldn't understand why would someone alter something so it starts doing one thing right at the expense of something else that is equally useful or important? 
all that im on about is that I paid for my card, my hardware and I can't use it for tasks it was created!
Wouldn't you be pissed off if let's say you bought a car and it's head lights, gearbox and air con wouldn't work?
would you say... ahh well.. at least i can sit inside it!!?

PS
Sorry for sounding like im attacking you but i couldn't get the drivers running properly from day one when i got ubuntu and Im a bit frustrated with every version being a mock. But if you say that they are still doing better than Nvdia that's fine! its a shame that it will take them six months to get there (from now) and I think its a optimistic estimation.

hey man, that's cool.

Don get me wrong - I'd way rather have them working at least nVIDIA levels.  But, being a free OS, its manageable (for now).  Definitely file a bug report with ATI so they can get on it.  It looks as if they are trying.  If they get it smoothed out in a couple months that's okay with me.

- CH

---

### Post by mzw! on 2008-01-21
I found out also that doing glxgears it gave me 30fps... besides it does not shutdown. so low performance? why?

---

### Post by NoVista on 2008-01-21
Thank you, Dreamlocked.
I knew I was correct :)

Looks like another month of having to run Ubuntu with XGL for CF.
Dang, I want to believe AMD/ATI are trying, yet months later, and not good enough AIGLX support to run CF. 

I'm up for a newer system soon. Planning it right around the the release for the next Ubuntu, with it's long term support. I was hoping ATI would have their act together for the Linux community by then. Alas, time looks like it is running short, and when I purchase that next system, it will be ATIless.

Thanks for all the input on the new drivers, everyone.

---

### Post by murmel on 2008-01-21
I'm using the 8.01 driver with Ubuntu Gutsy and most of the things are working, quit good. After some tweaking I came to the conclusion that it's compiz that screws up the direct rendering.
Because of when it's activated i get this:
glxinfo | grep rendering :: direct rendering: no (LIBGL_ALWAYS_INDIRECT set)
I turn it off and reboot:
glxinfo | grep rendering :: direct rendering: yes

Hehe, and when Compiz is activated both OpenArena and Nexuiz get 15-25 fps, when it's not activated i get 115-125fps. I'll live with this. I only have to reboot when I want to play a game or something else that uses direct rendering, and that's not so bad. What if it didn't work at all?

I got a Sony Vaio VGN-CR21Z with a Radeon Mobility X2300 as someone else above. It's just to keep on hoping that ATI will fix this as soon as possible. I've crossed my fingers and are thanking them for the latest driver that works as good as it does. Thanks!

- Simon

---

### Post by moron on 2008-01-21
This latest driver has an issue that causes a lockup on shutdown for a number of folks (me included). Apparently it is due to some interaction with the power related daemon atieventsd:

[http://www.phoronix.com/forums/showthread.php?t=7448](http://www.phoronix.com/forums/showthread.php?t=7448)

I also am still personally having sporadic issues with my widescreen resolution not being picked up correctly on startup (x1250 is the card) or when I come out of an OpenArena session.  I have to power cycle my monitor a few times before it gets found correctly by the card, launch amdccle play with the resolution or restart X.

If I had the money handy I would have bought a new Nvidia card today, the state of the the ATI drivers is disheartening to say the least.  

Cheers

---

### Post by WaySensei on 2008-01-21
I was not able to resume from suspend after installing the 8.01 driver on my Radeon X1600 as the release notes claimed. In addition, performance was choppier than the restricted driver, and Secret Maryo crashed upon start :( Because of this, I uninstalled the 8.01 driver and tried to return to the restricted 8.37.6 driver. However, now I have a major issue. The Restricted Driver Manager shows that my ATI driver is "not in use" after installing xorg-driver-fglrx. The details of this problem can be found here: [http://ubuntuforums.org/showthread.php?t=609467]("http://ubuntuforums.org/showthread.php?t=609467")

I would greatly appreciate any help you could provide.

---

### Post by dagfinn on 2008-01-22
> **moron said:**
> This latest driver has an issue that causes a lockup on shutdown for a number of folks (me included). Apparently it is due to some interaction with the power related daemon atieventsd:

[http://www.phoronix.com/forums/showthread.php?t=7448](http://www.phoronix.com/forums/showthread.php?t=7448)

I did the unofficial upgrade to the 2.6.24 kernel ([http://ubuntuforums.org/showthread.php?t=646755](http://ubuntuforums.org/showthread.php?t=646755)) and suspend started working, but the system locks up on shutdown if it's been suspended earlier. This happened with the 7.11 driver (which I reverted to after trying 7.12). 8.01 installed and works fine, but the shutdown problem remains. So in my case at least, the shutdown problem appears not to be specific to 8.01. It just became apparent since suspend started working.

---

### Post by Yaba on 2008-01-22
ATI 8.1 driver on a HP Compaq nw8240 with a Radeon Mobility X700:
[LIST]
[*]When shutting down, screen turns black and locks up. Sometimes hitting the power button persuades the system to do a clean shutdown, but not always.
[*]Suspend does not work - but it never did on my system. suspend2 ends the X session and shows a empty console screen, then locks up. ACPI suspend locks up the system immediately.
[/LIST]

Update: Removing the line

> Option "VideoOverlay" "on"

from my xorg.conf helped. I can reboot again, however no XV overlay anymore :-(

---

### Post by dynamethod on 2008-01-22
I had to reinstall my OS after trying that bloody driver, using X800 XT Radeon

it totally screwed everything up

---

### Post by markoloka on 2008-01-22
I have same shutdown bug. Ctrl+Alt+Del seems to get it shutdown better than power off.
Otherwise looks fine.

---

### Post by Talon2 on 2008-01-22
Does anyone have the 8.01 driver working with an AGP card?

All I get is a blank screen with a x1650pro agp card.

:(

---

### Post by rhc on 2008-01-23
I worked it with and AGP.

---

### Post by fethio on 2008-01-23
I tried installing 8.1 both ways (Ubuntu way, and manually) without success. The install worked fine. just as described [here]("//http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_7.12_Driver_Manually").

the fglrx module was loaded, and in the restricted_manager it was in use (green light but not enabled).

When I called aticonfig, it exited without touching a thing, it said it didn't need to do anything. So, I changed the "device" section in xorg.conf manually, replacing driver "ati" with "fglrx". When I restart X, I get simply a blank screen and no way to get back (CTRL-ALT-BKSP does not work), so I have to reboot the system in "safe mode" and change the driver setting in xorg.conf back to "ati". 

I suspect that my monitor is messing up, but I haven't seen anybody mentioning about monitors in forums. When kdm starts up, a message like "frequency scaling is not supported" passes by. In addition, in the Xorg.0.log listed below, there's a line which says "Screen 0 is not DRI capable".

During normal operation (when the "ati" driver is being used) I get the following message during startup of abaqus, similar message is displayed during startup of Pro/E
> Xlib:  extension "XFree86-DRI" missing on display ":0.0".

Does this provide any clue to what may be happening?

fethi


Excerpt from Xorg.0.log
> 
...
(--) Chipset ATI Radeon 9600 AS (AGP) found
...
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports 
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
...
(EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
[dri] Disabling DRI.
...
(EE) AIGLX: Screen 0 is not DRI capable
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
...
(II) RADEON(0): Manufacturer: SNY  Model: 2250  Serial#: 16843009
(II) RADEON(0): Year: 2004  Week: 17
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.643 redY: 0.344   greenX: 0.304 greenY: 0.566
(II) RADEON(0): blueX: 0.141 blueY: 0.085   whiteX: 0.312 whiteY: 0.318
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  304 x 228 mm
(II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Ranges: V min: 57  V max: 63 Hz, H min: 28  H max: 49 kHz, PixClock max 90 MHz
(II) RADEON(0): Monitor name: SDM-HS53
...


The xorg.conf file (related sections)
> 
Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Vendorname	"Sony"
	Modelname	"Sony SDM-HS53"
	Horizsync	28.0	-	49.0
	Vertrefresh	57.0	-	63.0
	Gamma	1
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
EndSection

Section "Monitor"
	# 
	Identifier	"monitor1"
	Gamma	1
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Driver		"ati"
	Vendorname	"ATI"
	Boardname	"ATI Radeon (fglrx)"
	Option	    "MergedFB" "off"
#	Option		"VideoOverlay"	"on"
#	Option		"OpenGLOverlay"	"off"
	Busid		"PCI:1:0:0"
EndSection

Section "Device"
	# 
	Identifier	"device1"
	Driver		"ati"
	Vendorname	"ATI"
	Boardname	"ATI Radeon (fglrx)"
	Option		"MergedFB"	"off"
	Busid		"PCI:1:0:0"
	Screen	1
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Driver		"fglrx"
EndSection

Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	Defaultdepth	24
	SubSection "Display"
		Virtual	1024	768
		Depth	24
		Modes		"1024x768@60"	"800x600@60"	"640x480@60"
	EndSubSection
EndSection

Section "Screen"
	# 
	Identifier	"screen1"
	Device		"device1"
	Monitor		"monitor1"
	Defaultdepth	24
EndSection

Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	Defaultdepth	24
	SubSection "Display"
		Viewport	0	0
		Depth	24
	EndSubSection
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option		"Composite"	"0"
EndSection


---

### Post by kellemes on 2008-01-23
> **Talon2 said:**
> Does anyone have the 8.01 driver working with an AGP card?

All I get is a blank screen with a x1650pro agp card.

:(


Same here..
It's pissing me of you can't believe!
the last 3 versions give me this result.
I'm forced to use 8.42.3
see [http://ati.amd.com/support/drivers/linux/previous/linux-r-8-42-3.html](http://ati.amd.com/support/drivers/linux/previous/linux-r-8-42-3.html)

---

### Post by MrClearPore on 2008-01-23
> Anyone install these yet?

I cannot shut down or reboot with these new drivers,  My screen goes black and just hangs there.  I either have to either Ctrl-Alt-Del twice to reboot, or use the command

```
sudo shutdown -r now
```

Aside from that, everything seems fine.  I'm not into Compiz (it's never really appealed to me because all my browsing becomes choppy and I lose the borders around all my application windows).  I don't play games either, so my gripes aren't as bad as many others' :lolflag:

I like the way the new DKMS handles the installation.  I think this way, a new kernel update won't affect the drivers as it did with older version of the ATI drivers, but I could be wrong.  IIRC with the 8.42 drivers I had to run a few commands after my kernel updated, and I didn't have to do that with these new drivers.

I hope the shut down/reboot bug gets fixed soon!  The programmers over at AMD are getting closer though.  Let's have patience, people :)

---

### Post by _kjus on 2008-01-23
i hate my self for buying an ati card  ](*,) .
since ati catalyst 8.1 some stuff is getting better, but not all!
System: gutsy Kernel:2.6.22-14 Hardware: ibm: t60
compiz is not working!! 
and most important for me - **no hibernate and suspend **
**F... also restart X crtl alt backspace does not work!!!**
Any solutions???

---

### Post by rhc on 2008-01-23
Solution is the restricted driver.

---

### Post by Connerll on 2008-01-23
I installed the 7.10 workstaton and the 7.10 server.  The workstation recognized my ATI card with a Sansung monitor at install time and has not been an issue.  I have installed various scenarios for the server and the monitor or dispaly issue is still there.  Using the Ubuntu repositories, I did not get anywhere.  I recenlty downloaded the latest ATI driver (ati-driver-installer-8-01-x86.x86_64.run), converted to a deb, and followed the gusty install instructions.  Now, it almost works (at least some response).  The digital box in the upper left corner of the screen appears for an instant and then the process fails.  There are a couple of reported errors (Divice ID) but the failure appears to be a path to fonts.  The fatal error states 'counld not open default font 'fixed''.

Anyone have any ideas???

I am also having an isuue with Lexmark all in one printer - no go at all.

Any help will be appreciated! Thanks---Connerll

---

### Post by NoVista on 2008-01-23
Ok, not to get off the topic of this post, so here:
[http://ubuntuforums.org/showthread.php?t=49714](http://ubuntuforums.org/showthread.php?t=49714)

It's probably the one post where you will either find/and/or/ get your answer for your printer.

---

### Post by Resonance378 on 2008-01-23
I've installed the 8.1 drivers without any real issue and I've been blogging about the experience of Ubuntu and the like from the start (well since today at least) but I've been at this since Sunday and am really enjoying it.  My signature has the link to my blog.

---

### Post by muecker on 2008-01-24
>  Originally Posted by Talon2
Does anyone have the 8.01 driver working with an AGP card?

All I get is a blank screen with a x1650pro agp card.

Same with me, black screen display locks up entirely as soon as it goes to graphical mode.  I was able to reboot into safe mode and remove the new driver and go back to the restricted module.  I didn't realize it was an issue with the x1650 on AGP.  Has anybody filed a bug with ATI yet?

---

### Post by murmel on 2008-01-24
Have you tried any of backups of your xorg.conf?
Have you tried configuring ati?
aticonfig --initial
aticonfig --overlay-type=Xv

Maybe it helps...

---

### Post by SoulSmasher on 2008-01-24
i'm using acer aspire as5104 laptop (which has mobility radeon x1300 ) and tried deleting restricted drivers and then clean install posted [here]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.1_Driver_Manually"), but as told above with compiz, all my opengl graphics' performance sucks. (like the old ati drivers) :( so i rolled back to restricted driver..

has anyone got working both compizfusion and opengl games , with good performane (as it has to be) like restricted drivers?

---

### Post by legzelda on 2008-01-25
I am also having similar problems others have been experiencing in this thread.  Ctrl + Alt + Backspace "freezes" my Dell E1505 with an X1400, but Ctrl + Alt + Del pressed a few times will reboot the computer.  And yes, having the computer freeze on logout is even more annoying.

The good news?  Changing post video to false in /etc/default/acpi-support makes suspend work without any problems--FINALLY.  These other problems are terribly annoying, however, and I hope a fix is found.

---

### Post by Arand on 2008-01-26
Same here:

Using an Acer TravelMate 2450 laptop, ATI radeon Xpress 200M. 

Installed driver quite smoothly by following: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

(Had to use the extra configs in that guide to get Sus/Hib to work, and had to reinstall Compiz-Fusion; following 'install' part of; [https://help.ubuntu.com/community/CompositeManager/CompizFusionATI?highlight=%28compiz%29](https://help.ubuntu.com/community/CompositeManager/CompizFusionATI?highlight=%28compiz%29)  and then whitelist it as described in the topmost guide to get CompizF working)

----------

BUT, I'm having kinda the same problem with X-restart:

If I do Ctrl+Alt+Backspace within ~3min after login, it restarts fine, however...

...if I wait a while (even without touching anything) and then try to restart X I get stuck: The menus and icons disappear, and it locks up with only the wallpaper showing, can't do Ctrl+Alt+[F*], can't use Ctrl+Alt+Backspace again.

What I CAN do is to press Ctrl+Alt+Del or the Laptop power button, which makes the computer reboot/shutdown in about half a minute (even showing the shutdown splash!).

Rather odd...

solutions...?

- Arand

---

### Post by kegobeer on 2008-01-26
Here's how I fixed my ctrl-alt-backspace / logoff problem:

[http://www.phoronix.com/forums/showpost.php?p=23097&postcount=23](http://www.phoronix.com/forums/showpost.php?p=23097&postcount=23)

I elected to do this: "/usr/sbin/update-rc.d -f atieventsd remove"

---

### Post by Aaron_M_E on 2008-01-27
Hello all,

I recently converted one of my desktops (being used as a server) to Ubuntu 7.10 from Windows XP. When I first installed Ubuntu I had an issue with the ATI driver but fixed it using a fix I found in a blog. The fix worked for a few weeks and all of a sudden one morning I turned on the monitor and the display is all messed up. The thing is that I am able to see the login area (shadows mainly) and login to the machine. Once logged in I start a vnc session from my laptop and am able to work on the machine no problem. As I am changing screen through vnc I can see the colour changing on the monitor of the linux box. From the bit I understand this issue could have been cause if there was an update to the kernel recently and thus messed up my video.

Does anyone have any suggestions? Anything would be greatly appreciated!

PS. I am comfortable with the command line as I have done work on Unix (limited but familiar)

](*,)

---

### Post by CarpKing on 2008-01-27
> **Aaron_M_E said:**
> Hello all,

I recently converted one of my desktops (being used as a server) to Ubuntu 7.10 from Windows XP. When I first installed Ubuntu I had an issue with the ATI driver but fixed it using a fix I found in a blog. The fix worked for a few weeks and all of a sudden one morning I turned on the monitor and the display is all messed up. The thing is that I am able to see the login area (shadows mainly) and login to the machine. Once logged in I start a vnc session from my laptop and am able to work on the machine no problem. As I am changing screen through vnc I can see the colour changing on the monitor of the linux box. From the bit I understand this issue could have been cause if there was an update to the kernel recently and thus messed up my video.

Does anyone have any suggestions? Anything would be greatly appreciated!

PS. I am comfortable with the command line as I have done work on Unix (limited but familiar)

](*,)

I don't have any real help to offer, but you would probably get help faster if you posted a new thread detailing your problem.

---

### Post by angels on 2008-01-27
> **kegobeer said:**
> 
I elected to do this: "/usr/sbin/update-rc.d -f atieventsd remove"

Hi kegobeer,
is this really helpful? I just check before I do something that I would not fix? I'm a newbie :)

---

### Post by _kjus on 2008-01-27
"/usr/sbin/update-rc.d -f atieventsd remove"
helped for me! 
System: gutsy Kernel:2.6.22-14 Hardware: ibm: t60
Now suspend, hibernate and alt-crtl-backspace works. Cool.
The only problem is, that sometimes I get an error with some applet panel, like the trash appelt.
Thanks!

---

### Post by murmel on 2008-01-27
It works for me with removing atieventsd
```
mkdir ~/.backup
sudo -i
cp /etc/rc0.d/K20atieventsd ~/.backup
echo "rc0,1,6" >> ~/.backup/rc
rm /etc/rc[016].d/K20atieventsd
```

---

### Post by Mxyzptlk83 on 2008-01-27
When configuring fglrx-kernel-source package there's a problem:

```
Adding Module to DKMS build system
Doing initial module build

Error! Your kernel source for kernel 2.6.22-14-386 cannot be found at
/lib/modules/2.6.22-14-386/build or /lib/modules/2.6.22-14-386/source.
Installing initial module

Error! Could not locate fglrx.ko for module fglrx in the DKMS tree.
You must run a dkms build for kernel 2.6.22-14-386 (i686) first.
Done.
```

The new fglrx.ko module has not been successfully installed but I don't know the reason. I've googled this problem but no results :(

Anyone has an idea?

**EDIT: Solved installing kernel-headers-2.6.22-14-386 :)**

---

### Post by aya_pro on 2008-01-27
> **angels said:**
> Hi kegobeer,
is this really helpful? I just check before I do something that I would not fix? I'm a newbie :)
Worked for me too.

angels, to just test it (no harm done), open console and do

```
ps -Hef | grep atieventsd
```
you will get something like

```
root      5550     1  0 Jan27 ?        00:00:00   /usr/sbin/atieventsd
root      6218  5550  0 Jan27 ?        00:00:00     sh -c /etc/ati/authatieventsd.sh grant :0 (null)
root     24451 23910  0 03:26 pts/1    00:00:00           grep atieventsd
```
your numbers will vary
now do (this is just an example for the output above. Use your own PIDs - the number right after the 'root' word)
```
sudo kill -9 5550 6218
```
Now try to reboot or log out. It should work.
Then you can execute the code kegobeer mentioned to prevent atieventsd loading at startup time.
By the way to get all symlinks back, i.e. revert everything, you can just reinstall fglrx packages.

---

### Post by angels on 2008-01-28
> **aya_pro said:**
> Worked for me too.

angels, to just test it (no harm done), open console and do
....
Now try to reboot or log out. It should work.
Then you can execute the code kegobeer mentioned to prevent atieventsd loading at startup time.
By the way to get all symlinks back, i.e. revert everything, you can just reinstall fglrx packages.

thanks for your help, to all of you :)
it works - I can logout successfully, but when I log in I encounter some problems: I get the message like this:
**The panel encountered a problem while loading "OAFIID: GNOME_Panel_TrashApplet". Do you want to delete the applet?...**
Do you have some ideas?
I appreciate your help

---

### Post by aya_pro on 2008-01-28
Ahh... I am afraid I cannot help you here since as you can see I am on Kubuntu.
You did not have this problem before getting rid of atieventsd, did you?

I would think that the TrashApplet problem should not be related to your video drivers...

Are you getting this error after log out and log on OR/AND after reboot also?

---

### Post by angels on 2008-01-28
Hm...this happens only when I login/logout, on reboot everything is OK. 
And in my opinion this is related to video settings as I encountered the same error before (for example, when I tried to connect computer with the TV and some of the changes in xorg.conf were conflicting, ...the only difference is that that time I knew how to fix the error :().

thanks for your help, however. I hope I'll find the solution or someone else will :confused:

---

### Post by johnwren on 2008-01-28
Some potentially useful information (and some notice about the February 8.02 drivers and ubuntu) is available  here: [http://www.phoronix.com/scan.php?page=article&item=976&num=1](http://www.phoronix.com/scan.php?page=article&item=976&num=1)
Looks like ati is paying a lot of attention to ubuntu.

---

### Post by fredwong on 2008-01-28
Hardware: Gigabyte GA-MA69G-S3H, ADM x2 64bit 5000+ 2.6GHz, 2g RAM, 500g hard disk.

I installed on Gutsy 7.10 with no problem and now 1360x768 works for me. I have a Sony LCD TV with native resolution of 1366x768 and the last release of the driver just would not display in 1360x768. The only problem I am having now is Mythtv plays TV programs, DVDs, etc like slow motion. I am battling with it and pulling my hair out. Anyone has any suggestion on how to fix slow playback of video using the onboard ATI x1250 chip?

---

### Post by JoePits on 2008-01-30
> **angels said:**
> thanks for your help, to all of you :)
it works - I can logout successfully, but when I log in I encounter some problems: I get the message like this:
**The panel encountered a problem while loading "OAFIID: GNOME_Panel_TrashApplet". Do you want to delete the applet?...**
Do you have some ideas?
I appreciate your help

that happened to me and i deleted it by mistake  i ran synaptic and reinstalled ubuntu-desktop not sure if i fixed it. gonna try to reinstall gnome from there now becuasei just realized trash can is still gone.


anywyas i just want compz/desktop effects working i tried reinstalling compiz like the other guy.

---

### Post by popiculo on 2008-01-30
everything goes fine until i try to run this:

```
sudo dpkg -i xorg-driver-fglrx_8.452.1-1*.deb fglrx-kernel-source_8.452.1-1*.deb fglrx-amdcccle_8.452.1-1*.deb
```

i get the following error:

dpkg: error processing xorg-driver-fglrx_8.452.1-1*.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing fglrx-kernel-source_8.452.1-1*.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing fglrx-amdcccle_8.452.1-1*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 xorg-driver-fglrx_8.452.1-1*.deb
 fglrx-kernel-source_8.452.1-1*.deb
 fglrx-amdcccle_8.452.1-1*.deb

not sure what to do now. can anyone help?

---

### Post by kegobeer on 2008-01-30
> **popiculo said:**
> everything goes fine until i try to run this:

```
sudo dpkg -i xorg-driver-fglrx_8.452.1-1*.deb fglrx-kernel-source_8.452.1-1*.deb fglrx-amdcccle_8.452.1-1*.deb
```

i get the following error:

dpkg: error processing xorg-driver-fglrx_8.452.1-1*.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing fglrx-kernel-source_8.452.1-1*.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing fglrx-amdcccle_8.452.1-1*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 xorg-driver-fglrx_8.452.1-1*.deb
 fglrx-kernel-source_8.452.1-1*.deb
 fglrx-amdcccle_8.452.1-1*.deb

not sure what to do now. can anyone help?

Did you download the installer, open a terminal window, switch to that directory, and execute this command:
sh ati-driver-installer-8-01-x86.x86_64.run --buildpkg Ubuntu/gutsy

Then, did you verify the .deb files were created?

---

### Post by fettuohi on 2008-01-31
I'm also running the 8.01 ATI drivers with my Radeon HD 2400XT and my Gutsy machine freezes on everytime I logout (even if I kill the xserver with Ctrl+Alt+Del) when compiz is on.

Regards

André

---

### Post by H_Plow on 2008-01-31
Hi there! 

Ubuntu GUTSY AMD64 Desktop
Kernel 2.6.22-14-generic (also tried on a 2.6.20.3-custom kernel I had installed...for various reasons..)

Using fglrx 8.1 also here on my HD2600XT 256MB PCI-E...and I cannot describe you all the fu**in job to let them work...even with Compiz activated (whatever compiz leaks on some "bugs" itself...)

"/usr/sbin/update-rc.d -f atieventsd remove"

Helped me to fix the "CTRL+ALT+BACKSPACE" problem.....whatever "CTRL+ALT+F(*)" issue still exists...

I cannot switch to a TTY console....when I try to do that I only get a blank screen (monitor still in sync) but I cannot even go back to X session (F7 to F9) or to another TTY session...only thing I can do is to press (simultaneously) "ALT+SYS RQ + S + U + B"  to reboot my machine....

I'm about satisfied after HARD job to let PAINFUL-FGLRX to "work"...but to be unable to use a TTY console is quite annoying...

Any idea? Any clues?
Many thanks.
Regards.

---

### Post by chaosrl on 2008-01-31
Hey guys,

I'm the typical T60 AMD64 Mobility Radeon X1400 user here. Upgraded (via the wiki guide on manual installation) to 8.1 without any hitches in an attempt to fix suspend and hibernate. My final results:

On the 2.6.22 kernel:

- Everything works like before. Compiz-Fusion works fine.
- Login/Logout was broken until I ran the fix posted here.
- I haven't tried Ctrl-Alt-F* yet, I'll try it when I get back on my computer.
- The only difference that I've found is that previously when I tried suspend, my computer would blink the suspend light indefinitely. Now, it'll attempt to go into suspend, and then immediately turn on again, prompting a login (as if I'd locked my computer). Then, after login, a little notification bubble will pop up and tell me that my computer has failed to go into suspend, and to check the help file for more information. This occurs with or without Compiz running. Hibernate appears to enter hibernate correctly, but booting up results in a normal boot.

On the 2.6.24 kernel, which I installed hoping suspend would be fixed:

- xserver-xgl was uninstalled for this and I attempted to use AIGLX (I don't know much about this, I just searched synaptic for AIGLX and installed whatever came up).
- Compiz-Fusion would not start because no composite was found (I suspect because I didn't have it set up correctly).
- Gave up and reinstalled xserver-xgl. Now, Compiz-Fusion runs, but everything is PAINFULLY slow and choppy. The computer is unusable. I did, however, try to suspend with and without Compiz running; both yielded the same result as above.

There's my long post, if anyone knows how to get suspend/hibernate working, I'd greatly appreciate it!

-Jeff

---

### Post by jack handy on 2008-01-31
updated Envy to the newest version, and BOOM!  everything works great now, and i've got my sweet high resolution back!  weee

---

### Post by frogotronic on 2008-02-01
> **H_Plow said:**
> 
"/usr/sbin/update-rc.d -f atieventsd remove"

Helped me to fix the "CTRL+ALT+BACKSPACE" problem.....whatever "CTRL+ALT+F(*)" issue still exists...



Whoops!  This command buggered my suspend/hibernate.  I'd like to reinstall the binary driver, but....that's a bit tricky.  Anyone know how to get the modules rebuilt against the rrunning kernel and all the hooks inserted again?

Thanks,
CH

---

### Post by SoulSmasher on 2008-02-01
i have the same issue with [post #43]("http://ubuntuforums.org/showpost.php?p=4178424&postcount=43"), opengl applications cannott run properly..
i've already started a topic [here]("http://ubuntuforums.org/showpost.php?p=4239679")..

could anyone solve this issue about opengl stuff? everything works fine while metacity is active :(

here's my xorg.conf 
```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"tr"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Extensions"
	Option		"Composite"	"Enable"
EndSection
```

---

### Post by frogotronic on 2008-02-01
> **SoulSmasher said:**
> i have the same issue with [post #43]("http://ubuntuforums.org/showpost.php?p=4178424&postcount=43"), opengl applications cannott run properly..
i've already started a topic [here]("http://ubuntuforums.org/showpost.php?p=4239679")..

could anyone solve this issue about opengl stuff? everything works fine while metacity is active :(

here's my xorg.conf 
```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"tr"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Extensions"
	Option		"Composite"	"Enable"
EndSection
```

[http://thedarkmaster.wordpress.com/2007/08/10/solving-video-playback-problems-in-compiz-fusion-beryl/](http://thedarkmaster.wordpress.com/2007/08/10/solving-video-playback-problems-in-compiz-fusion-beryl/)

---

### Post by frogotronic on 2008-02-01
> **cement_head said:**
> Whoops!  This command buggered my suspend/hibernate.  I'd like to reinstall the binary driver, but....that's a bit tricky.  Anyone know how to get the modules rebuilt against the rrunning kernel and all the hooks inserted again?

Thanks,
CH

Here's the fix.  (I actually read the instructions for the install)

Uninstall the modules:
```
sudo dkms remove -m fglrx -v 8.452.1 --all
```

reinstall (rebuild) the driver:
```
sudo dpkg -i xorg-driver-fglrx_8.452.1-1*.deb fglrx-kernel-source_8.452.1-1*.deb fglrx-amdcccle_8.452.1-1*.deb
```

Reboot

Suspend & Hibernate now works.

CTRL+ALT+BCKSPCE doesn't work, but I can live with that

---

### Post by SoulSmasher on 2008-02-01
> **cement_head said:**
> [http://thedarkmaster.wordpress.com/2007/08/10/solving-video-playback-problems-in-compiz-fusion-beryl/](http://thedarkmaster.wordpress.com/2007/08/10/solving-video-playback-problems-in-compiz-fusion-beryl/)

wow thanks, worked at last! picture is a bit blocky though and sometimes it's too laggy (even its software driver it souldnt imo, i think its from ati driver crap), but the point is it's working, much appreciated, thanks :)

now only issue is about games.. *do we have to disable compizfusion if we wanna play games ??*

---

### Post by frogotronic on 2008-02-01
> **SoulSmasher said:**
> wow thanks, worked at last! picture is a bit blocky though and sometimes it's too laggy (even its software driver it souldnt imo, i think its from ati driver crap), but the point is it's working, much appreciated, thanks :)

now only issue is about games.. *do we have to disable compizfusion if we wanna play games ??*

no problem.

I think so - xorg & ATI people are (supposedly) working on the compiz issue; but for now, I think disable is the call.  If you find out different, let us know.

- CH

Happy Viewing      :popcorn:

---

### Post by mech7 on 2008-02-01
They are still crap scrolling is buttslow on x700 mobility... and effects are slow also.

---

### Post by SoulSmasher on 2008-02-01
> **mech7 said:**
> They are still crap scrolling is buttslow on x700 mobility... and effects are slow also.

is xgl installed?

---

### Post by mech7 on 2008-02-02
> **SoulSmasher said:**
> is xgl installed?

Nope

---

### Post by SoulSmasher on 2008-02-02
> **mech7 said:**
> Nope

hm i don't know then, i've mobility x1300 (that is pci-e based) and works just fine...
but if the card is *agp*, new catalyst drivers suck both in windows and linux because of ati's crap performance tweaks

---

### Post by mech7 on 2008-02-02
> **SoulSmasher said:**
> hm i don't know then, i've mobility x1300 (that is pci-e based) and works just fine...
but if the card is *agp*, new catalyst drivers suck both in windows and linux because of ati's crap performance tweaks

Performance in windows is fine.. performance with compiz off also.. it's just crap drivers on linux.. the videocard can easily scroll a page in firefox without lag. No matter if it is agp or pci-e :p

---

### Post by fsweet on 2008-02-03
I just installed Ubuntu 7.10 an i to have a 9800 pro card that i need to install but dont have where to start. went to ati web site and downloaded their Linux x86 drivers but cant install a bin files cause of gedit has not been able to detect the character coding what ever that means?  Any help would be great  PS im new at linux.

---

### Post by H_Plow on 2008-02-03
Did anyone encountered same problem as mine??

- fglrx installed and working "properly";
- compiz working "like a charm"

but..........

TTY console are unaccessible.. :(

Before or after the graphical LOGIN, if I try to access a TTY (CTRL+ALT+F1-F6) the screen goes black (whatever the monitor sync LED remains always ON...not blinking) and I can't neither go back to X (CTRL+ALT+F7-F9) nor switch to another console (CTRL+ALT+F1-F6)...can only hard reboot or ALT+R SIST+S+U+B to reboot.....

I've tried (as suggested in topic #585454) to:

1) unblacklist "vesafb" driver:
$ sudo gedit /etc/modprobe.d/blacklist-framebuffer (and put a # before the vesafb line..);

2) $ sudo gedit /etc/initramfs-tools/modules
and add lines "fbcon" and "vesafb" lines

3) update the init scripts:
$ sudo update-initramfs -u -k all

4) add a vga=XXX as a kernel parameter in /boo/grub/menu.lst

Results are:
- I can see usplash (but this wasn't a problem yet before...)
- I can see "text lines" (system messages) during bootup... 
- I CANNOT STILL ACCESS THOSE FU**IN TTY CONSOLES...like before!!! :(

This is rather frustrating.... :mad:
Any suggestion from the experts?
Thanks.

---

### Post by CrossCrucial on 2008-02-08
> **sloggerkhan said:**
> I can't even run a video player trying to use XV, and on my computer, I don't think opengl playback is that great. As I mentioned before, subtitles seem to not work with xine, there's a clear video vsync problem using open gl for video, and mplayer throws error messages every time I start to play something. Mplayer at least shows subs, but they seem stuck at 14pt point font or something. Just really odd.

I had this problem with subtitles and opengl as well. Until I changed the OpenGL Renderer to 2d_tex

---

### Post by fcorourke on 2008-02-08
I no longer can run U buntu 7.10  ----- 'NO SUPPORT" -- so I am going to stay an unhappy windows XP user as I can access all USB drives [except Linux hard drive]  Surf and I for one do not see an advantage to Ubuntu. This NO SUPPORT & now you see a drive and next reboot you are NOT """ROOT' & this is the way to go? I do not love Windows [I did like 3.1] -- but without "SUDO" 8 times a day -- I guess windows is the default. 50 + hours just trying to get things working completely seems enough. I might try Knoppix as it can not lead in any worse direction.. Guess I am just lazy. Know I am tired of RE-installs to fix my problem and then add all the little fixes. I wil keep putting on older simple machines with no external drives as it does extremely well.

       Fred   :(

---

### Post by Dandeloreon on 2008-02-08
I tried gutsy, version 7.10, and it works fine, of course i did not use the gui installer to install it. only hassle with the driver compiz does not work right nnow, but that is due to me using Dual monitors, and ocassionaly i get a weird boot up/shutdown screen where it's clearly not easily read on my monitor.

---

### Post by portach king on 2008-02-09
Running 8.1 using the 2.6.24 kernel on my ati 200m xpress.
Good and bad.
For one, it's nice to be able to run compiz without having to install xgl (seemingly). Sure speeds up my bootup. Haven't tested the hibernate/suspend modes yet.
However, I do find that it runs a little more sluggishly than before. Animations seem to take a second to start, once the do they run fine (very smoothly), but there's a small moment of jerkieness there at the begining of each animation (for example while minimizing) which really ruins the effect. Firefox also seems to be effected, scrolling is very poor. Anybody else come across these and know of any solutions?   : )

---

### Post by cnr437 on 2008-02-09
x1400, dell 6400, 7.10 and it still doesnt work properly on aiglx as much comfort as it was xgl,
there are some cross cutting edge lines when I animate or use cube effect, you can see it easier in videos which has fast scenes. There should be more reliable version of this driver, and sure that ati works much on that, thank everyone...

---

### Post by portach king on 2008-02-09
Well, 
Susped/Hibernate aren't working for me. 
But I've discovered another issue now. I can't get video playback while running compiz. It's fine in metacity, but as soon as I activate compiz I get a black image where the video should be. I can even hear the audio. Anybody else with this slightly amusing problem?

---

### Post by X_melo on 2008-02-10
A nightmare!
I tryed open drivers and all work fine and fast... but, cause of my 9800SE, screen is full of artefact (I think drivers see my graphic board like 9800 PRO and enable all engines).
After upgrade to 8.1 compiz is not usable, video don't work fine, Crtl-Alt-Bkspace don't exit session but leave a still image of empty desktop. Only mode to restart is reset button!! Exit session command is the same....
and a lot o big and little bugs.
A total disaster... like my english..

---

### Post by H_Plow on 2008-02-12
Find better solution to any fglrx/ATI problem !!!

SAY "BYE BYE ATI" !!!  :lolflag:

GOOD LUCK !!

---

