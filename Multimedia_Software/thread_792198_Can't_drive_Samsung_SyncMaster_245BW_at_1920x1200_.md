---
title: "Can't drive Samsung SyncMaster 245BW at 1920x1200 with nVidia Quadra FX 3450 (64-bit)"
date: 2008-05-12
forum: Multimedia Software
---

### Post by randallecook on 2008-05-12
Sorry for the long title. I wanted to pack in as much information as possible. Here's the story:

At work I received a Dell Precision 490 workstation, which I hooked into my Samsung SyncMaster 245BW monitor with a DVI cable. The computer came with Windows XP, but I wanted to run Ubuntu 64-bit Linux on it. Installation was smooth and fast, and all hardware was recognized, even the nVidia Quadra FX 3450 it came with. Linux simply rocks on this hardware.

After install, the highest resolution I could get was 1280x1024. Ubuntu recognized the nVidia graphics card and asked if I wanted to install the restricted drivers for it. I did, and after doing so I could get 1600x1200 with full compiz effects. Getting there.

The monitor's natural resolution is 1920x1200, and I wanted to run it that way. I have an identical monitor on a machine at home (32-bit AMD Thunderbird, Ubuntu 7.04, nVidia GeForce FX 5200), and it works at 1920x1200 just fine. Others in my office run the same hardware with Windows XP and get full resolution, so it is clearly not a hardware issue.

I read through everything I could find about monitor configuration and tried many things:

- 'dpkg-reconfigure xserver-xorg' did not help
- the open source driver did not help
- installing the Linux driver from the nVidia site really did not help
- copying modelines found on the web did not help
- using PowerStrip under Windows to generate a modeline did not help

In all cases I either get a relatively low resolution (1024x768 or 800x600) with xorg running in failsafe mode, or something higher, but no 1920x1200. Xorg.0.log generally says "No valid modes for "1920x1200"; removing" and I am back at 1600x1200.

At this point I am out of ideas and am appealing to the community. I suppose giving up and getting a different video card is an option, but I'd like to think that we can use this opportunity to extend Linux's hardware reach. I can post xorg.conf files and log lines if that would help. Thanks.

---

### Post by randallecook on 2008-05-13
One more thing: I also tried the EnvyNG tool. It didn't help either.

Randall

---

### Post by wkulecz on 2008-05-13
Try using an analog cable.  Can't get anything better than 1600x1200 on my Sony with DVI.  But 1920x1200 is great with the VGA analog cable.  Go figure.

DVI appears to be a rip-off to my eyes, expensive, short, stiff cables and no improvement to the image over analog that I can see.

--wally.

---

### Post by cor2y on 2008-05-13
you can try the nvidia tool that comes with the closed drivers
via the terminal ```
sudo nvidia-settings
```
and go to x-server display configuration, see if you can select your default monitor output from there.
If you can then export that setting to the xorg.conf file (theres a setting to do that in nvidia-settings) when you restart you should have that resolution.
Also on another note its always a battle to get the correct res you wish using a Samsung monitor in ubuntu i have no idea why.

---

### Post by Mark Phelps on 2008-05-13
Hey randall -- see you did start a new thread ...

I've see other posts about not being able to get greater than 1600x1200 with DVI connection.  I have the same monitor, and although I AM able to get 1920x1200 with DVI, when I tried to use the Screen Resolution panel to add drivers for the Samsung 245BW, the max resolution the panel would allow was 1600x1200.

So, maybe there's something to this needing to use the analog port to get the higher resolution.  I'll change the connections tonight and try the panel again to see what happens.

I, too, am nervous about going to Hardy because it's been such a struggle to get this monitor working in Gutsy -- and I keep seeing post after post about new Hardy-related video problems.

---

### Post by Mark Phelps on 2008-05-13
Randall:

Sorry to report but there is definitely a problem using this monitor with a digital cable connection and Ubuntu 7.10.  I swapped in an analog cable, and not only was Ubuntu able to detect the resolutions properly, when I added the Samsung 245BW settings to the Screens panel (using the windows .inf file), they actually worked!

When I then swapped back the digital cable -- it all turned to crap again.  Just like last week.  While I was able to select resolutions higher than 1600x1200 in the Screens panel, and confirmed that the xorg.conf file got properly updated, that same file might as well have not existed.  Every time I rebooted or restarted the Xserver, it came up in low res mode!  I even copied back the xorg.conf file that I was using before these experiments -- one that I KNOW worked.  And even then, Ubuntu came up in low res mode.

I was only able to get 1920x1200 back using my digital cable by restoring my /root and associated files from a backup I made last week.

This really sucks!!  I just don't understand how the xorg.conf file can be absolutely correct but still come up in low-res mode!  Perhaps this is why they did away with a lot of the .conf file settings in Hardy.

I'm going to try installing Hardy and testing the Samsung there.  But if I have no better luck -- it goes back!

---

### Post by wkulecz on 2008-05-14
Why are you in love with the DVI cable if it don't work and the analog one does?

Its not confined to the Samsung monitor, I have the same issue with my Sony and am happy runing 1920x1600 with the analog cable since it works!

--wally.

---

### Post by randallecook on 2008-05-14
Thanks for your suggestions, Mark, cor2y, and Wally, and sorry you got roped into that system restore, Mark. Way beyond the call of duty there.

BTW, in my travails I sometimes ended up in low resolution mode as well. Restoring my xorg.conf did not help. I discovered that there was an /etc/X11/xorg.failsafe file (or something like that) that seemed to override the main xorg.conf. Deleting that failsafe file and restarting X made xorg.conf be respected again.

Cor2y, I tried 'sudo nvidia-settings', and while I could view a lot of settings, the 1920x1200 resolution option was not available. I set the resolution to the "auto" setting, had the nVidia control panel modify xorg.conf, and restarted X, but no luck. I'm still at 1600x1200, but Xorg.0.log is no longer reporting errors or problems.

My Quadra FX 3450 card has no analog output (well s-video, but that doesn't count). It has two DVI connectors, only one of which I can get a signal on. Frankly, I would prefer analog, since I have an analog KVM that I need to support some older systems under my desk. And I find that with good quality components, modern monitors do an excellent job of aligning analog video with the LCD pixels. DVI doesn't help much.

I have a simple adapter that looks to be able to split a DVI cable into another DVI cable and a VGA analog cable. I tried it on both DVI connectors, and could not get analog on either. It is possible that the card is simply not putting an analog signal on the analog pins on its DVI connectors, but I don't have the equipment to check that.

A colleague has identical hardware and is able to drive his monitor at 1920x1200 with a DVI cable, under Windows XP, of course.

Any other suggestions, guys? I'm sorry this is such a stumper.

Randall

---

### Post by Mark Phelps on 2008-05-14
wkulecz:  To answer your question ... when I switch over to the analog cable, every time I boot my machine, every single program shift forces me to press the auto center button ... so ...

When I first boot, the text is displayed off the left side of the screen so I can't see half of it ... press auto center ...

The grub splash screen comes up, items are displayed off the screen ... press auto center ...

The Ubuntu login screen comes up -- login box is displayed off the right side of the screen where I can't see it ... press auto center ...

The Gnome desktop comes up -- off-center ... press auto center ...

Then, when I restart and reboot into any of the other three OS's I'm running on this box ... I get to go through the whole drill again.

With the DVI cable connected, the screen comes up aligned properly every time.  No having to press auto reset again and again.

So, short answer, it's a lot less annoying to use the DVI cable.

---

### Post by wkulecz on 2008-05-15
I solve the resolution change centering issues by using the monitor's menu selections to put it in "native mode" where the 640x480 BIOS screen appears at 1:1 pixel size (no scaling) in the center of the screen etc.  But really, unless something goes wrong I don't need to see anything until my destop boots up -- I have auto login enabled for the default user, and then use the "switch user" to log into my private desktop.  This so I can work around the bug where only the user setup by the installer gets sound.  If I log out the default user, other users added with the "Users and Groups" tool don't get any audio.

Two 8.04 bugs that at least I've found workarounds I can live with.

--wally.

---

### Post by Mark Phelps on 2008-05-15
I'll look into the monitor's "native mode". Thanks.  But, I do need to see the Grub menu selections because I do all my multi-booting from there.

---

### Post by randallecook on 2008-05-15
Victory! I was discussing your responses with a colleague and he could not believe that the card could not produce analog output. I proved it by plugging an analog cable into the splitter and sure enough, no signal. We then took an identical system and plugged an analog monitor into it using my splitter. Sure enough, we got analog video. This made me suspect the analog cable.

We then returned to my machine. We plugged the DVI cable into the socket far from the s-video socket, and plugged the splitter into the DVI socket near the s-video, and plugged a new analog cable into that. Under that configuration, we only got video on the monitor's digital input, and only at 1600x1200. It did prove that the second DVI socket does work, which was news to me.

We surmised that the presence of the DVI connection might be disabling the analog connection, so we shut down and unplugged the DVI cable, leaving only analog. When we restarted, there were some centering problems with the Ubuntu login screen, but once on the desktop we could use the Screen Resolution preference panel to adjust the resolution to 1920x1600. At last!

My colleague still wants to push for full resolution over DVI, but I am content with things as they are. We also never tested the old analog cable alone to see whether it was truly bad or just the presence of the DVI cable disabled it. To leave a complete record for others, I'll try those tests and post my results, along with my xorg.conf file. Some restarts might reveal something about centering problems, too.

Thanks everyone for your help with this. You gave great suggestions. Ubuntu has a great community.

---

### Post by randallecook on 2008-05-15
Victory! I was discussing your responses with a colleague and he could not believe that the card could not produce analog output. I proved it by plugging an analog cable into the splitter and sure enough, no signal. We then took an identical system and plugged an analog monitor into it using my splitter. Sure enough, we got analog video. This made me suspect the analog cable.

We then returned to my machine. We plugged the DVI cable into the socket far from the s-video socket, and plugged the splitter into the DVI socket near the s-video, and plugged a new analog cable into that. Under that configuration, we only got video on the monitor's digital input, and only at 1600x1200. It did prove that the second DVI socket does work, which was news to me.

We surmised that the presence of the DVI connection might be disabling the analog connection, so we shut down and unplugged the DVI cable, leaving only analog. When we restarted, there were some centering problems with the Ubuntu login screen, but once on the desktop we could use the Screen Resolution preference panel to adjust the resolution to 1920x1600. At last!

My colleague still wants to push for full resolution over DVI, but I am content with things as they are. We also never tested the old analog cable alone to see whether it was truly bad or just the presence of the DVI cable disabled it. To leave a complete record for others, I'll try those tests and post my results, along with my xorg.conf file. Some restarts might reveal something about centering problems, too.

Thanks everyone for your help with this. You gave great suggestions. Ubuntu has a great community.

---

### Post by wkulecz on 2008-05-16
I'd filed a bug report on launchpad about the no 1920x1200 over DVI issue.  If you go over and confirm it, specifically that its not unique to GeForce 5500 cards and Sony LCD panels, might help motivate the developers to look into it.

--wally.

---

### Post by Mark Phelps on 2008-05-16
wkulecz:

Sorry, but I went through all the on-screen settings and I was unable to find any "native mode".  So, how do I put the monitor into "native mode"?

Also, I have an ATI X1600 card and a Samsung 245BW monitor, and am having the same 1600x1200 limitation with DVI. So, it's not just the geforce card and Sony monitor.

---

### Post by Mark Phelps on 2008-05-19
Randall:

Installed hardy over the weekend and it works great!  Found the monitor settings right off and offered the ATI restricted drivers.  Enabled the drivers and rebooted.  Have 1920x1200 res using the DVI cable -- no problems!  So, it's a problem with 7.10 that, at least in my case, does not repeat itself in 8.04.

---

### Post by itsjustarumour on 2008-05-19
> **wkulecz said:**
> I'd filed a bug report on launchpad about the no 1920x1200 over DVI issue.  If you go over and confirm it, specifically that its not unique to GeForce 5500 cards and Sony LCD panels, might help motivate the developers to look into it.

--wally.

Hi Wkulecz,
Please could you add a link to your bug report, as I'm having all the same issues outlined in this thread with my Samsung Syncmaster 244T monitor when trying to achieve 1920x1200 on Hardy 8.04 (32-bit with NVidia drivers, GeForce 6800LE)
Thanks in advance,
itsjustarumour

---

### Post by randallecook on 2008-05-21
Hi everybody. Here is some more information:

1. My old analog cable is fine. I just tested it. It must have been the presence of the DVI cable that screwed things up.

2. I also looked for some sort on "native mode" on my monitor and found nothing. Are we all talking about Samsung SyncMaster 245BWs here?

3. I second itsjustarumour's call for a link to the bug report. I suppose I could go look for it, but hey, this is the web. We like links. :)

4. As promised, here's my xorg.conf, for all who care to learn from it:

```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file works with a Samsung SyncMaster 245BW monitor and an 
# nVidia Quadra FX 3450 video card, connected by an analog cable
# via an analog/DVI splitter under Ubuntu 8.04 Hardy Heron. 5/21/08.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"SyncMaster"
	Device		"Generic Video Card"
	SubSection "Display"
		Modes	"1920x1200" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	Option		"AddARGBGLXVisuals"	"True"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	screen		"Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Horizsync	30.0	-	81.0
	Vertrefresh	56.0	-	75.0
	Option		"DPMS"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

```

There. Now it belongs to the ages.

Randall

---

### Post by itsjustarumour on 2008-05-21
> **randallecook said:**
> 3. I second itsjustarumour's call for a link to the bug report. I suppose I could go look for it, but hey, this is the web. We like links. :)

I like links too, although after a while I got impatient and went for a look - but I couldn't find it! :-)

---

### Post by geoff123 on 2008-05-23
Hello - Does anyone have any more suggestions?  I also have a SyncMaster 245BW which only showing up as 1650x1050 both in gnome-display and in the nvidia-settings dialog.  I've tried tweaking the xorg.conf file, tried dpkg-reconfigure.., tried nvidia-config, all with no luck. I have the same issue whether it's connected via DVI or Analog (with DVI converter on the computer end).  My video card is a Nvidia 6600GT.

Specifically if anyone has a hand edited xorg.conf file that works with this file that would be great.
Thanks, Geoff:confused:

---

### Post by randallecook on 2008-05-24
Geoff,

Which driver are you using? The open source driver, the nVidia driver that Ubuntu provides, or the nVidia driver that nVidia provides?

Also, take a look at your xorg log file. I forget its name exactly (and I'n not on Linux right now so I can't check), but it is in /var/log and its name is obvious. It might give a clue about why the high resolutions are failing.

Randall

---

### Post by geoff123 on 2008-05-25
Okay I'm fully up and running now at 1920x1200 and am very happy with this monitor except for the setup pain/learning.  After spending way too many hours on this issue it's working on my nvidia 6600GT card as well as the internal intel i915 graphics chip. Some notes here for anyone also trying this.  

Also, as others in this thread, it only works on the analog (CRT-0) inputs.  I'm not sure why (maybe it has something to due with dual input DVI vs...?). 

The intel and nvidia methods are slightly different, so I'll concentrate on nvidia.  A great resource for the "intel" driver and good background for "nvidia":
[http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12)

Nvidia documentation:
[http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/README/chapter-19.html](http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/README/chapter-19.html)
[http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/README/appendix-b.html](http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/README/appendix-b.html)

Confirm you are using the "nvidia" proprietary driver.
You can do this by less /var/log/Xorg.0.log and searching for "nvidia".  If you see a bunch of them you are probably good.   If not already running nvidia, you need to install the proprietary drivers so check out System > Administration > Hardware Drivers.  For the uninitiated there is a difference between "nv" and "nvidia". Reboot.

Then calculate the modelines:
gtf 1920 1200 59.95

 # 1920x1200 @ 59.95 Hz (GTF) hsync: 74.46 kHz; pclk: 192.99 MHz
  Modeline "1920x1200_59.95"  192.99  1920 2048 2256 2592  1200 1201 1204 1242  -HSync +Vsync

Edit your xorg.conf file like below. This shows what I needed to add to make it work:

#============= START OF xorg.conf FILE ==========

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"False"
    #MANUALLY ADDED
    Option "UseEDID" "False"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
    #SEE NOTES ON MANUALLY EDITING THESE SECTIONS
    HorizSync     30-81
    VertRefresh    56-75
    # generated using gtf
	Modeline "1920x1200_60.00"  193.16  1920 2048 2256 2592  1200 1201 1204 1242  -HSync +Vsync
       Modeline "1920x1200_59.95"  192.99  1920 2048 2256 2592  1200 1201 1204 1242  -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
    # FOLLOWING SECTION MANUALLY EDITED TO WORK WITH SAMSUNG
	SubSection "Display"
	    Depth 24 
	    Modes "1920x1200_59.95" "1920x1200_60.00" "1680x1050" "1600x1024" "1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
    Screen "Default Screen"
EndSection

Section "Module"
	Load		"glx"
EndSection

#============= END OF xorg.conf FILE ==========

Type either of these to see what is being used:
xrandr -q
xvidtune -show

Once it's all working - make a backup of the xorg.conf

Note that the System > Preferences > Screen Resolution does not seem to work properly. I avoided it.  

Hope this helps someone, Geoff

---

### Post by pipenew on 2008-06-29
Any new methods to make the DVI port work with 1920x1200 resolution? 

I've tried changing the xrog.conf file but when I reboot it gets re-modified and I have to rerun nvidia-xconfig to get the previous working driver setup installed. Also what's the main difference between DVI and analog? I can see the fonts are more clear but again the highest resolution is not working so, don't know if it's going to be worth it to make it work with DVI.

Thanks - my first post :-)

---

