---
title: "Installing Asus AH3450 ATI Radon HD3450 video card"
date: 2008-11-17
forum: Multimedia Software
---

### Post by Eddie Wilson on 2008-11-17
Good Day,
Well I've search all the forums and found no help with this. I upgraded my video card from an nVidia to an ATI. On my Ubuntu 8.10 install it went well. I just disabled the nVidia drivers, shutdown, replaced my video card, started back up and chose the ATI drivers. Thats all there was to it. On my Ubuntu 8.04 install I tried the same thing and it will not work. It seem to not be picking up the new ATI card. I don't want to do a reinstall of 8.04 because my wife has it set up like she wants it. Can anyone point me in the right direction?
Thanks,
Eddie

---

### Post by Eddie Wilson on 2008-11-17
Well I may have figured out a way to solve this problem. If it works I will let everyone know because people seem to be having a serious problem with this. (Switching from nVidia and setting up ATI video cards.)

---

### Post by helbent forleder on 2008-11-27
So, how did it go?
I tried to 8.04 and 8.10 with that card (8x AGP flavor) and it was a disaster - psychedelic colors - nothing normal. I went to Opensuse 11 - installation was no problem with that card - unfortunately I had other issues with that system (I just wish Ubuntu were easier to configure - in the realm of graphics).
Please let me know if you got things working.:)

---

### Post by nick09 on 2008-11-29
I want to know too as I'm planning on installing the AGP version pretty soon. Though I'm not switching from a nVidia card; its the first card for this system.

---

### Post by markbuntu on 2008-11-29
The drivers in the 8.04 repos are unable to detect that card. agp support was added in the 8.9 driver i believe and the driver in the repos is 8.3 or maybe 8.6. Anyway, you can get a newer driver from ati and just run the installer. 

Some people report problems with the 8.11 driver so get 8.10, it installs automatically. Just be aware that you may need to run it again when you get a kernel update.

---

### Post by nick09 on 2008-11-29
So I can install the drivers now and install the card later?

---

### Post by markbuntu on 2008-11-29
You can download the drivers now, they need to detect the card to work so dont run them until you have the card installed.

---

### Post by helbent forleder on 2008-11-30
Nick09 - if you haven't got the card yet, consider gettibg something else! I wish I had... but I haven't tried markbuntu's suggestion yet. :(

---

### Post by nick09 on 2008-11-30
OK. 

@markbuntu: I have Ibex 8.10 and I have purposed updates setup. Will it be fine to install the card on the system?

---

### Post by markbuntu on 2008-11-30
8.10 has updated drivers so it should work even without proposed. Just make sure you have the desktop visual effects set to none before you try anything.

---

### Post by nick09 on 2008-11-30
Thanks for letting me know. So I can use the special effects with the ATI(non-open source) drivers or can I use the open-source drivers for 3D effects?

---

### Post by Torgas Prim on 2008-11-30
But what about getting ati drivers to work for gaming and such?
Black Screens of Death?
Particle on all desktops?
I have an HD2400 and don't want to revert to my older slower FX5500 which basically is the suckiest nVidia card ever.

---

### Post by nick09 on 2008-11-30
I just play old games such as Warcraft 1 & 2, Quake 3, and other games. Plus most of my gaming is on consoles so I don't have to worry much about how good it is on the PC.

---

### Post by Eddie Wilson on 2008-11-30
I never could get the 8.04 install to work properly with the HD3450 card. I even tried the drivers from ATI with no success. Like I stated the 8.10 installation went well. One thing that I did have to do was to disable Compiz. There was too much jerking with all videos and with 3d games. After I disabled Compiz everything work very well. I really don't blame ATI for this problem or even Ubuntu. I blame Compiz Fusion for being a really inefficient and resource hungry app. Of course people have always had problems with Compiz and 3d games and videos but they seem to be at a standstill. I feel that if distros are going to install Compiz as a default then they should try to cover all bases with performance. And no there are not too many graphic card to test. It seems that they do try to get things right with Nvidia. But that's crap because Nvidia is starting to become one of the most unfriendly open source item you can get. I think its sad that people are asked to change their hardware in order to use a LTS distro.

---

### Post by nick09 on 2008-12-01
OK, all I wanted to know is that it works even without compiz. Thank you for the information Eddie.

---

### Post by nick09 on 2008-12-07
Well the ATI drivers work and the drivers that come with 8.10 works too but it is just a tad bit blurry, so the ATI drivers are recommended from me since they make it easier on the eyes. When you play games or watch videos make sure you disable compiz to get rid of the flicker. The drivers from the Hardware Drivers section add accelerated 3D support to the card and it handles the load from compiz easily. You can even overclock the core and memory from the command line also with the ATI drivers. Just enter aticonfig in the terminal after you install the ATI drivers. The ATI drivers have much more support in the refresh rate and the resolutions. Great card so far for me.

---

### Post by Torgas Prim on 2008-12-08
I just tried the newest PC OS live cd....no black screen of death and very fast.
I might give it a try since it is based on ubuntu also
:D

---

### Post by helbent forleder on 2008-12-09
So it must depend on some other things too... for me it simply doesn't work... not at all.

---

### Post by Master Letch on 2008-12-22
Hey I recently Switched from Nvidia to Ati

I'm just wondering where I can find these linux compatible drivers for the Asus AH3450 ATI Radon HD3450 (Sadly I'm stuck at a 800 x 640 res and have had no luck finding them, all I find is the pci equivelents)

---

### Post by Eddie Wilson on 2008-12-22
> **Master Letch said:**
> Hey I recently Switched from Nvidia to Ati

I'm just wondering where I can find these linux compatible drivers for the Asus AH3450 ATI Radon HD3450 (Sadly I'm stuck at a 800 x 640 res and have had no luck finding them, all I find is the pci equivelents)

Use the link below. The Ubuntu repositories have the 8.11 version, but you can download the newest driver from ATI/AMD. They also have good instructions for installing. I have the same card and Asus has nothing. These drivers work well.:mrgreen:

[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

---

### Post by Master Letch on 2008-12-22
I've dled the latest version of the drivers from ati, I'm having very little luck installing them using commandline (so I've looked towards the repositories) just wondering if there is an easier way to install the drivers (I only need basic ones with opengl support)

---

### Post by markbuntu on 2008-12-22
Before doing anything with the ati drivers you need to turn your desktop visual effects (compiz) off to avoid serious problems if anything goes wrong. You can do this by right clicking anywhere on the desktop and choosing change desktop background/visual effects/none.

The only way I found to get the ati driver properly installed since the 8.10 driver is to make the installer exectuable by right clicking on it and choosing properties/permissions and clicking on the little box next to Execute and then open a terminal and cd to the directory it is in and run it as root

cd Desktop

sudo ./ati-driver-installer-blah blah blah

This works for any driver 8.10 and later on Hardy and the 8.12 Driver for Intrepid. You get the 8.11 driver in Intrepid when you use the Hardware Manager. 

If you have an older driver you need to uninstall it. If you got it with Hardware Manager you can remove it with Synaptic. Just search fglrx and choose all the fglrx packages and choose remove completely. If you got it with Envy, use envy to completely remove it. If you installed it from the ati site open a terminal and cd to /usr/share/ati and run

sudo sh./fglrx-uninstall.sh

After installing the new driver, if you did not get any error messages, you need to reboot to load the new kernel modules. If you get a black screen after reboot you can run

sudo aticonfig --f

from the command line. Then reboot again. Once you get back to your desktop you can use the Catalyst Control Center to set up the driver and your screen(s). There are more options available in aticonfig

aticonfig --help

that is what I know about installing the drivers from ati.

---

### Post by nick09 on 2008-12-24
You can find the drivers in a much more safer fashion by going to System --> Administration --> Hardware Drivers on Ubuntu. I got the drivers for my computer that way. Installing from the command line is a last option to use.

---

### Post by Torgas Prim on 2009-01-21
Well OMFG I actually got ATI drivers to work now!
I just reinstalled 8.04 and updated it.
Then I used the restricted drivers instead of Envy and voile'
my games work great!
Getting up to 43fps in Guild Wars.
:D

---

### Post by TVMA on 2009-01-21
For those having flicker problems:

I have the ATI HD4850, and I was suffering from having the screen flicker during video playback while compiz settings were running. The bitch of it is, is that I also run AWN (avant window navigator) because I love having the dock, but don't want a panel at the bottom of my screen.

Well, if you set the appearance settings to "none", essentially disabling compiz, the video playback is fine, but then my AWN dock disappears because I guess it uses those 3D graphics to run the bar, this is not good for me. So I did some digging and found a fix:

type gstreamer-properties in terminal

 (Applications > Accessories in Ubuntu) and go to the video tab. Under Default Output, choose X Window System (no Xv).

This worked. No video playback flicker problems in Totem. Still having problems with VLC, but VLC has been going downhill IMHO lately anyways, so I hope this helps someone out!

cheers,

---

### Post by markbuntu on 2009-01-22
With vlc choose gstreamer instead of xine.

---

### Post by zika on 2009-01-22
**VLC**: Tools->Preferences->Video->X11

---

