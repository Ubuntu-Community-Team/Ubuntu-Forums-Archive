---
title: "[SOLVED] ATI + video tearing: Vsync, Antialiasing &amp; AF settings / installation"
date: 2007-12-21
forum: Multimedia &amp; Video
---

### Post by perixx on 2007-12-21
Hello again...

I have tearing problems when watching videos and playing (fast games).... it's most annoying when watching movies.

Since I can't give SMplayer any settings to have it using V-sync, unlike most games, I need to find another way; so, is there an option to set up in xorg.conf, that tells it to use V-Sync by default? If so, what would be an example code?

Also, I'd like to know about settings for AF and AA in Xorg - I'm using an ATI X1950GT...

many thanks,

perixx

---

### Post by perixx on 2007-12-22
By the way, I'm running Mplayer/SMplayer with the 'xv' driver....

---

### Post by perixx on 2007-12-23
*bump*

---

### Post by perixx on 2007-12-24
*bumpagain*

---

### Post by perixx on 2007-12-25
I've heard that Nvidia graphic cards have AA-support natively in Linux, which can be engaged with a certain command in the /etc/X11/xorg.conf file - and that all other (namely ATI) cards have no AA support under Linux at all... is that really true??

perixx

---

### Post by perixx on 2007-12-26
Does somebody know how to enable Vsync and Antialiasing for the Xorg server with ATI cards?

perixx

---

### Post by JohnLM_the_Ghost on 2007-12-28
I have quite a problem with this too.

Technically, it should be done with following commands:

```
sudo aticonfig --sync-vsync=on
```

and one special for video overlay

```
sudo aticonfig --sync-video=on
```

I have not properly tested these, but these are quite safe commands (and makes backup automatically anyways).

My windows don't sync (probably metacity doesn't use vsync)
Don't have any games to test it properly.

I will post if I have any more luck with using these.

---

### Post by perixx on 2007-12-29
Hello John_LM... thanks for your reply!

When I type these commands, I get messages like that:
> sudo aticonfig --sync-video=on
Password:
Warning: Option 'TexturedVideoSync' doesn't affect running session.
Using /etc/X11/xorg.conf

It means that I'm gonna have to restart Ubuntu, for changes are only made to xorg.conf, I suppose?
The only reference to some (new?) 'sync' option is this:
> Section "Device"
	Identifier  "Standardgrafikkarte"
	Driver      "fglrx"
	**Option	    "TexturedVideoSync" "on"**
	BusID       "PCI:1:0:0"
Is it a result of one of your commands?

Can't find any hint on V-sync enabled - even though I've used your commands on the CLI...
I'm not sure if anything changed in respect to the video-playback tearing by now, but it didn't in games, that's for sure (e.g. UT2004).

perixx

---

### Post by perixx on 2008-01-01
Seems I'm making some progress here...

Although I've found reference for a [COLOR="Blue"]**video-playback-tearing / vsync**[/COLOR] 
remedy above and under the link here: 
[http://wiki.cchtml.com/index.php/Aticonfighelp]("http://wiki.cchtml.com/index.php/Aticonfighelp")
it didn't seem to function as expected; to enable video-vsync, using this command is recommended
```
sudo aticonfig --sync-video=on
```
The ATI help-site considers this to do the following
> --sync-video
Enable/disable sync to vsync for AVIVO video.
This option is enabled by default and is used to prevent video tearing. By disabling this option video is free to render as fast as the 3D engine can handle. In the case of choppy video try to disable sync-video.
Because it's said that the option is enabled by default, [COLOR="Red"]**I consider this one as non-functional**[/COLOR] (have read about that several times, too). Perhaps limiting the vertical sync-range for the TFT to a fixed refresh rate will help, but I doubt that... anyway, no vsync for video for now.

As I interprete the information at Aticonfighelp, for [COLOR="Blue"]**enabling vsync in 3D-mode (games and such ONLY)**[/COLOR], the appropriate command is:
```
sudo aticonfig --sync-vsync=on
```
The description reads as follows
> --vs, --sync-vsync={on|off}       
Enable/disable sync buffer swaps with vsync.  Enable this option to prevent tearing during 3D rendering.
I cannot confirm if this one works yet, I've got to make some more gaming tests first.

Maybe it'll turn out that [COLOR="Blue"]**Overlay-settings**[/COLOR] will make some change for the better, regarding the vsync/video-tearing problem, maybe not - I'll test those the other day:
> --ovt, --overlay-type=STRING
Change the overlay for the X server.  STRING can be one of:
opengl
Xv
disable
--ovon, --overlay-on={0|1}
Choose which head the hardware overlay should be visible on. The hardware overlay can be used for either OpenGL, video, pseudo-color or stereo.

A real hard-sought feature for me was **[COLOR="SeaGreen"]Antialiasing (AA)[/COLOR]**; there's 4 commands, but as I see it, only 2 are really important for the average users (like me):
```
sudo aticonfig --fsaa=on
sudo aticonfig --fsaa-samples=4
```
This should enable 4xAA to have a good quality/performance balance... here's the reference from Aticonfighelp:
> --fsaa={on|off}
Enable/disable full scene anti-aliasing.  Enable this option to enhance photo-realism in 3D rendering.  Disable it to get the most accurate 3D mage.
--fs, --fsaa-samples={off,0,2,4,6}
Set the number of FSAA samples per pixel or 2, 4, 6.  off is the same as setting 0 samples.

When looking for the **Anisotropic filtering option (AF)**, I've stumbled upon the problem that my standard fglrx video-drivers, that were installed from the Ubuntu repositories, are by far too old:
> fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1950 Series
OpenGL version string: 2.0.6334 (8.34.8)
 - AF is supported only with driver version higher than 8.42.x or some such. So I've got to update my drivers first (hope for the best) and maybe have a working vsync feature for video playback also afterwards.
I'm gonna use 'ENVY' for that purpose and will report back later how it worked...

Also, I've learned that '**[COLOR="SeaGreen"]amdcccle[/COLOR]** might possibly turn out as what I've been looking for so long - a GUI to manage the most important advanced graphics features of my ATI card. I'll test this one too!

Btw., I guess it shouldn't be any problem to pack all those aticonfig-commands into one for more convenience: 
```
sudo aticonfig --sync-video=on --vs=on --fsaa=on --fsaa-samples=4
```
[COLOR="RoyalBlue"]**Don't forget to reboot after applying those changes; only re-starting the session didn't work for me!**[/COLOR]

There's gonna be a backup created with ".fglrx-0" ending of the xorg.conf file, if things go bad - so it should be perfectly save to use the commands. In the bad case, ```
sudo cp /etc/X11/xorg.conf.fglrx-0 /etc/X11/xorg.conf
sudo /etc/init.d/gdm restart
``` should revert to your original xorg backup and restart the X-server. 

perixx

---

### Post by perixx on 2008-01-02
Well, here I go again - trouble on the way :rolleyes:

'amdcccle' (provided with the ATI proprietary driver package) seems to function the way I need it - if I can get my NEW fglrx-driver's **opengl to work**!!

I used 'Envy' to 'completely uninstall' the old drivers in a first step - here there I had some output about the 'MESA'-package was being installed newly. 
Then I installed the new driver with 'Envy' in a second step; since it didn't seem to compile the first time, I redid the second step - I also had no OPGENGL support (just MESA) and this time it seemed to work. I rebooted into my desktop without probs.

Well, that's it - I'm currently stuck with the infamous opengl 'mesa'-message if doing a ```
fglrxinfo
``` check. Tried several suggestions from the forums:
> - turning off 'AIGLX'
- 'COMPOSITE' was already disabled
- applied an 'aticonfig --initial --input=/etc/X11/xorg.conf --overlay-type=Xv'
- commented out the 'DISABLE=FGLRX' option in /etc/default/linux-restricted-modules-common
- checked 'dmesg | grep agp --> agpgart is installed; I've read somewhere that the ATI-driver doesn't like that being compiled into the kernel module?? :confused: I'm having an ATI x1950gt PCIe anyway...
- checked 'dmesg | grep drm --> no reply; no DRM installed
- tried to remove the 'MESA'-package, but then sorta like half of my apps are gonna being uninstalled as well...

Gonna have to try to install the new driver from hand, eventually... :( 
First, I'll try to remove 'xorg-driver-fglrx', though...


[COLOR="Red"]**Output of  /var/log/Xorg.0.log, I've marked eventually most important relevant lines in red:**[/COLOR]
rem.: I've connected a single TFT with both connectors to my graphic-card, thus, 2 monitors are detected!
> (II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	[COLOR="Red"]compiled for 7.1.0, module version = 8.44.3[/COLOR]
	Module class: X.Org Video Driver

(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.44.3
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.443.1                  
(II) ATI Proprietary Linux Driver Build Date: Dec 19 2007 21:29:14
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset Supported AMD Graphics Processor (0x7288) found
(II) AMD Video driver is running on the exact device targeted for this release
(II) AMD Video driver is signed

[COLOR="Red"]>[/COLOR]
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
[COLOR="Red"]>[/COLOR]
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	[COLOR="Red"]compiled for 7.1.0, module version = 8.44.3[/COLOR]
	ABI class: X.Org Server Extension, version 0.3
(--) fglrx(0): VideoRAM: 262144 kByte, Type: DDR3
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported

(WW) fglrx(0): More than one displays are connected,so clone mode is enabled

(==) fglrx(0): NoAccel = NO
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000001f
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 256 MB
[COLOR="Red"](EE) fglrx(0): [pcie] Failed to gather memory of size 262144Kb for PCIe. Error (-1000)[/COLOR]
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.


[COLOR="Red"]II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. [/COLOR]
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *


(WW) fglrx(0): Textured Video not supported without DRI enabled.
(WW) fglrx(0): Video Overlay not supported on AVIVO based graphics cards. For XVideo support use Option "TexturedVideo".

(II) fglrx(0): Acceleration enabled
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
[COLOR="Red"](II) fglrx(0): Direct rendering disabled[/COLOR]


[COLOR="Red"](EE) AIGLX: Screen 0 is not DRI capable[/COLOR]
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
[COLOR="Red"](II) GLX: Initialized MESA-PROXY GL provider for screen 0[/COLOR]

From what I see, FGLRX was compiled for Xorg 7.**[COLOR="DarkOrange"]1[/COLOR]**.0, but EVERYTHING else for 7.[COLOR="DarkOrange"]**2**[/COLOR].0... that's really strange!
[COLOR="Blue"]**Any help is appreciated..!!**[/COLOR]

perixx

---

### Post by perixx on 2008-01-02
Now, I've tried to uninstall/re-install the 4.443.1 driver from ATI again, first with Envy and then by hand with the command:
```
 bash ./ati-driver-installer-8.443.1-x86.x86_64.run --buildpkg Ubuntu/feisty
```

Both times I do get the error message:
> cp: cannot stat `./debian/compiz-manager': No such file or directory
dh_install: command returned error code 256
make: *** [binary] Error 1
Removing temporary directory: fglrx-install.ZR9489
Does this mean, that I need to have COMPIZ installed to get the installation up and running + the OPENGL-functionality back with the new driver :confused:

Maybe it's just that the experts at ATI have mixed up 'Debian' with 'Ubuntu'.... perhaps they don't pay attention to such unimportant distro's at all - for the driver's officially 'optimized' for Fedora and Suse |-/

Seems like I'm not alone but in for it again :P When will I finally learn to investigate first and install THEN... 
Most probably ATI is to blame again:
[http://www.phoronix.com/forums/showpost.php?p=20735&postcount=24]("http://www.phoronix.com/forums/showpost.php?p=20735&postcount=24")

perixx

---

### Post by perixx on 2008-01-02
:mrgreen: **PROBLEMS ** S O L V E D ** MISSION SUCCESSFUL** :mrgreen:

> fglrxinfoconf
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon X1950 GT
OpenGL version string: 2.1.7170 Release


While wasting more than a whole day, trying to recover my system from the 'infamous OpenGL-Mesa-issue' and attempting to create and install a .deb package out of the 8.443.1 ATI-installer (as trouble was promised otherwise on several posts and blogs) - well, 
_I've really overlooked the most definitely simplest way_ of all: **just running the ATI installer as root **(via 'gksudo Thunar')!!!

**[COLOR="Green"]Everything just fitted into place and worked out-of-the box (!)[/COLOR]**

This was actually simpler than creating a starter for 'amdcccle' on my panel-bar 8^]

Everything necessary can be handled from within AMDCCCLE:
> - setting Antialiasing (AA)
- setting Anisotropy filtering (AF)
- setting dual-screens
- basic colour adjustments
- setting VSYNC (wait for vertical refresh)


The latter seems to pose the **ONLY way to effectively prevent tearing during video-playback**, unless there are video-player-specific options (none other proposed settings in the /etc/xorg.conf showed any significant change so far). 

Unfortunately, tuning VSYNC to 'always on' will only have a positive effect on video-playback, but actually sometimes even worsen tearing in games (like UT2004, but that one looks pretty fine with standard options) and cause some really annoying 'mouse-lag' and performance loss (in-game).
Perhaps someone knows how to deal with that properly...

perixx

---

### Post by JohnLM_the_Ghost on 2008-01-10
I'm glad you sorted at least something out.

Yeah, well commands I posted were quite useless for my PC too. Dunno why they are there anyways (cause they don't work). I suppose there could be some internal X settings what prevents, but have no idea where.

As for "Vsync in Games" I could share my theory why it happens, but not a single workaround. 
The thing might be that amdccc just uses 'Vertical Refresh Rate and screen update rate synchronization' (much like Frame limiter) instead of actual 'Wait for Vertical Retrace'
Kinda old hack in gamedev when you can't access Vsync.
But thats only what I think.

Shame I couldn't be of any more help.

---

### Post by perixx on 2008-01-10
Hi John!

> The thing might be that amdccc just uses 'Vertical Refresh Rate and screen update rate synchronization' (much like Frame limiter) instead of actual 'Wait for Vertical Retrace So these are different methods then? I don't know any details... maybe you can explain a little more thoroughly?

As for the settings... I'm afraid we're fairly down to use what 
ATI and Nvidia have little to offer... the native config-tools that come with the drivers (that's what 'proprietary' actually is all about, isn't it? 

Well, I've had my share of trouble the last 3 days when trying my ATI card and a Nvidia 6800XT, both with the repository- and latest drivers; though I managed to eliminate all difficulties along the way, I'm back to the ATI with Ubuntu's FGLRX drivers (v.8.34) again. They're working with least flaws and are the most compatible of all - the 6800XT would even crash on EVERY 3D app, regardless from what I tried. 

I was even suspecting this card to use more power than my ATI X1950 GT, which could explain a complete hang-up every time I entered the 3D-mode. The thing's only, that the ATI is by far better (and should also be expected to consume more power; I was even wondering how my old trusty 370W psu from BeQuiet still takes it :)) -- 
still, the ATI card has a separate built-in power connector, while the Nvidia drains all it needs directly from the bus... 

BUT I have an ASUS board with EZ-plug, so this SHOULDN'T matter. The only uncertainty that remains in this respect is, when thinking of the power cable connected to the EZ-plug may possibly be overloaded by too many connected devices... 

perixx

---

### Post by JohnLM_the_Ghost on 2008-01-11
Yeah well there are two methods.

I dont know the actual names, but it should give the idea...

1. Frame Limiter (Sometimes falsely referred as Vsync)

It really does (or tries to) synchronize the screen and monitor frame rates, but generally dont take into account the actual time when monitor refreshes. Used on software level, and the effect is strongly application and system dependent. Usually doesnt prevent tearing, but may reduce it considerably.

2. True Vsync (wait for Vretrace)

This is hardware/driver level approach. It does full frame rate and time sychronization, but all screen updating must be given to driver. While it is by far more better than former method, it is a bit harder to code (tending to do more bugs) and may cause all kinds of weird things if driver is not good. (And unfortunately Linux is quite short on good drivers, especiallly ATI's)

as for me, I'm not really intensively searching for a solution for vsync, cause I still use Windows for most part, but would be good to know how to achieve it though.

And Yeah ATI really rules lately, they're faster and cheaper. But then again - already mentioned lack of drivers.

---

### Post by perixx on 2008-01-13
Well, I really have no idea, what the AMDCCCLE's 'VSYNC' option actually does - whether it's just a frame limiter or a real 'wait for vertical retrace' function. Considering the poor performance of this function, it's maybe the first method in use or the second badly implemented, as you stated.

Hm, ATI ruling over Nvidia? Not so sure... cheaper they are, in some cases (with comparable models) - and generally tend to have better video signals - but AFAIK, nothing beats the 8800 series for quite some time, most especially, since the favourable 8800GT was launched by Nvidia... this might change with the new ATI chips that are expected soon, if it's true what rumors tell.

I've already launched a 'rant' to ATI about their ill-designed and poorly performing drivers.... 
if more people would do so, maybe ATI/AMD might pay attention.

perixx

---

### Post by JohnLM_the_Ghost on 2008-01-19
Hope ATI hears your 'rant'!

As for ATI being a little bit better (my subjective opinion, of course)... I usually measure Raw Power per one money unit (whatever anyone uses).
Geforce 8800GT is cool, but Radeon HD2600XT (GDDR4 version) with its 2.2Ghz Memory Clock is also cool. However I am not stating that either one performs better!
But let's not make this just another ATI vs. Nvidia Thread! There's too many already!

Besides all that, I guess there's nothing really to do except to wait for a better driver.

---

### Post by perixx on 2008-01-20
> But let's not make this just another ATI vs. Nvidia Thread! There's too many already

So true ;)

But we could kick off another 'Linux vs. Windows' thread ^^ Since it's the Linux drivers that perform so utterly bad and I've also learned that DVD playback isn't as reliable as under XP - under Windows everything's pretty much sunshine, sorry to say but simply true...

In fact, I've re-launched my long sleeping XP Pro Mega-Registry'n'Tweaks-Collection project again...
I'm aiming to configure XP as secure and stable as possible and then launch a fast and lean internet gaming platform.

perixx

---

### Post by perixx on 2008-02-09
Analog to post #12 in this thread, I wanted to report back after reinstalling several different ATI proprietary driver versions for my X1950 GT. 

So far, [COLOR="Blue"]I've been able to solve practically all of the troubles[/COLOR] I've encoutered with those - even to recover from differently branded drivers (Nvidia) - as can be seen here: [http://ubuntuforums.org/showthread.php?t=686684]("http://ubuntuforums.org/showthread.php?t=686684") 

I've been running driver versions up to v. 7.11 on my system, which is my current graphics driver. 
[COLOR="Blue"]**Intriguing:**[/COLOR] I was able to get any driver **running** in the end (apart from 8.01), by simply using the **installer** with 'sudo' - 
[COLOR="Red"]**BUT NOT**[/COLOR] with any kind of other solution, like compiling .deb packages and kernel sources myself, as proposed on several help pages! Seems that the xorg-'fglrx' / drm modules aren't compiled properly, then, or whatever. 

Copying it to /home/ and running the installer has the advantage of everything is compiling automatically and all necessary symlinks are being created + the '**amdcccle**'  GUI is installed as well.  
Besides, also removing the drivers was easy enough with ```
sudo sh /usr/share/ati/fglrx-uninstall.sh
``` 

So far, the good news. But contrary to the censing reports of the 'greatly improved performance' of the newer drivers > v. 8.41, I can't agree to this. So far, only 6xAA is supported (at least with my card) and advanced features like temporal AA and HDR rendering aren't implemented at all, obviously. You wouldn't want to use any setting >x4 anyway, as it drawns the performance much more than with the Windows drivers. Even without ANY eyecandy - nice, but not comparable to XP at all.

[COLOR="Red"]**IMPORTANT:**[/COLOR] If you're unsatisfied with your ATI drivers, I suggest you create an account under that links below and/or complain there, to push ATI/AMD a little... **try to be objective and don't hassle/shittalk, though, please!!**
[http://ati.cchtml.com/]("http://ati.cchtml.com/")
[http://support.ati.com/ics/survey/survey.asp?deptID=894&surveyID=508&type=web]("http://support.ati.com/ics/survey/survey.asp?deptID=894&surveyID=508&type=web")

perixx

---

