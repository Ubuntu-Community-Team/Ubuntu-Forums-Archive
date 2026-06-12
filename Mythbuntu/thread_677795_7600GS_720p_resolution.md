---
title: "7600GS 720p resolution"
date: 2008-01-25
forum: Mythbuntu
---

### Post by uncle hammy on 2008-01-25
Hi all,

This is my first go at this, so go easy on me :).  I have installed MythButnu AMD64 on myold AMD 64 3200+, 1.5 gig ram box, insatlled my HDHomeRun, and MythuBuntu is working nicely with it, installed my EVGA 7600GS in the box, and installed the NVdia_new drivers at setup and selected 720p component for the TV out settings.

Everything is working fine in most regards....I can watch, record, pause, my guide works,  blah blah blah tv.  All this was while still connected to my 17 lcd pc monitor for setup.  Then a few quirks happened....

On one reboot, after first watching tv on my monitor, my resolution mysteriously flopped to 640 x 480, and the Nvidia proprietary drivers were turned off.  I exited to the desktop, turned on the drivers again, and set my resolution through "displays and graphics" to 1280 x 1024 and rebooted.  When it came back up, it was at 1600 x 1200 with the drivers on, and I couldn't change it.

Undaunted, I hooked it all up to my lcd tv to see what happens....

If I hook up via component, the color is horrid (extremely bright, and very washed out), but fine via s-video.  For the most part it's awesome.  However, I can't seem to get any better resolution than 1024 x 768, and I want the 1280 x 720 that my tv can handle.  I have played around with the NVidia configuration, but 1024 x 768 is the highest resolution available to me.

What I have now, is odd to me.  If I look at settings in the Display and Graphics window, my card drivers are shown as the NV only...not the proprietary ones.  However, in the restricted drivers manager, the proprietary drivers show as enabled.  In Display and Graphics, the monitor shows as my pc monitor at 1280 x 1024, but in the NVidia Configuration it shows "Screen 0" as my tv at 1024 x 768.

Perhaps I should also add, the box is an old EMachines.  It has integrated video, that I am not using.  I think I disabled it in the BIOS by disabling UMA for integrated video...but I'm not sure if that actually disabled it.  Then again, if it's like most motherboards, inserting the new card into the PCI Express slot would have disabled the onboard video.

Can anyone give me any advice on getting 720p tv out output, and perhaps how I can get my component output to clean up?

Thanks,
Hammy

---

### Post by uncle hammy on 2008-01-25
Another quick thought.  My 7600GS card has a DVI output, and my TV has an HDMI input.  Would my best bet be to buy a DVI - HDMI cable, and hook up my video that way?

---

### Post by BillDozer on 2008-01-25
I hooked my MythTV box like that DVI->HDMI and am very happy about it. I have other specs though so YMMV. ;)

---

### Post by uncle hammy on 2008-01-25
Did you just hook up a separate sound source, because HDMI normally carries sound?  Do you think my resolution could be currently limited because of the connection s-video connection I am using, or should I still be able to get 720p through s-video with some configuration tweaking?

---

### Post by stoodleysnow on 2008-01-25
You might have inadvertantly messed up xorg.conf
Try going to a terminal program and type:
```
cd /etc/X11

```
If you want you can open xorg.conf
```
sudo nano xorg.conf
```
at the top of xorg.conf it gives you a reconfiguring command - I think it is
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
But I can't remember for sure.:?:
:popcorn:
Good luck.

---

### Post by BillDozer on 2008-01-25
> **uncle hammy said:**
> Did you just hook up a separate sound source, because HDMI normally carries sound?  Do you think my resolution could be currently limited because of the connection s-video connection I am using, or should I still be able to get 720p through s-video with some configuration tweaking?
I added a sound cable from my PC to the TV too, there is a seperate entry on my TV for sound input connected to the HDMI port and the TV uses that when it is connected. 

I do not think you can get 720p via s-video. As I recall s-video is interlaced as well, although I am not an expert....

---

### Post by uncle hammy on 2008-01-25
> **stoodleysnow said:**
> You might have inadvertantly messed up xorg.conf
Try going to a terminal program and type:
```
cd /etc/X11

```
If you want you can open xorg.conf
```
sudo nano xorg.conf
```
at the top of xorg.conf it gives you a reconfiguring command - I think it is
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
But I can't remember for sure.:?:
:popcorn:
Good luck.
SO, you're saying to launch the reconfigure command, and go through it step by step?  At the end, I should hopefully have everything back to normal?  Will it allow me to select the nvidia proprietary drivers again, set tv out settings again, etc?

---

### Post by tgalati4 on 2008-01-25
S-Video is also called 2-wire video.  It it interlaced, 480 lines of resolution.  Instead of one-wire video (composite video) where the entire video signal is pushed down one wire (with a shield), S-Video splits the same signal into two wires (color (C) and brightness (Y)), but it's still standard definition (480i).  You need component (RGB) three-wire video to push higher modes like 480i, 720p, 1080i, 1080p.  There are converters that take DVI and put out component and also DVI to HDMI which should also work.

Please post your experiences when you get a working combination of cabling and resolution selection.

---

### Post by uncle hammy on 2008-01-25
My GS7600 card came with a s-video to component adapter that plugs in to the tv s video out.  It was my first connection, but (as mentioned) the color has horrible....very bright, and washed out. I would love to figure out why that is.

Either way, I suspect I will get better results using DVI / HDMI cabling.

---

### Post by newlinux on 2008-01-25
You will definitely get better results using DVI-HDMI. It is capable of much higher resolutions than S-video, which computer displays need (this is part of the reason you don't find computer monitors with S-video inputs). Computers have used higher resolutions than TVs for years until HDTV came into prominence. What ever resolution your are using on your computer is getting downsampled to 480i through s-video.

Also, there is currently little support for audio through HDMI in linux. Besides if you are using  DVI->HDMI there is no possibility for audio to go through because DVI doesn't support audio. 

If you want 720p you'll need to get the component (not composite, just to be clear because I see a lot of people interchange the two) working right or the DVI->HDMI working right. If your TV has a VGA in input your computer a VGA output you can get it that way too. Be sure to check what resolutions and refresh rates your TV supports through VGA if you go with this method.

What is your TV's native resolution.

---

### Post by superm1 on 2008-01-25
The very first thing you should be checking is *why  *the tv wasn't showing its native resolution via your cabling.  In /var/log/Xorg.0.log, you will see information related to the EDID (if it couldn't be read, if it was, etc).  Also you will see what resolutions were supported.  If you have trouble interpreting it, post it here and one of the forum folks can help out.

---

### Post by uncle hammy on 2008-01-25
I'm not sure what constitutes "native", but here's the specs from my tv's website...

Video Formats : 480i - 60Hz, 480p - 60Hz, 720p - 60Hz, 1080i - 60Hz

---

### Post by uncle hammy on 2008-01-25
> **superm1 said:**
> The very first thing you should be checking is *why  *the tv wasn't showing its native resolution via your cabling.  In /var/log/Xorg.0.log, you will see information related to the EDID (if it couldn't be read, if it was, etc).  Also you will see what resolutions were supported.  If you have trouble interpreting it, post it here and one of the forum folks can help out.
The TV is working fine ( I think).  I can't actually increase the resolution being output in the NVidia configuration in the Control Center.  The highest resolution it will let me set is 1024 x 768.  The higher resolutions aren't even an option.

---

### Post by superm1 on 2008-01-25
> **uncle hammy said:**
> The TV is working fine ( I think).  I can't actually increase the resolution being output in the NVidia configuration in the Control Center.  The highest resolution it will let me set is 1024 x 768.  The higher resolutions aren't even an option.
Right, I understand this : the important part is why this is happening (Which is detailed in that log)

---

### Post by uncle hammy on 2008-01-25
Gotcha.  I'll let you know.  To be honest, I may just reinstall from scratch.  I spent a lot of time yesterday hacking around trying to get things working....who knows what I did during all that.

Now that I know how to configure everything without messing around, it may be easier to just start over than try to fix it all.

I bought a DVI - HDMI cable, so I may even install with my tv as the monitor and configure it for that from the get go....and eliminate anything that may have happened with detections by moving from my pc monitor to my tv.

Is this a bad plan?

---

### Post by superm1 on 2008-01-25
> **uncle hammy said:**
> Gotcha.  I'll let you know.  To be honest, I may just reinstall from scratch.  I spent a lot of time yesterday hacking around trying to get things working....who knows what I did during all that.

Now that I know how to configure everything without messing around, it may be easier to just start over than try to fix it all.

I bought a DVI - HDMI cable, so I may even install with my tv as the monitor and configure it for that from the get go....and eliminate anything that may have happened with detections by moving from my pc monitor to my tv.

Is this a bad plan?
Depends on the implementation of your TV's hdmi port.  If it is intended to act like a monitor (with no overscan etc) then that will be fine.

Otherwise, you'll see a really overscanned picture that can't be fixed easily.  If it is very overscanned, you will have more luck with VGA typically.

Personally, on my TV I use VGA for this exact reason.  The TV provides a valid EDID over VGA with no overscan.

---

### Post by uncle hammy on 2008-01-25
OK, I got home, and I plugged in the DVI-HDMI cable, and the picture is gorgeous!  NVidia Control Center even recognizes my make and model of TV, set it automatically to 1280 x 720 resolution @ 60 hz and everything.

The only issue I have (and it's probably what you were referring to), is picture is too big for the screen by about 10 - 20  pixels all the way around, so that part gets cut off (it's especially noticeable in configuration menus, or the desktop).

Anything I can do about that?

---

### Post by uncle hammy on 2008-01-25
OK, I played around with GuiX, GuiY sizes, by decreasing them by equal percentages, and the X, Y offset, and got the screen to fit, and centered.

I checked "use Gui size for TV", and everything seems to be good.  Does this actually resize the image, or simply crop off the extra?

---

### Post by superm1 on 2008-01-25
> **uncle hammy said:**
> OK, I played around with GuiX, GuiY sizes, by decreasing them by equal percentages, and the X, Y offset, and got the screen to fit, and centered.

I checked "use Gui size for TV", and everything seems to be good.  Does this actually resize the image, or simply crop off the extra?
This will work out fine for myth, it resizes/rescales the image.  As long as your CPU can handle doing that on the fly you are fine.  You're trouble will be when you launch external apps (say to browse the web or to play a dvd).  These can't be sized the same way.

---

### Post by uncle hammy on 2008-01-25
> **superm1 said:**
> This will work out fine for myth, it resizes/rescales the image.  As long as your CPU can handle doing that on the fly you are fine.  You're trouble will be when you launch external apps (say to browse the web or to play a dvd).  These can't be sized the same way.
So far, everything seems fine.  I do occasionally get some "lining", where  I can see the horizontal lines in the picture, would be nice to get rid of it, but I can certainly live with it.

Is there another / better way to rid myself of the overscan?  I do not have a VGA input on the TV.  I have seen "modeline" referred to a couple times, but I have a feeling that would be well out of my league.

---

### Post by superm1 on 2008-01-25
> **uncle hammy said:**
> So far, everything seems fine.  I do occasionally get some "lining", where  I can see the horizontal lines in the picture, would be nice to get rid of it, but I can certainly live with it.

Is there another / better way to rid myself of the overscan?  I do not have a VGA input on the TV.  I have seen "modeline" referred to a couple times, but I have a feeling that would be well out of my league.
Mess with deinterlacing in myth a little, and possibly the vsync settings in nvidia-settings for the the horiz lines.

W/o vga port, this is probably your best bet for now.  Modelines can be tricky to create unless you find one already made for your TV.

---

### Post by uncle hammy on 2008-01-25
Where do I go to play with the deinterlacing?  

By the way, I haven't said thanks for all your help...so Thanks!  You've been great.

---

### Post by tgalati4 on 2008-01-25
The S-Video connection that you referred to earlier is actually a dual-port--S-Video and Component out.  It's possible that you didn't set the correct RGB mode on the TV.  There are 2 basic modes:  RGB-with sync on Green, and YPrPb with sync on Y.  If you have the wrong mode set, then your colors will be strange.  Check your TV settings and your card settings and make sure you have the same mode.

What kind of horizontal lines are they?  Are they slowly moving down?  Are they brightness lines?  Perhaps the component cable will provide a clearer picture.  Also try turning off the noise and some other filters on the TV.  They are designed to clean up a dirty cable signal, but degrade a computer output.

---

### Post by uncle hammy on 2008-01-26
Now, the aren't moving.  They aren't all the time either.  They are the actual horizontal lines of pixels.  They usually appear in the form of little black streak around objects when the objects move.

---

### Post by uncle hammy on 2008-01-26
OK, time for a reset....

I have reinstalled Mythbuntu (mostly because I am still in the testing phase, so it's no big deal).  This time, I was very careful when setting the TV out options in the NVidia drivers setting during installation.  

I now have component out working at full 720p!  I also have DVI - HDMI working at full 720p!  Both worked right out of the box once I rebooted after installation.  I have a feeling I may have selected composite instead of component the first time round.  I know the difference, but it was late :).

However, even using component instead of HDMI, I still get over scanning.  I also get the "lining" (think Enemy Of The State, what the screen looks like when they show the satellite images, only not so severe, and intermittently, depending on the show and channel).  I wish I could take a screen shot of it, to show.

Is fixing the over-scanning easier from Component than HDMI?

---

### Post by uncle hammy on 2008-01-26
Sometime this stuff gets so confusing....

My tv spcs says that 1080i is supported.  So I tried doing an install and setting the TV OUT options Component 1080i, and it worked just fine.  Now I suspect that the TV's NATIVE resolution is 720p, because the HDMI connection automatically chooses that.

However, at 1080i component out, the TV indicates it's a 1080i signal, and the "lining" seems to be gone.  Though there appears to be a slight of flicker on objects move quickly.  There is also some flicker in Myth Setup menus at the bottom....not in the main gui though.

Now the confusing part, if I go to the Myth Control Center, and look at the NVidia Settings Panel, all resolution options are available to me (1080i on down).  So, out of curiosity, I set it to 720p and applied.  Well, the screen just shrunk, and when I rebooted, all resolution options were gone, and I was stuck with 1024 x 768 and the washed out color, and no apparent way to get it all back??

---

### Post by uncle hammy on 2008-01-26
OK, in the spirit of someone down the road getting something out of this post...

I have a backup of a working 1080i xorg.conf file and a 720p xorg.conf file on my machine, both from clean installs selecting 720 and 1080i for tv out respectively.  I am able to overwrite xorg.conf with either, and they work. 

I found the deinterlacing setting in the Playback settings, and it has solved almost all of my "lining" problem.  

The only question I now have, is there are 3 algorithms for deinterlacing (Bob, Liner Blend, Kernel).  WHat are the benefits / trade offs of each, and is there a clear cut winner to use?  I have had no ill effects of any of them.  I am thinking Bob, because it says if uses Xvc, which if I understand correctly, dumps some of the load to the Graphics Card.

---

### Post by newlinux on 2008-01-26
[http://www.linuxjournal.com/article/8524](http://www.linuxjournal.com/article/8524)

May help explain the differences.

I use bob on some machines and linear blend on others. It isn't clear cut because there are a lot of variables (video card, XvMC, display, CPU, types of programs you watch, etc.).

XvMC requires the use of  bob, but Bob doesn't have to use XvMC. Bob generally requires the most CPU.

I notice the most difference when I watch fast moving things (like football). For me Bob is the only one that does a really good job on the movement.

---

### Post by uncle hammy on 2008-01-27
Thanks, that was very helpful!  It did bring up another question I've been pondering.....the mythical XvMC.  I've seen it mentioned, I picked my 7600GS card over an 8500GT because I read the GS was XvMC capable, and that was a good thing.

What exactly is it, how do you use it, or know if you're using it?

---

### Post by newlinux on 2008-01-27
[http://www.mythtv.org/wiki/index.php/XvMC](http://www.mythtv.org/wiki/index.php/XvMC)

Will tell you all you need to know. You basically set up your Xorg.conf to use it (See the configuration section of the link I sent you) then you set myth to use it. You'll know you are using it when your OSD is in black and white. You should see CPU usage decrease as well. I have found it a bit buggy, as have others... so if you can display HD fine without, I'd recommend that.

---

### Post by uncle hammy on 2008-01-27
Thanks again!  I enabled it just to see, and it works well so far...though bringing color to the OSD would be nice....but hey, if you could have everything.....:)

I may bump my output to 1080i again to see how it effects that.  I tried it last night without XvMC, and I was watching a sporting event, and there was some real jerkiness to it, so I bumped down to 720p again.  This machine is a AMD64 3200+ with 1.5gigs of memory and the 7600GS card, but it's also front-end and back-end, so I think I was pushing it.  This may help.

Is there a way to view view your CPU usage while doing playback to compare results with and without?

---

### Post by newlinux on 2008-01-27
yes you can use the "top" program from a terminal to see CPU usage.

ssh into your machine open up a terminal on your machine while myth is running and run the program "top." It gives a realtime display of processes, CPU usage, and other information

---

### Post by stdPikachu on 2008-01-27
I've run into dozens of TV's that incorrectly report their spec over DVI/HDMI. NO idea why that is.

Thankfully, nVidia are aware of this and provide a nice "DFPNativeResolutionCheck" option. Just define the native res (or as close as you can get) in the monitor section of your Xorg.conf and then add the aforementioned option; the driver should then no longer fail to load when handed a FUBAR EDID.

---

