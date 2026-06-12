---
title: "ATI and smooth video, how?"
date: 2008-06-12
forum: Mythbuntu
---

### Post by netslacker on 2008-06-12
I hate to resort to publishing this question on this forum but I have searched and searched for nearly two weeks now (this and other forums) for help.  I have tried so many different things now that my proficiency with ubuntu has increased drastically!... but I'm still at a complete loss...:(

Here's my issue...
During video playback (HD, SD, DVD or ... whatever) I get horizontal anomalies in the playback video.  These are NOT interlacing issues but rather every once in a while there will be a few horizontal lines in the video that span the entire width.  They are usually on a part of the image that is moving, but not always.  It can be in a completely calm scene as well.

Here's what I've tried...
Every playback setting within myth, including every single deinterlacer. Some make the problem worse, some dont, but it's always there.
MPlayer... Xv works the best, others not so much. Same problem.
VLC media player.... same problem... all video.
SMPlayer... same.
Copied several video clips w/ anomalies to XP box where they play w/o issue.

I have the latest ATI Catalyst drivers installed from ati.amd.com (version 8.5).  I have also tried the restricted drivers in the repository but they wouldn't play higher rez video at all.  

Is this just how it is w/ ATI? or does someone have a solution that has worked for them that they can share?  I've seriously spent more time and effort on resolving this than any other problem I've had w/ linux and I just can't seem to get past it.  This is my last issue to resolve before moving my newly built Mythbuntu box into the living room and revealing it to my wife for the initial WAF!  

Here's my gear:
Gigabyte GA-MA78G ATX mobo with ATI HD 3200 Graphics / HDMI / 8ch audio.
AMD Athlon 64 5000+ BE
2GB ram
Seagate 750GB SATA
Antec PS
HDHomeRun on 100mb network

I'm running MythBuntu AMD64 8.04 w/ all system updates.

I am also pretty sure that the problem is video card driver related (but don't let this sway your thinking either... in case I'm wrong!). I am on the latest video driver so maybe an older one?! 

Thanks in advance...
R

---

### Post by Trollslayer on 2008-06-12
Are you using the restricted driver?
If you have a recent graphics card  the version in Synaptic might not detect it, go to [www.ati.com](www.ati.com) and download the graphics driver.

---

### Post by netslacker on 2008-06-12
> **Trollslayer said:**
> Are you using the restricted driver?
If you have a recent graphics card  the version in Synaptic might not detect it, go to [www.ati.com](www.ati.com) and download the graphics driver.

Yes. Using the latest ATI Catalyst driver version 8.5 dated late May (current download).

---

### Post by netslacker on 2008-06-14
anyone?

---

### Post by Canis familiaris on 2008-06-14
Try installing the graphics drivers using Envy:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Canis familiaris on 2008-06-14
> **netslacker said:**
> Yes. Using the latest ATI Catalyst driver version 8.5 dated late May (current download).

Oh you already have installed the latest driver?
You can ignore my last ost.

---

### Post by Canis familiaris on 2008-06-14
Which ATI card you use?

Also post output of:
```
fglrxinfo
```
And also what is FPS output of:
```
fgl_glxgears
```

---

### Post by gmwouters on 2008-06-15
I have the exact same problem.  Actually, my friend and I, with the same motherboard, have the same problem.  I have tried all of the standard Myth options like you have, however since I don't have any Linux expertise I am at a loss changing the Catalyst.  

Here is my set up:

Gigabyte GA-MA78G ATX mobo with ATI HD 3200 Graphics / HDMI / 8ch audio.
AMD Athlon 64 4850e
2GB RAM
SAMSUNG 500GB SATA
Antec Case, Earthwatts PS
HDHomeRun on a 10MB connection

I am running Mythbuntu 8.04

I think the problem lies with the ATI driver, however I have no idea how to fix the problem.  If anyone could help that would be awesome.  I am thinking about buying a Nvidia video card to solve the problem.  Does anyone have any advice?

---

### Post by misterspider on 2008-06-15
> **gmwouters said:**
> I have the exact same problem.  Actually, my friend and I, with the same motherboard, have the same problem.  I have tried all of the standard Myth options like you have, however since I don't have any Linux expertise I am at a loss changing the Catalyst.  

Here is my set up:

Gigabyte GA-MA78G ATX mobo with ATI HD 3200 Graphics / HDMI / 8ch audio.
AMD Athlon 64 4850e
2GB RAM
SAMSUNG 500GB SATA
Antec Case, Earthwatts PS
HDHomeRun on a 10MB connection

I am running Mythbuntu 8.04

I think the problem lies with the ATI driver, however I have no idea how to fix the problem.  If anyone could help that would be awesome.  I am thinking about buying a Nvidia video card to solve the problem.  Does anyone have any advice?


I have the identical hardware as you gmwouters, excpet for the tv card and i also have an ATI RX2600XT Heat-pipe graphics card (which is a very tight fit in my Antec NSK2480, the lid touches the heatpipe).

I also have gone through 2-3 weeks of agony to get this setup working, either using onboard graphics or the ATI card. The driver from the website does not work as well as the one through Envy (i have been told that they will be updating the website driver every month, but not sure if this will be available through Envy ever).

Almost everywhere i turned, the solution people gave was get an NVidia card, it has much better support. I had a spare GeForce 8400GS lying around, so i put it in, and it played everything perfectly. 

So i have bought a new card, MSI NX8600GT 256 DDR3 Heatpipe (for silent playback), so that i can record and watch HDTV simultaneously. I think i agree, nVidia is far easier to operate with linux.

---

### Post by netslacker on 2008-06-16
> **Anurag_panda said:**
> Which ATI card you use?

Also post output of:
```
fglrxinfo
```
And also what is FPS output of:
```
fgl_glxgears
```

fglrxinfo:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3200 Graphics
OpenGL version string: 2.1.7537 Release

fgl_glxgears:
300 frames in 5.0 seconds = 60.000 FPS
300 frames in 5.0 seconds = 60.000 FPS
300 frames in 5.0 seconds = 60.000 FPS
299 frames in 5.0 seconds = 59.800 FPS


I'm pretty sure I have the driver setup properly. But if anyone has any answers there is apparently several people with this issue....

---

### Post by netslacker on 2008-06-16
> **gmwouters said:**
> <snip>...I think the problem lies with the ATI driver, however I have no idea how to fix the problem.  If anyone could help that would be awesome.  I am thinking about buying a Nvidia video card to solve the problem.  Does anyone have any advice?

I too believe the problem lies within the ATI driver and like others, I have spent hours and weeks trying to resolve this.  Since ATI is releasing a new version on a regular basis it stands to reason that at some point this will be fixed.  In the interim, I ordered a Biostar 7200GS from Newegg.com for 26.99 + DVI->HDMI cable for 5.99 (since I planned to use the HDMI of the mobo).  Altogether w/ shipping was just over 42.00 (an expense I was hoping to avoid... ).

For those interested:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814141067](http://www.newegg.com/Product/Product.aspx?Item=N82E16814141067)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16812270113](http://www.newegg.com/Product/Product.aspx?Item=N82E16812270113)

I should have them by Tuesday and I will post back my results once I get the new card installed.  

It's a real shame, I had high hopes for the mobo and ATI 3200 graphics along with complete audio over HDMI to my HD TV... Had I known the ATI card would be this much of a hassle I would have picked a different mobo.

ATI? if you're reading this... you need to update/fix your drivers...

R

PS, if there is another solution by all means, there are lots of us that would love to hear it.

---

### Post by gmwouters on 2008-06-16
So i have bought a new card, MSI NX8600GT 256 DDR3 Heatpipe (for silent playback), so that i can record and watch HDTV simultaneously. I think i agree, nVidia is far easier to operate with linux.[/QUOTE]

misterspider

Thanks for the reply.  I was very disappointed to play with my new DVR and get the digital tearing, but I am glad to hear that the right video card can do the trick.  Hey, would you be willing to post how your new video card, the MSI NX8600GT, works for you?  Also would you happen to be running a 1920X1080 output?  When I use the GA-MA78G motherboard I get a boarder around my Vizio VU42L FHDTV10A 42" LCD.  Is that normal?  Sorry for the newbie questions.

Thanks again

---

### Post by gmwouters on 2008-06-16
> **gmwouters said:**
> 
QUOTE *****************
So i have bought a new card, MSI NX8600GT 256 DDR3 Heatpipe (for silent playback), so that i can record and watch HDTV simultaneously. I think i agree, nVidia is far easier to operate with linux.
QUOTE *****************


misterspider

Thanks for the reply.  I was very disappointed to play with my new DVR and get the digital tearing, but I am glad to hear that the right video card can do the trick.  Hey, would you be willing to post how your new video card, the MSI NX8600GT, works for you?  Also would you happen to be running a 1920X1080 output?  When I use the GA-MA78G motherboard I get a boarder around my Vizio VU42L FHDTV10A 42" LCD.  Is that normal?  Sorry for the newbie questions.

Thanks again[/QUOTE]

---

### Post by netslacker on 2008-06-16
> When I use the GA-MA78G motherboard I get a boarder around my Vizio VU42L FHDTV10A 42" LCD. Is that normal?

Yep, that's pretty normal.  I am and will be running 1920x1080 output to my TV.  Using the ATI card I got the black border but it was an easy fix since in my TV setup I had the ability to adjust the overscan.  I also believe you can do this through the xorg.conf file on your system: Option "TVOverscan" "on" or something like that (don't copy/paste that as I'm not exactly sure that will work, look it up as I believe the option does exist).

You may want to check your TV for an overscan adjustment before messing w/ your xorg.conf file as that would be the easiest way to fix it.

R

---

### Post by misterspider on 2008-06-16
> **gmwouters said:**
> 

Hey, would you be willing to post how your new video card, the MSI NX8600GT, works for you?  Also would you happen to be running a 1920X1080 output?  



I've ordered the part, when it arrives and i install i will let you know how it all goes. I'm actually fairly new to all this too. For the moment, I'm outputting from the video card to a component connection on an older television, a large flat screen is next on the shopping list, so i dont think i can answer your second question.

---

### Post by gmwouters on 2008-06-17
Quote******************
> **netslacker said:**
> Yep, that's pretty normal.  I am and will be running 1920x1080 output to my TV.  Using the ATI card I got the black border but it was an easy fix since in my TV setup I had the ability to adjust the overscan.  I also believe you can do this through the xorg.conf file on your system: Option "TVOverscan" "on" or something like that (don't copy/paste that as I'm not exactly sure that will work, look it up as I believe the option does exist).

You may want to check your TV for an overscan adjustment before messing w/ your xorg.conf file as that would be the easiest way to fix it.

R

QUOTE******************************

Netslacker thanks for the help.  

I was able to find in my TV’s menu an over scan option for the vertical, however there is no option for the horizontal.  I tried putting Option “TVOverScan” “0.5”, Option “TVOverScan” “on”, and Option “TVOverScan” “true” in the device section of xorg.conf, but it did not seem to have any effect on the TV screen.  I am not sure if that is also an ATI video card problem.  I did some online searching and it seemed like everyone using the Option “TVOverScan” had Nvidia cards.

Well, at least half my problem is solved by using the TV’s over scan.  Is it possible that a different video card could solve the boarder problem?

---

### Post by sydbat on 2008-06-18
Not sure if this fits here or not, but I have similar problems with my ATI card (older x600), including not getting envyng to work at all (white screen)...but fglrx does work. While I have yet to get my DVD working, I have noticed the same type of flickering with other video intensive apps (like some games). I had turned the proprietary ATI driver off, which defaulted to the Ubuntu driver after reboot. With both I am able to fully use Compiz, but the default Ubuntu driver allows for no flicker in above mentioned apps, but has some issues of its own.

So, my question is, is there a way to change the video driver for a particular app (including DVD playback) without having to turn off the ATI driver and reboot?

---

### Post by debenbain on 2008-06-18
ATI has a new driver out today; when you get a chance, can you let me know if that fixes your problem.

Also, while using the NVidia card, are you able to use the HD video decoding from the ATI chipset?

Sincerest thanks

---

### Post by chalewa on 2008-06-18
i just installed the new driver on my machine...

playback seems to be a lil bit better.

i watched a 720p mkv last night that had a few horizontal lines, but looks to be slightly smoother today with 8.6...but it could just be hopeful thoughts i dunno. 

just out of curiosity what video players/codec combos/preferences does everyone use. I typically just use a vanilla vlc setup, but i have heard better/worse successes with other preferences selected?

---

### Post by chalewa on 2008-06-18
> **netslacker said:**
> fglrxinfo:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3200 Graphics
OpenGL version string: 2.1.7537 Release

fgl_glxgears:
300 frames in 5.0 seconds = 60.000 FPS
300 frames in 5.0 seconds = 60.000 FPS
300 frames in 5.0 seconds = 60.000 FPS
299 frames in 5.0 seconds = 59.800 FPS


I'm pretty sure I have the driver setup properly. But if anyone has any answers there is apparently several people with this issue....


also, your FPS should be like way higher than that....

chalewa4bambu@chalewa4bambu-desktop:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
3397 frames in 5.0 seconds = 679.400 FPS
3544 frames in 5.0 seconds = 708.800 FPS


and that is with an x600

---

### Post by JugeHuge on 2008-06-19
Here is my specs with same renderer

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3200 Graphics
OpenGL version string: 2.1.7412 Release

fgl_glxgears
Using GLX_SGIX_pbuffer
2044 frames in 5.0 seconds = 408.800 FPS
2243 frames in 5.0 seconds = 448.600 FPS
2524 frames in 5.0 seconds = 504.800 FPS

Here is my xorg.conf
```

# xorg.conf (X.Org X Window System server configuration file)
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

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "fi"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "TexturedVideo" "on"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
EndSection

```

have you runned command aticonfig --input=/etc/X11/xorg.conf after changing xconf??

I have read from this thread that there is amdpcsdb where aticonfig write xorg.conf data and fglrx read it totally ignoring xorg.conf even if you change it.. 

[_Setup an ATI card with the new FGLRX drivers for Compiz-Fusion_]("http://forum.compiz-fusion.org/showthread.php?t=6794")

i have kept my xorg.conf as simple as possible

---

### Post by chalewa on 2008-06-19
> **JugeHuge said:**
> Here is my specs with same renderer

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3200 Graphics
OpenGL version string: 2.1.7412 Release

fgl_glxgears
Using GLX_SGIX_pbuffer
2044 frames in 5.0 seconds = 408.800 FPS
2243 frames in 5.0 seconds = 448.600 FPS
2524 frames in 5.0 seconds = 504.800 FPS

Here is my xorg.conf
```

# xorg.conf (X.Org X Window System server configuration file)
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

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "fi"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "TexturedVideo" "on"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
EndSection

```

have you runned command aticonfig --input=/etc/X11/xorg.conf after changing xconf??

I have read from this thread that there is amdpcsdb where aticonfig write xorg.conf data and fglrx read it totally ignoring xorg.conf even if you change it.. 

[_Setup an ATI card with the new FGLRX drivers for Compiz-Fusion_]("http://forum.compiz-fusion.org/showthread.php?t=6794")

i have kept my xorg.conf as simple as possible



strangely i can only see the first part of your post until i try to quote you...

the only aticonfig that i have run is the initial command right after install. Is the video working any better for you?


edit1: haha now i can see the whole post
edit2: that compiz post is pretty good... i am going to try all that when i get home, i think that i am also going to try to compile compiz from git. 

Also, are you trying to playback video with compiz turned on?

---

### Post by JugeHuge on 2008-06-19
I tried with that compiz guide but i got my system so messed up that i had to reinstall mythbuntu.. :)

I don't have compiz installed..

Well video is running quite smoothly but occasional tearing occurs.. mostly when there is color fading in video..

I'm waiting that new 8.6 driver to come from repositories.. There was some promising fixes in it..

---

### Post by netslacker on 2008-06-20
> **chalewa said:**
> also, your FPS should be like way higher than that....

chalewa4bambu@chalewa4bambu-desktop:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
3397 frames in 5.0 seconds = 679.400 FPS
3544 frames in 5.0 seconds = 708.800 FPS


and that is with an x600

Agreed.

I was able to get ~750fps after I re-installed the driver (again) and ~1900 fps using glxgears.  However, the same tearing still occurred in all my video playback. 

I haven't tried the new 8.6 driver (and frankly don't plan to either).  I have, however, installed an nvidia 7200GS video card (26.99) to get past this problem.  I'll revisit it in a couple of months once there have been some more driver releases.

I recommend to anyone reading this post that, after exhausting all your options to resolve this, you just buy a cheap nvidia card - nothing special is required.  I'd hate to recommend this as a solution on this thread as I would really like to see the ATI graphics work (especially for me), but if you're like me and just need it to work and don't have the time to spend - go nvidia.  I'll come back to this later in the summer before the TV season starts in September to see if I can resolve the issue.  For now, I'll be content just to use the system w/ an nvidia card.

Cheers,
R

---

### Post by netslacker on 2008-06-20
> **netslacker said:**
> Agreed.

I was able to get ~750fps after I re-installed the driver (again) and ~1900 fps using glxgears.  However, the same tearing still occurred in all my video playback. 

I haven't tried the new 8.6 driver (and frankly don't plan to either).  I have, however, installed an nvidia 7200GS video card (26.99) to get past this problem.  I'll revisit it in a couple of months once there have been some more driver releases.

I recommend to anyone reading this post that, after exhausting all your options to resolve this, you just buy a cheap nvidia card - nothing special is required.  I'd hate to recommend this as a solution on this thread as I would really like to see the ATI graphics work (especially for me), but if you're like me and just need it to work and don't have the time to spend - go nvidia.  I'll come back to this later in the summer before the TV season starts in September to see if I can resolve the issue.  For now, I'll be content just to use the system w/ an nvidia card.

Cheers,
R
looks like I may have jumped ship too soon?!? ... I'll still wait to see how this all plays out...

[http://tech.slashdot.org/tech/08/06/19/2113242.shtml](http://tech.slashdot.org/tech/08/06/19/2113242.shtml)

[http://www.phoronix.com/scan.php?page=article&item=amd_evolution&num=3](http://www.phoronix.com/scan.php?page=article&item=amd_evolution&num=3)

---

### Post by JugeHuge on 2008-06-20
> **netslacker said:**
> looks like I may have jumped ship too soon?!? ... 

Another lost soul who doesn't have enough faith.. :) AMD/ATI have noticed linux community also and therefore i still have faith on them to make their product support on linux better.. 

I also have occasional tearing on videos but not so much that it would bother me.. I'm waiting to get fix on that.. 

from 8.6 drivers release notes:
This release of the Catalyst™ Linux software driver introduces UYVY and YUY2 pixel format support. This support provides interleaved stream support for video playback applications such as TVTime and MythTV.

and resolved issues list is promising.. So have faith and show some support to AMD/ATI and they will reward us with better drivers..

what a speech.. :lolflag:

---

### Post by netslacker on 2008-06-20
> **JugeHuge said:**
> Another lost soul who doesn't have enough faith.. :) AMD/ATI have noticed linux community also and therefore i still have faith on them to make their product support on linux better.. 

I also have occasional tearing on videos but not so much that it would bother me.. I'm waiting to get fix on that.. 

from 8.6 drivers release notes:
This release of the Catalyst™ Linux software driver introduces UYVY and YUY2 pixel format support. This support provides interleaved stream support for video playback applications such as TVTime and MythTV.

and resolved issues list is promising.. So have faith and show some support to AMD/ATI and they will reward us with better drivers..

what a speech.. :lolflag:

Actually, I gave ATI a good, long, hard look and spent hours and hours trying to get smooth video from the card.  Trust me, I bought the board I did because it had ATI/HDMI and I could do a complete package in one deal.  It's just at some point enough is enough and I have to move on to something that DOES work.  I was not at all expecting the troubles I had w/ the ATI card, and frankly it was a huge dissapointment.  But, all is not lost, I do indeed plan and hope to use the IGP ATI graphics in the future once the drivers are up to snuff.  It's just for now, I need it to work and work well and I'm not tolerant of video tearing (to the level I had it) when there is a cheap option that will resolve it.

If someone has used the new 8.6 drivers with an HD 3200 and does not get video tearing, please post it here.  I'll switch back to the ATI card once I see that the issue is resolved.

---

### Post by JugeHuge on 2008-06-21
I also have ATI HD 3200 on my system and i knew that there going to be tons of problems with ATI and HDMI.. I haven't got fully working audio through HDMI and tearing problem still exists.. 

In Linux world it's always problematic if you get cutting edge hw..

well i let you know how 8.6 behave when i get them through repositories.. Not planning to build them by myself..

---

### Post by netslacker on 2008-06-21
> I also have ATI HD 3200 on my system and i knew that there going to be tons of problems with ATI and HDMI.. I haven't got fully working audio through HDMI and tearing problem still exists..

In Linux world it's always problematic if you get cutting edge hw..

well i let you know how 8.6 behave when i get them through repositories.. Not planning to build them by myself.. 

Actually, audio over HDMI worked fairly easily for me.  It's not bound to the ATI drivers but rather is detected by ALSA and appears as a second sound card.  To make audio over HDMI work, simply run "aplay -l" on the command line... look for HDMI (probably last) and note the card number and device number.  For me, this was card 1 (onboard audio was card 0), device 3.  For others, this has been 1:0.

In myth, under the audio output device, enter: ALSA:hw:1,3 (or whatever the numbers correspond to your setup).  This will direct myth sound out the HDMI.  There are similar settings for MPlayer as well, but I don't know them off hand.

Please report your success w/ 8.6 as I am interested to know if that driver version resolves the tearing.  I have been tempted tonight to try the 8.6 driver but the thought of going through the hassle for the 5th time is not appealing.

---

### Post by JugeHuge on 2008-06-21
I have configured ALSA and i got sound out but there is some weird cases when audio isn't working.. 

Playing MP3 in myth gives this kind of error
2008-06-21 10:18:18.598 Opening audio device 'hw:1,3'. ch 2(2) sr 44100
2008-06-21 10:18:18.598 Opening ALSA audio device 'hw:1,3'.
2008-06-21 10:18:18.609 AudioOutput Error: Rate doesn't match (requested 44100Hz, got 48000Hz)
2008-06-21 10:18:18.610 AudioOutput Error: Unable to set ALSA parameters

Another case is when sometime opening livetv
2008-06-19 22:24:58.414 Opening audio device 'hw:1,3'. ch 2(2) sr 48000
2008-06-19 22:24:58.414 Opening ALSA audio device 'hw:1,3'.
2008-06-19 22:24:58.523 Mixer unable to find control Master
2008-06-19 22:24:58.523 Mixer unable to find control Master
2008-06-19 22:24:58.525 Mixer unable to find control PCM
2008-06-19 22:24:58.525 Mixer unable to find control PCM
2008-06-19 22:24:58.525 Mixer unable to find control Master
2008-06-19 22:24:58.527 NVP: Enabling Audio
2008-06-19 22:25:00.219 NVP: prebuffering pause
2008-06-19 22:25:00.220 WriteAudio: buffer underrun
2008-06-19 22:25:00.952 NVP: prebuffering pause
2008-06-19 22:25:01.494 NVP: prebuffering pause
2008-06-19 22:25:01.495 WriteAudio: buffer underrun
2008-06-19 22:25:02.254 NVP: prebuffering pause
2008-06-19 22:25:02.255 WriteAudio: buffer underrun

and sometimes i get no audio and log files show..
ALSA lib pcm_dmix.c:996:(snd_pcm_dmix_open) unable to open slave

well it's not bound to ATI driver but point was that with new hardware there is always some problem in linux.. 

Those audio problems could be solved by configuring .asoundrc
or .asoundrc.asoundconf but those are so cryptic and haven't had time really study how to configure those correctly..

I will report my findings when i get there.. i build driver two times at first but then i decided that i will wait until it comes from repository.. :)

---

### Post by misterspider on 2008-06-26
> **gmwouters said:**
> 
Hey, would you be willing to post how your new video card, the MSI NX8600GT, works for you?


It really was a case of plug and play. Anything that is broadcast free to air in High Def plays perfectly, i can record and watch another at the same time no worries on my older TV. 

Funny though, now that the new driver from ATI is out, I'm tempted to put the other card back in and try!

---

### Post by netslacker on 2008-06-26
> **misterspider said:**
> It really was a case of plug and play. Anything that is broadcast free to air in High Def plays perfectly, i can record and watch another at the same time no worries on my older TV.

Same here, on a 7200GS.

> **misterspider said:**
> Funny though, now that the new driver from ATI is out, I'm tempted to put the other card back in and try!

That's funny, me too.  One of us should try it... do you want to?! ;-)

Has anyone tried the new ATI Catalyst dirver 8.6?

---

### Post by chalewa on 2008-06-26
currently using the 8.6 driver

playback looks better on a lot of videos, but others still a lot of horizontal lines. what is weird is that i can't figure out if it is limited to one file type or what. i can seemingly play 720p mkv files fine, but then some avis look like crap.

---

### Post by netslacker on 2008-06-26
> **chalewa said:**
> currently using the 8.6 driver 

playback looks better on a lot of videos, but others still a lot of horizontal lines. what is weird is that i can't figure out if it is limited to one file type or what. i can seemingly play 720p mkv files fine, but then some avis look like crap.

Thanks for the update.  

How about HD mpeg? Since this is my primary playback format (via myth).

---

### Post by chalewa on 2008-06-26
haven't downloaded any recently... i will see if i can dig a couple up and let you know. 

it was an easy install tho, probably worth just giving it a shot.

---

### Post by netslacker on 2008-06-26
> **chalewa said:**
> haven't downloaded any recently... i will see if i can dig a couple up and let you know. 

it was an easy install tho, probably worth just giving it a shot.

For me, I'd have to roll back the nvidia card and reinstall the ATI stuff to try it.  Maybe I'll give it one more driver release (next month) and then give it a go.

---

### Post by misterspider on 2008-06-30
Ok, i put my MSI ATI HD 2600 XT in and just installed the ATI driver with EnvyNG. Everything seemed pretty good, apart from HD which just seemed to struggle slightly. 

So i then downloaded the Catalyst 8.6 driver and installed. Now, all videos and things like Google Earth have a nasty flicker when watching. I realise that i can turn off  desktop effects, but thats not really the point! Has anyone got it working properly?

Also, it added an item to my applications menu in Ubuntu (ATI Catalyst Control Center), and if you open it, under 'Information' it says Driver version 8.50.3. Is that actually the latest, i downloaded 8.6?

---

### Post by dsbw on 2008-06-30
I can't 100% recall, but I thought 8.6 said 8.6 when I did it.

What I found was that it gave me corrputed Myth menus--non-Myth was fine. Playback was quite good, way better than earlier. I'm now back to 8.4 and I get some slight tearing.

---

### Post by misterspider on 2008-06-30
It seemed to install fine, i followed the installer instructions and everything happened exactly as it should. 

I rebooted and tried to select System -> Preferences -> Appearance, then the Visual Effects tab and select 'Normal'. It said proprietry drivers need to be in use for this to work, so i ticked the box and rebooted.

Was this a mistake? Does that mean i am using the older driver again?

---

### Post by dsbw on 2008-06-30
> **misterspider said:**
> It seemed to install fine, i followed the installer instructions and everything happened exactly as it should. 

I rebooted and tried to select System -> Preferences -> Appearance, then the Visual Effects tab and select 'Normal'. It said proprietry drivers need to be in use for this to work, so i ticked the box and rebooted.

Was this a mistake? Does that mean i am using the older driver again?

I believe so. Or something weirder. I did this a few times and it did not work well for me. :D

---

### Post by misterspider on 2008-06-30
Thanks dsbw, i might go back to the driver from EnvyNG, it seemed to give better results for me at moment.

---

### Post by chalewa on 2008-07-01
> **misterspider said:**
> Ok, i put my MSI ATI HD 2600 XT in and just installed the ATI driver with EnvyNG. Everything seemed pretty good, apart from HD which just seemed to struggle slightly. 

So i then downloaded the Catalyst 8.6 driver and installed. Now, all videos and things like Google Earth have a nasty flicker when watching. I realise that i can turn off  desktop effects, but thats not really the point! Has anyone got it working properly?

Also, it added an item to my applications menu in Ubuntu (ATI Catalyst Control Center), and if you open it, under 'Information' it says Driver version 8.50.3. Is that actually the latest, i downloaded 8.6?


yea mine says the same thing. 8.50.3 for 8.6

---

### Post by dsbw on 2008-07-01
> **chalewa said:**
> yea mine says the same thing. 8.50.3 for 8.6

Perhaps that's why there's a new message here saying 8.6 was just released?

---

### Post by chalewa on 2008-07-02
i think that you are misunderstanding, both myself and misterspider, installed the 8.6 drivers from the website, but after they are installed, it is listed as being 8.50.3 within the ati catalyst tool.

---

### Post by dsbw on 2008-07-02
> **chalewa said:**
> i think that you are misunderstanding, both myself and misterspider, installed the 8.6 drivers from the website, but after they are installed, it is listed as being 8.50.3 within the ati catalyst tool.

No, I understand that. I guess I don't understand why someone posted a message yesterday or the day before that 8.6 was finally out, when it's been up since June 18th, according to the ATI site. I thought maybe there was a glitch with the install script.

---

### Post by misterspider on 2008-07-20
Can i revive this thread...I'm having real problems again.

I just used EnvyNG to install the latest ATI driver (8-6 it says) and it gives me the strangest video playback. It basically does not matter which media player i choose, i have tried VLC, mplayer, xine etc. This happens to all videos, regardless of extension (avi, mpeg, flash). Im using Ubuntu 8.04. 

When i double click a file to begin a playback, the media player will open and then i will get about 1/4 second of completely black screen (entire screen). Then, all videos will playback with a nasty flicker. Also, if i have another application open (eg firefox) and Alt+Tab to it, the video (only the video, not the actual player) will still be on top and flickering, with the other application underneath. 

Using the other application (eg navigating to pages on firefox) does not hide the video, the only way to put it in the background is to kill it, either pressing stop on the player or closing the player.

Any suggestions on what to try to fix? (I should mention that all these problems disappear if i turn off desktop effects.)

---

### Post by dsbw on 2008-07-20
Yeah, I'm having trouble with it, too. [Though only inside of MythTV]("http://ubuntuforums.org/showthread.php?t=864869"). What's weird is it had started to go to hell before I updated it.:confused:

I seem to have a choice between a driver that doesn't seem to render anything well (I get, like, a frame a second off TV or DVD) and a driver that renders all right but cripples MythTV.

---

### Post by misterspider on 2008-07-20
Yeah, i took my ATI card out of my Myth box until i can get it sorted.

---

### Post by JWLou on 2008-07-20
Same here. After installing today's updates through the update manager I was presented with some pretty interesting graphics on my next Mythfrontend endeavor.

My desktop displays fine. As soon as I launch Mythfrontend I'm shown a garbled image with misaligned horizontal lines.

For now, I've removed the EnvyNG ati drivers through the EnvyNG manager. Upon reboot, I had no video so went into recovery mode from grub and ran the X Server fix. This got my display back. I went into restricted hardware drivers and enabled the ATI restricted drivers. Rebooted and Mythfrontend looked as it should and was running at full resolution. Only problem is, EnvyNG was producing better playback results - as soon as it have it reinstall the ATI drivers, it goes back to the garbled display.

---

### Post by tuxxy on 2008-07-20
ATI drivers are terrible in my experience, nVidia miles better :)

---

### Post by chalewa on 2008-07-21
for those following along at home, 8.7 is out. i am going to try it right now.


well haven't tried any video yet, but according to fgl_glxgears my fps are up over 100, and my glxgears is running at about 3500 fps

---

### Post by JWLou on 2008-07-21
Lets us know when you get around to trying video. I'm especially interested, if the 8.7 drivers work better I'm all for it. From looking at the catalyst install instructions from the forum I'm not looking forward to the install... :)

---

### Post by dsbw on 2008-07-21
> **JWLou said:**
> Lets us know when you get around to trying video. I'm especially interested, if the 8.7 drivers work better I'm all for it. From looking at the catalyst install instructions from the forum I'm not looking forward to the install... :)

What forum is that? There's an install script, is that not enough?

---

### Post by JWLou on 2008-07-21
EDIT: LOL thanks for pointing that out... I didn't even realize it was already a script.

---

### Post by dsbw on 2008-07-21
Well, I'm more-or-less in the same boat. Horizonal line displacement, so I get two half images.

For a brief moment, it adjusted itself and worked. DVD play worked (though some TV trouble)...and then when I exited and came back it was back to double-vision.

I think this can be resolved; but no clue as to where to look. Maybe an xorg.config thing. AMDCCCLE isn't providing any intersting options.

:confused:

---

### Post by JWLou on 2008-07-21
A little progress here. I updated to the 8.7 drivers and still had the line displacement. I ran ```
mythfrontend --reset
``` to reset the frontend. Still nada.

I VNCed into my mythbox so I could see the frontend menu and changed the painter from QT to OpenGL. Restarted the computer and the frontend is displaying properly. BUT... browsing to "Watch Videos" causes the program to freeze, hitting ESC a few times takes it back to the main menu where I can navigate the menu. Strange. EDIT: Actually, it isn't frozen. It appears to frozen but if I hit enter 3 more times it plays the movie. I can hear the audio but all I see is the Media Library menu.

DVD Video in VLC is smooth.

---

### Post by JWLou on 2008-07-22
Still no luck with the new driver. Does anyone know how to revert back to the repository 8.6 driver?

---

