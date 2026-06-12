---
title: "How to solve problem with nvidia and lcd tv linked by dvi?"
date: 2006-11-22
forum: Multimedia &amp; Video
---

### Post by luckyaua on 2006-11-22
Hi guy, i'm new in this forum and new in ubuntu, i'm italian and then i'm sorry for my poor english.
So, i've this problem i have a htpc equipped with nvidia Gf6150 linked with 16:9 lcd tv toshiba 32wl56p by cable dvi--->hdmi.
In ubuntu i've the same problem that i found in xp, desktop in resolution like 1280x720 is too big respect visible image.
In xp i've solved by underscan/overscan then the resolution is still 1280x720 but the desktop area is reduced to 1216x684 and centered, so all ok.
In ubuntu i don't find this option in nvidia control panel (nvidia-settings) and i can't set the resolution out of the classic/edid resolution then res like 1216x684 is refused by the system in system xlog.

How to solve?
Please help me...:!:!:!:

---

### Post by luckyaua on 2006-11-22
Nothing for me?...
A little help?

---

### Post by luckyaua on 2006-11-22
This my settings in xp.

---

### Post by gerick on 2006-11-28
You should be able to come up with a custom modeline from those WinXP settings.  Can you trans into English the screen shot for me?  Specifically you need the Horizontal and Vertical Front Porch (portico?), Horiz and Vert Back Porch, and Horiz and Vert Sync., plus the Polarity and DotClock.

Looks like your HSync = 40, VSync = 5, Polarity H- V-.  DotClock might be 74.0018, 
Front Porch H = 110, V=5 maybe?

You might try:
Modeline "1216x684" 74.0018 1216 1326 1346 1650 684 689 694 750 -hsync -vsync

---

### Post by juan_kerr on 2006-12-08
I am in the exact same situation. I still haven't worked out what to do, probably partly because I'm a begginer. 

Unfortuantely I have deleted my windows partition (intentionally) so I cannot go back to check my previous XP settings regarding my adjusted settings. 

You make reference to editing a file and give an example string. What is the file and where is it? Do I just edit it in Kate (I'm using Kubuntu)? 

I'll give it a go if I can find out where to make the changes. 

Thanks

---

### Post by gerick on 2006-12-08
Your screen settings are in /etc/X11/xorg.conf

What are you trying to use as your monitor?  You might be able to google the proper timings for it.

---

### Post by oneiromancer on 2006-12-08
Hey, I'm in essentially same boat but have a different central issue...  I pulled modeline instructions from forum and put in xorg.conf to try and get more resolutions enabled, only to have GDE fail to load and tell me "Modeline" is not a valid command (just occurred to me...  is it capitalized or uncap'd?  Could that be issue?).  I have ASUS M2NPV-VM mobo with Nvidia GeForce 6150 chipset, and presently I beleive the DVI out does not work at all in Ubuntu, does in XP Pro..  Also appreciate any help getting component video out working in XP or Ubuntu, I'm displaying on a 1024 x 768 plasma at the moment (though that's likely to change pending resolution of dispute with retailer) and its tricky trying to compensate for non square pixels in XP Pro, but harder in ubuntu when I only have like 3 or 4 resolutions to choose from...  Someone referenced a "Modeline" utility to help generate valid modelines for specific monitors, can anyone direct me where to find that?  A quick search on forums and my previous looks seem to have only references to it, not links etc, though [this post]("http://ubuntuforums.org/showthread.php?t=221427&highlight=Modeline+utility") has some interesting stuff about xserver-xorg-driver-i810 from Synaptic (no idea if relevant) and reference to having properlyu "setup 915resolution from Synaptic, and a link to linuxmint.com that's broken..... ([http://linuxmint.com/content/view/212/52/](http://linuxmint.com/content/view/212/52/) ) All help appreciated, feel free to email me as I'm ADD and may forget to come back here for a week otherwise :-)

---

### Post by oneiromancer on 2006-12-09
OK, update on two minor points....
One, I found the modelin utility in question ([http://www.bohne-lang.de/spec/linux/modeline/](http://www.bohne-lang.de/spec/linux/modeline/))
Also confirmed that the Modeline commands seems to be capitalized, which is the way I entered it.  So this is the key question:  Why the hell is Modeline an unrecognized command by GDE/X/Nvidia, whatever processes the modeline argument...  Is there an alternative I can try, or could that error reflect the *wrong* modeline rather than modeline *really* being a bad command reference?

Edit: OK, I think what I needed was "ModeLine" rather than "Modeline" but haven't tested yet...  most promising things so far are this ([http://gentoo-wiki.com/HOWTO_Xorg_HDTV](http://gentoo-wiki.com/HOWTO_Xorg_HDTV)) and this ([http://ubuntuforums.org/showthread.php?t=98456](http://ubuntuforums.org/showthread.php?t=98456))  and finally noticing this line in xorg.conf which, having run and liking what I saw as a start, I'm about to reboot GDE and test: 
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg
This reconfigure allowed me to select resolutions to try etc...  I also found references to checking output of sudo ddcprobe and discovered I didnt have that, so installed from synaptic, and that may have helped get better H and V refreshs for my tv or something... I dunno for sure if it helped but I ran dpkg-reconfigure -phigh (etc) twice, once before and once after installing ddcprobe, and  HorizSync  value in xconfig (which I think wasnt present before reconfigure) went from I think 28-90 or 92 before to 28-84 after, which is presumably more accurate due to ddcprobe or something...  Rebooting/logging in now, wish me luck :-)

Post-Mortem: OK, well, after a typo or two, new xorg.conf file runs...  but resolutions under preferences still only list one mode and not the name I specified, same one it had when I rebooted after doing reconfigure, 1280 x 720, though that wasnt a listed resolution in the new-auto xorg.conf file, nor is it what I chose...  and now I have severe overscan problems, can't see menu bar or bottom bit of screen, and only lead I have on fixing overscan is this page ([http://www.rockhopper.dk/linux/hardware/graphics_cards.html](http://www.rockhopper.dk/linux/hardware/graphics_cards.html)) referencing fbset, only from what I can tell (not much) ubuntu's not or can't use frame buffers over DVI or something, in any case I installed fbset and it tells me fb0 doesnt exist, and no other fb devices listed in /dev.....  Help?    Here's my current xorg.conf file, though I have many backed up versions, most work as in function, but so far not much in way of progress other than having a widescreen mode now...

---

### Post by gerick on 2006-12-11
Try putting ```
Option "DynamicTwinView" "FALSE"
``` in ```
Section "Device"
       Identifier  "Card0"
       Driver      "nvidia"
       VendorName  "nVidia Corporation"
       BoardName   "[Onboard Video - GeForce 6150]"
       BusID        "PCI:0:5:0"
       Option "ModeValidation" "NoMaxSizeCheck, NoHorizSyncCheck,, NoVertRefreshCheck"
       Option       "RenderAccel" "true"
       Option       "AllowGLXWithComposite" "true"
       Option       "ConnectedMonitor" "DFP"
       Option       "NoLogo" "1"
EndSection
```

Remove ```
Load	"dri"
``` from the "Modules" Section.

What is your monitor?  If it is a HP-S4253, then you would probably be better off using the VGA input on the hdtv.

---

### Post by oneiromancer on 2006-12-11
It *is* an HP-S4253, though like I said that's somewhat likely to change pending resolution of retailer conflict(*).  I'll try your suggestions first chance I get, and to switch between DVI and VGA, I just switch "ConnectedMonitor" "DFP" to "ConnectedMonitor" "VGA" or something right?  Any ideas on whether component video might be better still, or not worth it?  I don't think I've fully gone through the HDTV setup guide which seems to focus on S-Video but looked like it would work for component too, but haven't gotten that working properly in windows either (finally got it outputting, but colors were all messed up despite being plugged in right and trying some switches, maybe its not standard Y Pr Pb, but one of the other component outs?  I forget, and it seems unlikely, but we'll see).

(*)Off topic for those interested: They advertised the model as having a "Digital Cable Ready Tuner", and while the HP-S4273 has this feature, the 4253 doesn't, and after slowly acknowledging their fault, they still refused to let me return without a restocking fee or exchange for a model that had feature at no cost beyond price difference... I also offered for them to pay for an external QAM box, but their best offer was $60 back, which was too little, and inappropriate considering they'd engaged in false advertising...  so credit card company and/or attorney general will sort it out now...

---

### Post by gerick on 2006-12-12
> **oneiromancer said:**
> I just switch "ConnectedMonitor" "DFP" to "ConnectedMonitor" "VGA" or something right?  Any ideas on whether component video might be better still, or not worth it?

```
Option "ConnectedMonitor" "CRT"
```

I don't know about picture quality, but it would be much easier.
Your sammy can do 1024x768 thru the vga port, and that is still a HD picture.  The advantage is that monitor is plug-n-play and send the correct timing to the computer so no modeline is needed.

You would need to comment out some code in xorg.conf and let the monitor send proper timings to pc.

```
Section "Monitor"
       Identifier      "Samsung PDP"
       VendorName      "Samsung"
       ModelName       "HDS-4253"
  #    Option          "IgnoreEDID" // DO NOT IGNORE, want to use
  #	HorizSync	28.6
  #	VertRefresh	43
  #     Modeline "1152x648" 37.30  1152 1176 1224 1304   648  648  649  665          
  #     DisplaySize             1152 648
EndSection
Section "Screen"
   Identifier "Screen0"
   Device     "Card0"
   Monitor    "Samsung PDP"
   DefaultDepth 24
#   SubSection "Display"
#       Viewport   0 0
#       Depth     24
#       Modes "1152x648"
#   EndSubSection
EndSection

```

There are menus on the TV to position the screen and center it.  I think that going this route is the easiest to deal with the overscan (the picture going beyond the edge of the screen).

Also, I am not sure about the "ModeValidation" line. Since we are going plug-n-play, this line might want to come out.

---

### Post by oneiromancer on 2006-12-13
OK, first of all, thank you for suggestion to go back to VGA, I'd started there but switched to DVI when I was trying to get component video to work on XP or in Ubuntu, as 6150 can't do Compon. and VGA at same time...   I dunno what settings I changed in windows since I last used CRT, but suddenly I can do a near perfect looking 1280 x 720 or x 768 (sticking to 720 for now as its correct aspect ratio, though now I have to assume all the pixels are visible and its just some overscan artifact in signal that messed it up over DVI... ) I guess this is what you meant about proper timings being automatic over VGA, but since DVI carries analog rider I guess I figured there weren't many advantages to VGA...

But back in Ubuntu, I can't get the 1280 x 720 option that was present on DVI, and that works fine in Windows, to show up over VGA...  It keeps going to the native-but-stretched 1024 x 768, though there is an 832 x 624 mode, but when I try and switch Samsung says not supported mode...

I tried the suggested modifications on last posted xorg.conf file, I tried doing sudo dpkg-reconfigure -phigh xserver-xorg, and I ran the envy script ( [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) ), and I tried going back to the 1280 x 720 working script I had on dvi, which didn't actually specify DFP anywhere in it, but also didnt specify the 1280 resolution, but as I recall said that it would use the highest one that worked...  I'll attach, appreciate any tips, maybe there's a way to pull modeline off windows?  Or do modelines not work for VGA, is that why first time I tried one it said invalid command or whatever?  Appreciate the help, thanks...
           -Brian

---

### Post by gerick on 2006-12-13
Sorry if I am not helping much. I am a newbie also, BUT I have gotten xorg to work with my Sony HDTV. 

Looking at your manual, page 91, I see that your monitor supports 640x350, 720x400, 640x480, 800x600, and 1024x768. That might be why 1280x720 doesn't work.  I also see in your manual that your monitor only supports XGA over VGA.  That is a 4:3 aspect ratio.  You need the HP-S5053 to support WXGA (16:9).

Modelines work for VGA as well as DVI.  It is just that using VGA on your monitor did not need them because your monitor is plug-n-play.
> VESA Plug and Play solution eliminates complicated and time consuming setup. It allows you to install your monitor in a Plug and Play compatible system, without the usual setup hassles and confusion. Your PC system can easily identify and configure itself for use with your TV. This TV automatically tells the PC system its Extended Display Identification data (EDID) using Display Data Channel (DDC) protocols.

The modeline sets the timings manually and can be used for VGA or DVI.  But using DVI, you have the added issue of overscan.  The normal TV signal displayed on your TV displays the picture several pixels beyond the edge of the screen.  This prevents you from seeing any artifacts on the edge of the screen.  But when you try to send the PC signal to the screen, the same issue is there.  The taskbar at the bottom of the screen is cutoff and the mouse can move beyond the edges of the screen.  

The nVidia WinXP drivers handle this by showing a window within a window.  If you have dual boot, you can get the timings needed for linux.  Under WinXP, you can use DVI and tell nVidia that you have 1280x720 hdtv.  Then nVidia has a over/under scan screen that shows green arrows at each corner that you can adjust so each arrow is at the corner of the screen.  What this does is show something like a 1176x664 screen centered in a 1280x720 window.  The pixels around the 1176x664 screen are the ones overscaned beyond the edge of the monitor display.

If you get this looking good in WinXP, then get the timings from the windows (I can't remember what screen, but somewhere in advanced settings) and post the values here.

---

### Post by oneiromancer on 2006-12-13
Nod, thanks again Gerick, not sure I knew my manual was online, my own copy is only a photocopy for some reason...  What's weird is, mabye I wasn't clear before, the 1280x720 res *is* working and looking great in windows, and as far as I can tell its not 1176x664 that's being sent, when I adjusted over DVI using nVidia drivers over/underscan config starting from 1280x720, I wound up with something along the lines of 1176x664 (forget exact numbers, and I tried a bunch of different ones... it even took 1080p input much to my surprise, when I let nVidia wizard try out all diff. resolutions).  That doesnt seem to be the case here, as those odd numebrs always showed up as current res. under Display Properties -> Settings -> Screen Resolution slider bar...  I will try and pull timings from windows next chance I get and post here or see if I can translate myself using modeline tool or something, one big reason for using VGA over DVI is the HDMI input doesnt support PC/monitor functionality as well as VGA on the 4253, so for instance when I first tried the 1280x720 res on VGA yesterday, it was perfect vertically but way off to the left horiz.  Nvidia controls only let me move it 30-50% of the way to correct, but then I did auto adjust in Samsung menu and it was perfect... (I also played with 1280 x 768 and 1360 x 768, both of which looked pretty good, but as I said, 1280x768 is wrong aspect ratio for HD video, and 1360x768 is correct, but didn't look quite as solid, probably owing to 1280 being exactly 25% over 1024, so nice even horiz. scaling rate, wheras 1360 is a messier 32.8125%...  I think 1280x720 is also the natural resolution of 720p video, so all the more reason to stick with it...  good to know if I get stuck with this monitor I can get a decent looking PC display on it after all :-)

---

### Post by gerick on 2006-12-13
720p is what I settled on for my Sony Wega.

I tried to use it's native resolution of 1368x768, but never could get the proper timings.  That is why I ended up using the WinXP drivers to handle the monitor as a hdtv.  I also tried 1080i, but it did not seem as sharp (maybe because it is kind of like 540p doubled).

I see that your mobo supports component out.  That is something I have not tried.  I wonder if there is any advantage of using that over dvi?

---

### Post by oneiromancer on 2006-12-13
Nod, I mentioned the component video out, and it appealed to me to try it, but I had issues getting set up, and have less motivation to try it now that I have good VGA timings in Windows, and hopefully shortly in Ubuntu...  The [modeline utility ]("http://www.bohne-lang.de/spec/linux/modeline/") doesn't have a 1280x720 resolution in its menus by default, but I hacked it into the command line argument with a vertical refresh of 59.999 pulled from my windows timings and got [this for a modeline]("http://www.bohne-lang.de/spec/linux/modeline/modline.php?MODE=1&RE_VALUE=1280+720&FREQ=59.999") etc:
[INDENT]  Horizontal Resolution:   1280 
  Vertical Resolution:      720 
  Vertical Refresh Rate:   60.00 Hz 
  Horizontal Refresh Rate: 44.81 KHz 
  Dot Clock Frequence:     69.91 MHz 

 # V-freq: 60.00 Hz  // h-freq: 44.81 KHz
 Modeline "1280x720" 69.91  1280 1320 1408 1560   720  720  722  746 [/INDENT]

This closely matches my windows timings in Horiz. scan rate (refresh rate), but is somewhat further off on pixel clock (dot clock).  Here's all the timing info I pulled from windows config so you can see for yourself:
Horiz - Front Porch: 56       Vert - Front P: 1
Horiz - Back Porch: 192       Vert - Back P:22
Horiz - Frnt End Act.: 1280 Vert - F.E.A:720
Horiz - Scan Wid.: 136         Vert- Scan W.:3
             Scan Rate: 44.76     Refresh 59.999
Sync Polarity ( - )                Sync Polarity ( + )
                            Pixel Clock 74.48

Think the above modeline will work, or is there a way to get a more accurate/closer one to this?

Oh, also, just in case this is really trivial and you or someone reading knows, I have an unpartitioned like 80 gigs on my linux drive, but already have 4 primary partitions there, is there an easy way to move the installation's swap partition over to the other HDD so I can format the last 80 gigs and make use of it?  Thanks, if not trivial or no one's sure I'll take it to appropriate forum, just thought I'd throw it out there for now...

---

### Post by gerick on 2006-12-13
> **oneiromancer said:**
> 
Horiz - Front Porch: 56       Vert - Front P: 1
Horiz - Back Porch: 192       Vert - Back P:22
Horiz - Frnt End Act.: 1280 Vert - F.E.A:720
Horiz - Scan Wid.: 136         Vert- Scan W.:3
             Scan Rate: 44.76     Refresh 59.999
Sync Polarity ( - )                Sync Polarity ( + )
                            Pixel Clock 74.48

I believe those figures would give you a modeline of 
Modeline "1280x720" 74.48 1280 1328 1464 1656 720 721 724 746 
Try both and see which is better.
> **oneiromancer said:**
> Oh, also, just in case this is really trivial and you or someone reading knows, I have an unpartitioned like 80 gigs on my linux drive, but already have 4 primary partitions there, is there an easy way to move the installation's swap partition over to the other HDD so I can format the last 80 gigs and make use of it?  Thanks, if not trivial or no one's sure I'll take it to appropriate forum, just thought I'd throw it out there for now...
You can use the partition tool to create a swap partition.  Then somewhere (fstab?) there is a place that tells linux what to mount on loading.  That is about as much as I know about that.

---

### Post by oneiromancer on 2006-12-13
Thanks, will do...  and I knew how to create new swap, but I'll check out fstab to see if I can reassign the swap location (It'll leave 2 gigs unpartitioned on one drive instead of 80 on the other, easy call :-} ).  Out of curiosity, how did you create the modeline?  Is there another tool besides one I linked to, or do you know how to read them well enough to just infer it somehow? Obviously first number is pixel clock and second is H. Resol, but next 3 and last 3 are a mystery to me... just curious, thanks again Gerick!

EDIT: OK, tried your modeline, and it works perfectly...  And once I was actually typing the numbers they made sense to me, 2nd and 3rd number after H. Res. are first number  + Horiz. Scan Width, and then that number + H. Back Porch equals 3rd...   it leaves the 48 diff from 1280 to 1328 a bit of a mystery, any chance that was supposed to be 1336 for 1280 + Front Porch?  This'd also make sense since that's the number added to Vertical resolution, the veritcal front porch of 1 for 721, so I think I'lll change that for consistency...  Only adjustment I had to make was auto adjusting the screen to move it horizontally a bunch just like I had to in windows, but that might save readjustments switching between or something....  Thanks again, and hope this all helps someone else :-)

---

### Post by gerick on 2006-12-14
> **oneiromancer said:**
> OK, tried your modeline, and it works perfectly...  And once I was actually typing the numbers they made sense to me, 2nd and 3rd number after H. Res. are first number  + Horiz. Scan Width, and then that number + H. Back Porch equals 3rd...   it leaves the 48 diff from 1280 to 1328 a bit of a mystery, any chance that was supposed to be 1336 for 1280 + Front Porch?  This'd also make sense since that's the number added to Vertical resolution, the veritcal front porch of 1 for 721, so I think I'lll change that for consistency...  Only adjustment I had to make was auto adjusting the screen to move it horizontally a bunch just like I had to in windows, but that might save readjustments switching between or something....  Thanks again, and hope this all helps someone else :-)

You are correct.  Bad math late at night.  Plus I forgot your Polarity flags.

Try this one and see if it is better if you haven't already made the corrections.
```
Modeline "1280x720" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
```
BTW, another way of showing the proper timings 
```
Mode "1280x720"
	DotClock 74.48
	HTimings 1280 1336 1472 1664
	VTimings   720   721  724   746
	Flags    "-HSync" "+VSync"
EndMode
```

The two above code sections are equivalent, you would use one or the other.  

Setting the proper timings and polarity flags might help center your screen better.

---

### Post by globexispower on 2006-12-16
> **gerick said:**
> ... I have gotten xorg to work with my Sony HDTV. ...

Could you attach your xorg.conf?  I am trying to get my Sony Wega working as my monitor but I can't seem to get any res besides 800x600.

---

### Post by oneiromancer on 2006-12-16
Well, I'm the one with the Samsung (HD-S4253) not the sony, but if you have windows installed you can probably use that to find good timings/resolution, and I'll attach my final xorg in case any one else wants it...  Gerick'll probably respond soon enough assuming he's still checking this thread though...

---

### Post by gerick on 2006-12-18
> **globexispower said:**
> Could you attach your xorg.conf?  I am trying to get my Sony Wega working as my monitor but I can't seem to get any res besides 800x600.


I don't have my entire xorg.conf avail at this moment, but I do know what modelines I have used. This is for a Sony KF-50WE610.

```

Modeline "1280x720" 74.16 1280 1392 1432 1648 720 725 730 750 +hsync +vsync
Modeline "1176x664" 74.16 1176 1288 1328 1648 664 669 674 750 +hsync +vsync
```

The 1280x720 resolution has a bit of overscan. For example, the bottom half of the KDE taskbar is cut off.

I ended up using the 1176x664 resolution that corrects this by showing a 1176x664 window in the same timing as the 1280x720.  I also needed to add
```
Option "FlatPanelProperties" "scaling = centered"
```
to the Screen Section so that this resolution is not stretched back to 1280x720.

I can add my xorg.conf later when I get a copy of it.

**oneiromancer:** Did adding the -/+ polarity flags make any difference on your settings?

---

### Post by oneiromancer on 2006-12-19
> **gerick said:**
> **oneiromancer:** Did adding the -/+ polarity flags make any difference on your settings?

Oh, yeah, it centered it  so I wouldn't have to keep doing monitor auto-adjusts between WIndows & Ubuntu...  I'd had one of two modelines or mode sections in the past that had either +hsync + vsync or - hsync - vsync things at their tail, but out of context I thought they were variables subtracting the horizontal and vertical resolution from some of the other parameters or something :-}

Now I'm having MythTV problems, and my friend over there who is apparently one of the developers for mythTV may have abandoned me to go somewhere on holiday or something!  I should probably find a more applicable spot to cross-post the issue, to get faster help, but he got me into the trouble, right?  I'm considering just uninstalling and resintalling mythTV entirely, but not sure if that should really be necessary, or if it won't entail its own problems....  anyonje knowledgable who happens to be reading, that thread is here
[http://www.ubuntuforums.org/showthread.php?t=320304](http://www.ubuntuforums.org/showthread.php?t=320304)

---

### Post by gerick on 2006-12-20
> **oneiromancer said:**
> Oh, yeah, it centered it  so I wouldn't have to keep doing monitor auto-adjusts between WIndows & Ubuntu...  I'd had one of two modelines or mode sections in the past that had either +hsync + vsync or - hsync - vsync things at their tail, but out of context I thought they were variables subtracting the horizontal and vertical resolution from some of the other parameters or something :-}

Now I'm having MythTV problems, and my friend over there who is apparently one of the developers for mythTV may have abandoned me to go somewhere on holiday or something!  I should probably find a more applicable spot to cross-post the issue, to get faster help, but he got me into the trouble, right?  I'm considering just uninstalling and resintalling mythTV entirely, but not sure if that should really be necessary, or if it won't entail its own problems....  anyonje knowledgable who happens to be reading, that thread is here
[http://www.ubuntuforums.org/showthread.php?t=320304](http://www.ubuntuforums.org/showthread.php?t=320304)

MythTV is my next project to tackle.  My wife hopes I have it running before "Lost" and "24"  startup in Janurary.

---

### Post by Shiva_T on 2006-12-20
Hi everyone,

I too am having trouble getting my Samsung HL-S6187 DLP to work with my nVidia 7600GT over DVI-HDMI. The max resolution I can currently set it to is 1280x720 with siginificant overscan. In Windows, I'm running 1768x992. I have two questions:

1. How do I extract the relevant timings from my Windows config? Vista's nVidia drivers aren't very good, so I haven't been able to find them yet.
2. Once I find them, what file should I edit and what line should I add to it?

Thanks, and sorry for the n00bish question :)

---

### Post by gerick on 2006-12-20
> **Shiva_T said:**
> Hi everyone,

I too am having trouble getting my Samsung HL-S6187 DLP to work with my nVidia 7600GT over DVI-HDMI. The max resolution I can currently set it to is 1280x720 with siginificant overscan. In Windows, I'm running 1768x992. I have two questions:

1. How do I extract the relevant timings from my Windows config? Vista's nVidia drivers aren't very good, so I haven't been able to find them yet.
2. Once I find them, what file should I edit and what line should I add to it?

Thanks, and sorry for the n00bish question :)

1) In WinXP, the timings are somewhere in an advanced settings tab.  You need:
Horiz Front Porch, Vert Front Porch,
Horiz Back Porch, Vert Back Porch,
Horiz Front Active, Vert Front Active, 
Horiz Scan (or Sync) Width, Vert Scan Width,
Horiz Sync Polarity, Vert Sync Polarity, 
and Pixel Clock.

2) In your /etc/X11/xorg.conf there is a place for modeline that looks something like 
```

Modeline "1768x992" 74.48 1768 1336 1472 1664 992 721 724 746 -hsync +vsync
[SIZE="1"]Just an example. Do not use this one.[/SIZE]

```
The modeline is in a format of 
```
Modeline "somenamehere" <dotclock> <H1> <H2> <H3> <H4> <V1> <V2> <V3> <V4> <HP> <VP>
```
where dotclock = Pixel Clock
H1=Horiz Front Active 
H2=H1+Horiz Front Porch
H3=H2+Horiz Sync Width
H4=H3+Horiz Back Porch
V1=Vert Front Active 
V2=V1+Vert Front Porch
V3=V2+Vert Sync Width
V4=V3+Vert Back Porch
HP=Horiz Sync Polarity [-hsync/+hsync]
VP=Vert Sync Polarity [-vsync/+vsync]

Simple formulas, but it took me weeks of searching to find out how to convert windows timings to a linux modeline

---

### Post by Shiva_T on 2006-12-20
Thanks a bunch, gerick!

---

### Post by Shiva_T on 2006-12-20
Well, I tried what you suggested, and changed the relevant section of my xorg.conf file to read as follows:

```
Section "Monitor"
    Identifier     "Samsung"
    HorizSync       32.0 - 79.0
    VertRefresh     59.0 - 79.0
    Option         "DPMS"
    Modeline "1768x992" 145.42  1768 1872 2064 2360   992  993  996 1027 +hsync +vsync
EndSection

Section "Device"
    Identifier     "7600GT"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "7600GT"
    Monitor        "Samsung"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1768x992" "1024x768"
    EndSubSection
EndSection
```

Still no luck; I don't see the 1768x992 mode under screen resolution. Any idea what might be wrong?

Thanks!

---

### Post by gerick on 2006-12-25
> **Shiva_T said:**
> Well, I tried what you suggested, and changed the relevant section of my xorg.conf file to read as follows:

```
Section "Monitor"
    Identifier     "Samsung"
    HorizSync       32.0 - 79.0
    VertRefresh     59.0 - 79.0
    Option         "DPMS"
    Modeline "1768x992" 145.42  1768 1872 2064 2360   992  993  996 1027 +hsync +vsync
EndSection

Section "Device"
    Identifier     "7600GT"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "7600GT"
    Monitor        "Samsung"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1768x992" "1024x768"
    EndSubSection
EndSection
```

Still no luck; I don't see the 1768x992 mode under screen resolution. Any idea what might be wrong?

Thanks!

Please post your entire xorg.conf and xorg.log
Log is probablyat "/var/log/Xorg.0.log"

---

### Post by Shiva_T on 2006-12-25
The log basically tells me that it's an unsupported mode. I've tried several, and copied timings over from Windows via Powerstrip exactly, with no luck.

By disabling EDID and setting ExactTimingsDVI to true, I can get it to attempt to use the custom modelines, but then my monitor tells me they're unsupported. Why on earth would they work in Windows but not in Linux? ](*,)

I'm about ready to give up on Linux altogether. It's unusable with this inferior resolution.

---

