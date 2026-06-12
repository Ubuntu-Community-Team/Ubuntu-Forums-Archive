---
title: "NV6 Nvidia Vanta/lt xorg.conf issues"
date: 2009-06-20
forum: Multimedia Software
---

### Post by Carn443 on 2009-06-20
I've lurked around the forum for a while now looking for an answer to my Nvidia driver/ Card woes to little avail but to make things worse. Ok, here's my problem: My original  xorg.conf is not seeing my vid card or my monitor or much else. I would also like to play starcraft with wine but a stable system is my priority. (I think that's an opengl issue but I'm not sure; I think that may be fixed when I figure this out.) When I run:
```
lspci | grep VGA
``` I get: ```
01:00.0 VGA compatible controller: nVidia Corporation NV6 [Vanta/Vanta LT] (rev 15)
``` Here's my xorg.conf: ```
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```So I went ahead and used the Nvidia X server settings in System->Administration and after I added the driver line to my xorg.conf it looked good enough so I rebooted.(I'll get back to you on the specifics of the alterations after I reboot again.) While booting up I get a message similar to ```
(EE) No devices detected
(EE) No modules or sumesuch
(EE) Incorect driver's
Etc etc
```I can't remember it exactly. Now my resolutions low and I think the refresh rate's on my monitor's messed up.  Allright, so now I suspect my driver's are at fault. After looking through the board I found a guide on how to install the nvidia legacy drivers. The package they had in the guide was:```
nvidia-glx-legacy
``` Now those packages have been replaced by ```
nvidia-glx-96 nvidia-glx-71 nvidia-glx-180 nvidia-glx-173
``` Now I'm not sure which package to use or where to go. I've installed the ```
NVIDIA-Linux-x86-71.86.09-pkg1.run
``` drivers from nvidia's drivers website to no real effect; maybe I did that incorrectly but I don't think so. If you guys could point me in the gerneral direction it would be much apreciated.

---

### Post by Carn443 on 2009-06-20
Ok, here's my nvidia x server xorg.conf:
```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by Carn443 on 2009-06-20
My ubuntu release is ```
Distributor ID:    Ubuntu
Description:    Ubuntu 9.04
Release:    9.04
Codename:    jaunty

```And here is the exact error message when I use my nvidia X server xorg:```
Ubuntu is running in low-graphics mode
-The following error was encountered you may need to update your configuration to solve this.
--(EE) Failed to load module "type1" (module does not exist,0)
--(EE) Failed to load module "freetype" (module does not exist,0)
--(EE) No devices detected.
```Ok I've tried deleting the excess module's and that works but I still have the no devices detected error. If it helps I also keep getting this message even when I've followed the directions ```
 You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 
``` I'm guessing that's the driver issue though.

---

### Post by SteveDee on 2009-06-20
Carn443 I don't have experience with your graphics card but here are a couple of general points.

Support for Nvidia cards in 'buntu is pretty good. I would start by running System > Administrator > Hardware Drivers and activate the [first] recommended driver. If you have a list of possibles then try them one at a time, rebooting each time to gauge their performance.

Generally you cannot use System > Administrator > Nvidia X Server Settings straight from the menu to make changes to your system. This is because you need root access. So from a terminal run "gksu nvidia-settings" whenever you need to make changes.

Only fiddle with xorg.conf as a last resort.

---

### Post by Zaiken on 2009-08-02
I have been having the same problem, The recommended drivers dont seem to work no matter how many ways I tried to install them. In the end I tried EnvyNG, used it to uninstall the old drivers first, then restarted and let it autodetect and reinstall new drivers. Now glx is working fine but its only running at 800x600. Ill try to tweak it today and tell ya how it works out.

---

### Post by Zaiken on 2009-08-02
ok got it working, at first i tried changing the res with a display subsection under the screen section of my xorg.config, that didnt work, and I knew the card was setup and seem to be workin, SO i figured maybe my moniter wasn't setup right. I opened up usr/share/applications/screens and graphics selected a generic moniter with 1024*768 and logged back in. now everything seems to work fine. I think they should put a shortcut to screens and graphics in the control panel, would make things easier in my opinion.

---

### Post by Flash__Gordon on 2009-10-17
I too have a NV6 Nvidia Vanta graphics card on my wives computer and am unable to get the accelerated drivers functioning. I have tried the "restricted hardware" route (which worked fine on my own system with a Gforce 7300GT card but on the system with the vanta there is nothing listed in the "restricted hardware" window. No drivers offered just blank. I tried then with EnvyNG and it identified the 71 drivers and after doing its thing requested a restart and upon restart after the login I receive the following message. 

(EE) Failed to load /usr/lib/xorg/modules/drivers//nvidia_drv.so
(EE) Failed to load module "nvidia" (loader failed, 7)
(EE) No drivers available


I have to revert to generic setup and reboot. Any ideas or help would be appreciated as this system is a compaq and due to its small layout I can't put any regular sized graphics card in ( normal cards are taller that available space). 

The system in question is a Compaq EVO with a P4 1.8 Ghz cpu, 768 MB Ram, Ubuntu 9.04 Jaunty and Nvidia Vanta NV6 Rev 15

Thanks

---

### Post by Majki-Fajki on 2009-12-22
The story is about xorg - which is incapable to use vantaLT and official Nvidia drivers.


> The 71 and 96 series of proprietary nVidia drivers, as provided by the nvidia-glx-legacy and nvidia-glx packages in Ubuntu 8.04 LTS, are not compatible with the X.Org included in Ubuntu 8.10. Users with the nVidia TNT, TNT2, TNT Ultra, GeForce, GeForce2, GeForce3, and GeForce4 chipsets are affected and will be transitioned on upgrade to the free nv driver instead. This driver does not support 3D acceleration. 

Users of other nVidia chipsets that are supported by the 173 or 177 driver series will be transitioned to the nvidia-glx-173 or nvidia-glx-177 package instead. However, unlike drivers 96 and 71, drivers 173 and 177 are only compatible with CPUs that support SSE (e.g. Intel Pentium III, AMD Athlon XP or higher). Systems with older CPUs will also be transitioned to the nv driver on upgrade.


Source: [http://www.ubuntu.com/getubuntu/releasenotes/810#nVidia%20%22legacy%22%20video%20support](http://www.ubuntu.com/getubuntu/releasenotes/810#nVidia%20%22legacy%22%20video%20support)


Good luck. 

I still have machine witch Ubuntu 8.04, becouse I have no idea, how to run nvidia smoothly on newer versions.

---

### Post by Flash__Gordon on 2009-12-22
> **Majki-Fajki said:**
> The story is about xorg - which is incapable to use vantaLT and official Nvidia drivers.





Source: [http://www.ubuntu.com/getubuntu/releasenotes/810#nVidia%20%22legacy%22%20video%20support](http://www.ubuntu.com/getubuntu/releasenotes/810#nVidia%20%22legacy%22%20video%20support)


Good luck. 

I still have machine witch Ubuntu 8.04, becouse I have no idea, how to run nvidia smoothly on newer versions.

 Thanks for the information. I have since upgraded the computer in question (which was my wife's) to a newer system with a tower. Put in a 6200 Nvidia card and Ubuntu 9.04 with ext4 fs and all is well. The Vanta was a low end card anyway.

---

### Post by Kraust on 2009-12-22
To be more exact, the nvidia drivers for this card and any legacy that relies on the 71 drivers are not available to use. You need to use the vesa or nv drivers which can be located through Synaptic.

These drivers do not have 3D support at all and there's nothing you can do about that. Because of the lack of 3D support somethings like Compiz will not work on this Card.

Furthermore, I used this card for some 7 yesrs before upgrading to a 7300GT (Somewhere around last month). If there are any more questions I would be happy to answer them.

---

### Post by Flash__Gordon on 2009-12-22
> **Kraust said:**
> To be more exact, the nvidia drivers for this card and any legacy that relies on the 71 drivers are not available to use. You need to use the vesa or nv drivers which can be located through Synaptic.

These drivers do not have 3D support at all and there's nothing you can do about that. Because of the lack of 3D support somethings like Compiz will not work on this Card.

Furthermore, I used this card for some 7 yesrs before upgrading to a 7300GT (Somewhere around last month). If there are any more questions I would be happy to answer them.

 Yes that is what I have concluded as well. Problem was I wanted 3d support for that computer so as I have previously stated, I upgraded to one I could install a newer card. The Vanta worked great as far as a video card goes, just no 3d support under linux:( I use a 7300GT on my computer and it works great. I have put a 6200 on my wife's and she is happy with it. Both work as they should under linux and via wine I have been able to play most games (ie: return to castle wolfenstien, Sin, etc.) I haven't tried Half-life 2 yet but it is on the list. :P

---

### Post by houseworkshy on 2009-12-22
I had issues with this and found a fix here

[http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html](http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html)

A search for nvidia on the site I've linked to brings up quite a bit more too.

---

### Post by Majki-Fajki on 2009-12-23
I have a question. 


Ubu 9.10 - will it work smooth enough with nouveau?

I have not tried for a long time with a new Ubu on Vanta, so any info?

---

### Post by narcisgarcia on 2010-03-11
Both methods tried with Ubuntu 9.10 (Karmic) in a "Compaq Evo D500", but no success.
The driver provided by NVIDIA works bad, and the packages in ppa:nvidia-vdpau/ppa repository haven't any better effect.

Can't use Compiz nor any GLX game, and Youtube's videos are shown frame-to-frame.

---

### Post by manolomanolo on 2010-07-11
Hi to all.

I upgraded from 9.10 to 10.04 and my video card is not working smoothly

```
VGA compatible controller: nVidia Corporation NV6 [Vanta/Vanta LT] (rev 15)

```

I removed the noveau drivers and installed those
[http://www.nvidia.com/object/linux_display_ia32_71.86.13.html]("http://www.nvidia.com/object/linux_display_ia32_71.86.13.html")

less /etc/X11/xorg.conf
```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

Any suggestion, please?
Thanks.

---

### Post by cascade9 on 2010-07-11
> **Kraust said:**
> To be more exact, the nvidia drivers for this card and any legacy that relies on the 71 drivers are not available to use. You need to use the vesa or nv drivers which can be located through Synaptic.

These drivers do not have 3D support at all and there's nothing you can do about that. Because of the lack of 3D support somethings like Compiz will not work on this Card.

Furthermore, I used this card for some 7 yesrs before upgrading to a 7300GT (Somewhere around last month). If there are any more questions I would be happy to answer them.

There is your answer manolomanolo. 

The Vanta uses the 71.xx drivers, and according to Kraust (and alot of other posts around the forum) the 71.xx drivers cannot be used on newer versions of ubuntu (from 8.10 onward IIRC).

---

### Post by manolomanolo on 2010-07-11
cascade9, thanks for your reply.

Looking for the drivers in Synaptic I found **xserver-xorg-video-vesa** is already installed.
Looking for nv I find a lot of stuff and I don't know what to choose.

Any suggestion, please?

---

### Post by cascade9 on 2010-07-12
The nouveau drivers are probably your best choice.

---

### Post by manolomanolo on 2010-07-12
cascade9, how to make the noveau drivers work properly? I remark that my problem was just with those drivers not working properly (scratchy and slow videos)

---

### Post by cascade9 on 2010-07-12
I'm not quite sure what you mean by 'scratchy' but slow, I'm not suprised...the vanta is a 1999 video card. 

I doubt that vesa or nv will be any better than the nouveau drivers.

---

### Post by manolomanolo on 2010-07-12
Scratchy is the opposite of "fluent".

Again, as I said in a previous message, how to install the "nv" drivers?

---

### Post by cascade9 on 2010-07-12
I'm not 100% sure. 
If you have an xorg.conf file, just get the xserver-xorg-video-nv package, then edit the xorg.conf file so that instead of 'nvidia' or 'noveau' is has 'nv'

---

### Post by dimeotane on 2010-08-26
I'm had a similar issue, and setting up an older surplus system (Compaq EVO) with a Vanta video card (nVidia Corporation NV6 [Vanta/Vanta LT] (rev 15)). I've prepared a Ubuntu system to display video on my HDTV Sony Bravia EX700.  When I display 1280x720 DVD video with it on the HDTV I frequently see a horizontal line where the image jumps halfway down the screen during motion.  Can't quite describe it, but it looks like the video card is having trouble displaying the DVD/DIVX video properly.  Any way to fix / improve this issue?


Using the 'nv' driver in xorg.conf seems to let the card detect the HDTV's available resolutions, but 'nvidia' doesn't work at all. 

On a fresh install of 10.04 it gave me a xorg dialog box at first boot, where I had to choose low graphics mode.  (strangely enough that ended up being 1080p. So I used the /etc/X11/xorg.conf.failsafe and changed the driver to "nv". 

With the NV driver set in xorg.conf it shows a large choice of available resolutions in System-->preferences-->monitors. But it doesn't detect the monitor name or refresh rates. 

When I set the system to 720p I the screen appears wrong with  'overscan' or incorrect cropping when I press Wide on the HDTV remote.  

I'm hoping to correct this by using xvidtune, and entering the modeline into xorg.conf.  

Since it's such an old surplus system, I don't see the point in buying another PCI graphics card for it. Rather than 'buy more stuff' I hope to get the best video possible from this system for now by tweaking it more if possible. Any suggestions are appreciated. For anyone who's read this far in my post. Thanks!

---

### Post by dimeotane on 2010-08-26
[IMG]http://www.imagepost.eu/images/0/video_test.png[/IMG]

Here's an example of what I'm talking about in my previous post. I see this often in video played on this machine. 
In this example video clip the train is moving fast. Perhaps this is just part of the original encoded file xvid not encoding 24 fps well enough? 
Is this possibly caused by the refresh rate of the video card being too low? Can it be fixed by tweaking the xorg.conf settings somehow?

---

