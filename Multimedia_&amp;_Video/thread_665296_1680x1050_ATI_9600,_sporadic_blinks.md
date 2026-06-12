---
title: "1680x1050 ATI 9600, sporadic blinks"
date: 2008-01-12
forum: Multimedia &amp; Video
---

### Post by BMWDriver on 2008-01-12
Hi,

Well, I get blinks from the screen turning black. It doesn't seem to matter what driver I use - ati or fglrx. I've also tried installing with Envy, but Catalyst does not recognize 1680x1050. I can't find any info on Catalyst for that. Changing xorg.conf doesn't influence Catalyst at all.

So, I'm sure it's not a hardware issue since I've no problems with the screen on Windows XP, and the other modes I've used on Ubuntu show no problem whatsoever. 

The LCD is a Samsung 225BW hooked up on DVI.

I've tried a lot of things with xorg.conf, but nothing remedies it.

The blinks seem to happen when there is a lot of graphic activity. When I start moving windows around for example. I can also be a good while without a blink.

Anyone have a clue ? Could it be X, or the drivers ? Or is 1680 just a jinxed resolution ?

---

### Post by tospo on 2008-01-12
Hi BMWDriver,

You might be interested in my thread here:
[http://ubuntuforums.org/showthread.php?t=662278&highlight=ati+catalyst](http://ubuntuforums.org/showthread.php?t=662278&highlight=ati+catalyst)
I had trouble with my widescreen monitor too - the correct resolution wasn' showing up in ATI catalyst - and it was suggested to install an earlier version of the ATI driver software (7.11 instead of 7.12) which did the trick for me. Maybe it also helps with your blinking?

---

### Post by BMWDriver on 2008-01-12
Hi Tospo. Sounds good, I'll give it a shot and report back.

---

### Post by BMWDriver on 2008-01-12
Indeed, installing 7.11 solved the blinking. I'm minus the neat 3D desktop special effects, but at least (so far in the last 30 minutes)** the screen does not blink anymore !**

In superuser mode, first reset the xserver:
> [FONT="Courier New"]$ dpkg-reconfigure -phigh xserver-xorg[/FONT]
Then switch to the directory where the 7.11 Catalyst was downloaded, and :
> [FONT="Courier New"]$ chmod +x ati-driver-installer-7-11-x86.x86_64.run
$ ./ati-driver-installer-7-11-x86.x86_64.run[/FONT]

DON'T REBOOT YET ! just follow the instructions for automatic installation for X Server 7.01...
Then go back to the console and initialise the driver, then set the resolution of the screen:

> [FONT="Courier New"]$ aticonfig --initial
$ aticonfig --resolution=0,1680x1050[/FONT]


---

### Post by tospo on 2008-01-13
Glad that it worked for you too. I would like to thank "Dracheschreck" for that one.
 No, the 3D eye candy doesn't work in that version but I really don't care about that too much. 
My only problem is that although I can set the correct resolution in the ATI catalyst control center now - and it all works fine - it doesn't stick. Next time I boot I get a very low resolution again and I have to change it again in the ATI catalyst. My xorg.conf contains the correct resolution but it doesn't seem to be used.
Do you have the same problem or is it only me?

---

### Post by rune0077 on 2008-01-13
Have you tried setting it under System > Preferences > Screen Resolution.

It can also be set in System > Administration > Screens & Graphics (here you should also make sure the proper monitor is selected).

---

### Post by tospo on 2008-01-13
The system settings menu doesn't offer me the correct resolution, even after installing the correct driver. Only the ATI control center lets me choose 1680x1050.

---

### Post by rune0077 on 2008-01-13
You should try this: in System > Administration > Screens and Graphics, instead of selecting your monitor model, select generic model, and then at the very bottom of the list select plug n' play. Also be sure to check the widescreen box. This should allow you to choose all widescreen resolutions.

---

### Post by tospo on 2008-01-13
Thanks rune0077,  I gave that a go. It's slightly different on my machine because I'm on KDE desktop but here his what I did:
System settings -> Monitor and Display, entered Administrator Mode and then -> Hardware
Selected the primary monitor and hit "configure", there I first selected "Generic LCD 1680x1050" and (bottom of the screen) "Widescreen". Then I hit "detect" and the monitor selection automaticaly changes to "Plug and Play". Now the monitor is identified as <plug'n'play, widescreen> in the hardware tab.
With this setting I CAN now actually select 1680 x 1050 @ 60Hz from the size-orientation and positioning tab. I then get a message that I have to restart for these settings but when I do that it just simply comes back with the good old 640 x 480 resolution and now I can only select up to 1280 x 1024. The monitor is still identified as  <plug'n'play, widescreen> on the hardware tab.
I also tried to do this without the auto detect and leave it on "generic LCD 1680x1050" but when I restart I get a mess of a picture and I had to go into recovery mode and exchange the xorg.conf for the previous version.
Apparently, this whole thing seems to have uninstalled the ATI drivers, so that I can't even start the ATI control center right now. I'll re-install the driver and try again.
Any idea what's going on here?

---

### Post by tospo on 2008-01-13
ok, I'm at least back to square one: I still have to reset my resolution every time I start the desktop but at least it works again. 
In the hardware tab of "Monitor & Display" my video card is identified as "VESA driver generic" and the monitor is (again) "unknown". I tried to change the setting for the video card to ATI radeon but that again left me with X not even starting.

---

### Post by rune0077 on 2008-01-13
The method you described above worked for me. My ATI card also gave me tons of problems and Gnome refused to acknowledge my monitors resolutions. When I had it set as plug n' play everything began working fine. 

Odd that a restart would mess it up for you. You could try changing the driver to ATI *without* changing the resolution, then restart to see if it'll let you. Then you can try changing the resolution through Screen Resolution (not sure what it's called in KDE), which doesn't require a restart as far as I know. Or it may just screw things up again, so it's your choice.

---

### Post by BMWDriver on 2008-01-13
Actually, I went further because I really like the eye candy. However, it seems you had to get rid of the MESA drivers that loaded instead of the ATI ones for the 3D - so it was revealed with the command [FONT="Times New Roman"]$ fglrxinfo[/FONT]. So, I tried a couple of procedures, but wound up messing things up, bad  enough that the video was performing rather poorly in plain 2D, no special effects.

So I went ahead, backed up my important files and re-installed Ubuntu. Since I had upgraded online from Feisty, this time I downloaded Gutsy. 

And, lo thee, upon reinstall, update and reboot, I find I need no more the ATI drivers to manage video display. All is working nicely, and with the Compiz effects too ! It took some time, but at least all is good now. 

I have not used Feisty all that much, but I don't recall screen blinks. So I wonder if I was simply the victim of a glitch in the upgrade. Since I don't plan on gaming or such, I don't think I need to fetch the ATI drivers.

So, I believe I'm now on OpenGL as the default installation. I'm not even gonna turn on the proprietary drivers ! =D>

So thanks again Topso for pointing me in the right direction nonetheless.

---

### Post by tospo on 2008-01-14
I played with this a bit more now. I did try to change the driver to ATI and not change the monitor. After rebooting I got the same low resolution as usual. BTW: after all the changes I have made so far to the drivers the system forces me to reboot with the message that this is an untested configuration which requires a full system reboot.
So after the system was back I then selected the Plug'n'Play monitor (the video card was still on ATI Radeon) and I also selected "widescreen". Now I had the corect option for 1680x1050@60Hz (all of this is in the System Monitor & Display menu, not the ATI control center). I selected this resolution, rebooted and the screen was completely messed up (two screen images interlaced). I could more or less read the screen still and it again only offered the incorrect resolutions in the Monitor & Display menu.

Part of the problem is that I don't even know which video card driver to choose because I have these options (administrator mode in Monitor & Display):
ATI Radeon
ATI Radeon 8500
ATI Radeon (fbdev)
ATI Radeon (fglrx)
ATI Radeon (vesa)

For the last three I can also select "Standard" or "Proprietary". I tried the vesa one for the "experiment" above but I have to admit being at a complete loss as to which one I need and of course together with the monitor settings there are numerous combinations to try now. 
Does anybody have a hint which one I should choose for my ATI Radeon X1650? 
I installed the system just a couple of days ago with this monitor already plugged in so I have little hope that it would help me to reinstall.

If the monitor wouldn't work at all I would give up now but I CAN set it to the correct resolution in the ATI control center, this setting is just consistently overwritten by something else.

Interestingly, the login screen seems to be at the correct resolution. The incorrect low resolution is applied after that when with the system startup screen. Does that maybe give a hint? 

I also ran the fglrxinfo command and I get this output:
```
 
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
```

So where are these Mesa drivers coming from now? 

Thanks for your help!

---

### Post by tospo on 2008-01-14
\\:D/ I think I need to have a party because IT FINALLY WORKS :grin:

So I tried a couple of settings and it turns out that what I need to do was set the video card driver (in System Settings -> Monitor & Display, admin mode) to "ATI Radeon (vesa)" and select "PROPRIETARY". This is what I hadn't done before. Of course it makes sense because I donwloaded the proprietary driver from ATI, so I could have tried this a bit earlier but there you go...](*,)
Now it says: ATI Radeon (vesa), driver: fglrx and I got to choose the correct 1680 x 150 @60 Hz.
I rebooted and - \\:D/ - the settings are still there and the resoltuion still correct.

Phew, I almost gave up on that one. Thanks again guys for your help.

---

### Post by BMWDriver on 2008-01-15
UPDATE on my part;

Upon second boot after install, I got the blank screens again. So I went and reinstalled Catalyst 7.11, and I'm now rid of those.

I was able to enable Compiz effects by whitelisting my ATI card as described in the Desktop Effects forums. So far, everything's enabled, though I still have to see what effects or sideffects will occur.

---

### Post by wheezer on 2008-01-15
> **tospo said:**
> The system settings menu doesn't offer me the correct resolution, even after installing the correct driver. Only the ATI control center lets me choose 1680x1050.

I am totally lost here.
I just got a dell 2208 1680x1050.  I am still running Feisty with a Radeon x-series card. 
I am still a bit of a Linux newb and I cannot even locate the "ATI" control panel.  When I bring up "System > admin > screen resolution, the 1680 option is not there.

So what do i do, exactly, to get this set properly.  Where is ATI control panel, if that's the answer?

---

### Post by BMWDriver on 2008-01-15
You may have to choose the monitor again, and make sure you mark the widescreen checkbox in the same admin menu you mention. If the monitor is not listed, insert the CD-Rom that came with your monitor.

The ATI control center Tospo refers to is the Catalyst Control Center that comes with the installation of ATI's latest drivers. ATI has only made Catalyst available to Linux in the last two versions of their drivers, which are now Catalyst 7.11 and 7.12. Before that, only the drivers were shipped. 

To confuse you some more, Catalyst 7.11 contains driver #8.433, and Catalyst 7.12 has driver #8.443. ATI drivers are available without Catalyst as well. You can also enable ATI proprietary drivers under "System>Admin>Proprietary Drivers". But I would not do that at this point.

**I don't recommend installing Catalyst at this point. Just make sure your screen shows up in the screen selection as I said above.** Catalyst is only available via download from ATI's website.

---

### Post by wheezer on 2008-01-15
Well,. to add insult to injury, i upgraded to Gutsy.  I had a ton of errors.  After it finished, I ran "Check" and it seems to fix them, and a reboot worked.  But my "Logout" button has a Red X icon, and I cannot fix it.  My Screen resolution options remain the same. Nothing for 1680.  What now? 

1) Should I run the Live CD repair, perhaps, to fix the missing icon?

2) What do I do now for ATI? I have this shiney new wide monitor running at the wrong res

---

### Post by BMWDriver on 2008-01-16
Well, I can't help you with the icon. My suspicion is that it is related to the desktop theme, and that it is in fact how the button should look like. You could always post a screenshot of it in the Desktop portion of the forum. 

As far as your screen goes, did you re-specify the monitor as I said above ?

If so, try the following to install the latest ATI drivers:

> _Enabling the "restricted" Repository:_ 

Make sure the restricted repository is enabled in /etc/apt/sources.list or this guide will not work!  To do so:

System > Administration > Software Sources. Check "Proprietary Drivers for Devices (Restricted)" box. 

Installation 

For most users it won't be necessary to go into installation and configuration details of the driver. Ubuntu 7.10 (Gutsy) provides a notification saying that there are restricted drivers available. You just have to go there (Restricted Drivers Manager) and enable the "ATI accelerated graphics driver". Ubuntu will then install and configure the driver for you. If this does not provide the optimal solution you were looking for, please read ahead.

If that fails, go here and choose your options (it's the rest of the excerpt above): 
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")

---

### Post by rune0077 on 2008-01-16
Don't select your own monitor-model, that has never worked for me. Instead, select Generic > Plug n' Play and, as said, remember to check to widescreen mark. That should give you lots more screen resolutions to pick from.

---

### Post by BMWDriver on 2008-01-16
> **rune0077 said:**
> Don't select your own monitor-model, that has never worked for me. Instead, select Generic > Plug n' Play and, as said, remember to check to widescreen mark. That should give you lots more screen resolutions to pick from.

Good point. And easy too !

---

