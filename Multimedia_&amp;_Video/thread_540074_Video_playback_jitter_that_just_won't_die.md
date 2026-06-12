---
title: "Video playback jitter that just won't die"
date: 2007-09-01
forum: Multimedia &amp; Video
---

### Post by cdekter on 2007-09-01
Hi folks,

I have been trying and trying to get this problem corrected, but after a week and many google searches, I am reaching the point of giving up.

I installed Ubuntu Feisty on my AMD64-based PC about a week ago with great anticipation. I was prepared for a learning curve, and for the fact that some things may not work right the first time. I work extensively with Linux at work so I'm not a total noob. To give you an idea, I've so far managed to get most applications I need working, and even got MythTV working nicely (a great media system btw)

The problem I am having is jittery video playback. I have tried literally everything I can find on the net and nothing has helped one little bit. Keeping in mind that nearly 90% of what I use my PC for is video playback, this is a major showstopper, enough to make me go back to Windows. This happens with  any media player, any video format. It's just a very slight jitter effect that happens about every 3-5 seconds, a couple times per second. Subtle but extremely annoying on panning shots etc.

My system:
AMD X2 4800+
2048Mb DDR2
80 gig SATA
Geforce 7900GT 256Mb
Audigy Value
LG 226WTQ screen


Here's a summary of what I've tried so far:
Change window managers: Metacity, Compiz, Beryl - no effect.
Upgrade to latest nVidia binary drivers (from nvidia site) - no effect.
Tweak all manner of settings in beryl - no effect.
Try every single video output option in eg VLC - no effect
Try various media players - no effect
Tweak settings in nvidia settings manager - no effect
I've also tried tweaking various other obscure settings I came across in my searches.

It does not seem to be a frame dropping issue - VLC reports no frames being dropped, and it happens with low quality downloaded videos as much as full HD videos. It seems like some kind of display sync issue, but I have pursued an investigation down that path with no success.

I should mention that video playback is working fine in Vista on the same machine. Also, general 3D effects are silky smooth in Ubuntu (for example the Beryl window animations). It's just the video playback that's having the problem.

Hoping somebody here has been through this - I really seriously can't accept this and will be going back to Vista full time if I can't resolve it, which I'd rather not :(

---

### Post by cdekter on 2007-09-01
OK an update - it seems this problem is somehow related to vsync. If i disable 'sync to vblank' in beryl settings, video playback is smooth (plus tearing of course). 

WIth vsync on, it does seem like the problem is global, ie if i drag a window around on the desktop, I can also see the jittery effect. 

Ideas?

---

### Post by cdekter on 2007-09-02
OK finally a solution - looks like I can avoid the problem by not using an OpenGL window manager. I booted off the live CD and just kept everything plain ol' metacity, and videos were playing flawlessly. Guess I should have paid some attention to the message in the Desktop Effects dialog box regarding it being a 'technology preview'! :P Anyway hopefully my struggles will be helpful for someone having this same problem... I think the underlying problem is the nVidia drivers, but I guess time will tell...

---

### Post by MCMcButtah on 2007-09-28
FYI: I have a very similiar system to yours (core2duo is only difference) and I have not not been able to achieve smooth video playback with compiz-fusion or beryl either. The thing that is driving me crazy though is if I enable XVMC in the playback options for mythtv the video is super smooth..BUT (always something isn't it?) I get this weird flickering. I can see the desktop behind the myth video, they switch back and forth real fast like they are fighting to be the window on top. Sometimes this doesn't happen at all. I can play the same video some reboots later under the same conditions and it doesn't do this, but it usually does. It will also go for minutes with no flicker, and then it flares up. XVMC without compiz enabled works great. My solution to this so far has been to just give up on the 3D desktop, which sucks because I really like it.

---

### Post by Maybelline on 2007-10-01
I'd just like to chime in on this as well.

Running Xubuntu Feisty with Compiz Fusion, I get a weird flickering when MythTV is set to use XvMC.

For now, I'm just using the standard video driver on Myth, and the flickering stuff goes away.

---

### Post by cdekter on 2007-10-02
I have a very strong suspicion that this stuttering problem will disappear altogether when the first kernel with CFS comes along after Gutsy. I plan on having a go at building a custom kernel with CFS, tonight, and will report back my results shortly!

---

### Post by cdekter on 2007-10-02
OK well I did the kernel build, got everything working including installing the nvidia binary drivers... I would say the stuttering is improved somewhat, but it's certainly not gone. I do recall seeing a bug report around Beryl/Compiz and video playback stutter. Presumably this is something that will be fixed in the near future, and the CFS scheduler can only improve matters further. Pity it's not being included in Gutsy! 

I have to admit, having played around a bit, it's hard to see much difference from the old-fashioned scheduler. Presumably on a modern dual-core system with loads of resources available, things are going to be pretty smooth from the get go.

---

### Post by MCMcButtah on 2007-10-02
Are we on the same page were with a distinction between stutter/flicker? Let me clarify my
experience.

Stutter: Without XVMC enabled, highdef recordings stutter (like low fps in game) when using compiz fusion, compiz, or beryl. When not using compiz or beryl video is smooth without xvmc.

Flicker: With XVMC enabled video is very smooth, but there is this strange flickering where I can see elements of my desktop and any windows I may have open breaking through the video. It is like mythtv and the background are fighting to be the top window. It does not happen with all recordings, just some but I can see no pattern to it. This has been the case with both Beryl and compiz fusion. When not using berl/compiz xvmc works like it should.

Is anyone else experiencing the flickering I described? Or is it just stutter?

---

### Post by Poene on 2007-10-04
> **MCMcButtah said:**
> Are we on the same page were with a distinction between stutter/flicker? Let me clarify my
experience.

Stutter: Without XVMC enabled, highdef recordings stutter (like low fps in game) when using compiz fusion, compiz, or beryl. When not using compiz or beryl video is smooth without xvmc.

Flicker: With XVMC enabled video is very smooth, but there is this strange flickering where I can see elements of my desktop and any windows I may have open breaking through the video. It is like mythtv and the background are fighting to be the top window. It does not happen with all recordings, just some but I can see no pattern to it. This has been the case with both Beryl and compiz fusion. When not using berl/compiz xvmc works like it should.

Is anyone else experiencing the flickering I described? Or is it just stutter?

I get that screen flicker too. I wonder what it is?

---

### Post by cdekter on 2007-10-04
Perhaps the flicker (not the stutter) is some kind of contention with Beryl. Have you tried setting (in the Beryl Settings Manager) the option for Unredirect Fullscreen Windows to be enabled?

---

### Post by Poene on 2007-10-04
> **cdekter said:**
> Perhaps the flicker (not the stutter) is some kind of contention with Beryl. Have you tried setting (in the Beryl Settings Manager) the option for Unredirect Fullscreen Windows to be enabled?

I'm running the default settings on Ubuntu. The video playback quality is poor for some reason.

---

### Post by t0n1 on 2007-10-05
I have the exact same problem. This can especially be seen on panning sequences in the video. Annoying as hell.

Update: I am not using any OpenGL window manager, yet the problem persists. Any advice?

---

### Post by CulleyS on 2007-10-08
I have the same problem and am guessing it is also related OpenGL 3D desktop.  I have an nvidia card (GeForce 8600GT) and installed the restricted drivers (used NVIDIA-Linux_x86_64-100.14.19-pkg2).  I have two monitors connected, one DFP and one LCD.  I am also running Ubuntu gutsy (development branch), kernel 2.6.22-13-generic.  AMD 64 processor.

I've tried a number of programs and tweaks as well.  Tried rebuilding the nightly build of VLC, but to no avail.  In fact, I think that made it worse, so I reinstalled my OS yesterday just to start from scratch.

When I boot into XP and use the similar Nvidia settings control center, video plays flawlessly.  I've tried in VLC for comparison, but my primary tool in Windows for video is Media Player Classic.  It's the only thing I'm using Windows for now.:)  I don't remember this stutter/flicker problem back in Feisty.  However, in Feisty, I only had one monitor working and wasn't using OpenGL 3D effects. In Gutsy, I am experiencing this on both monitors.

When I go to full screen in VLC, I also see the background, but it doesn't flicker, it's just there around the edges of the picture.  Fixed.  If I right-click on VLC to pull up the drop-down, then click off to the side of the menu, the background edges disappear.  However, I always experience what you all are calling a "stutter."  Where every several seconds, little lines or stutters come through.  It sort of reminds me of how vhs tapes will flutter when they get worn.  But, it's much quicker and doesn't scroll up the screen.

The other thing I've noticed is that with OpenGL 3D graphics, my second monitor desktop is funky.  Windows aren't fully clickable.  I can't click and drag them or resize them with the mouse.  They open and are just there.  I have to manually close them with a keyboard command or by pulling up a drop-down menu.  I can click on objects IN the window, but the borders themselves are visible, but not interactive... except for the menus/links.

I am not at home, but will try to disable OpenGL when I get there.  I wonder if there is a way to disable OpenGL 3D effects on just one of my desktops?  Monitors?  I really only watch video on the DFP anyway.

Okay, UPDATE: I disabled OpenGL 3D effects last night and that really took care of most of the video stutter and flicker problems.  However, every 5 or 10 minutes throughout a video, I now see what others are reporting with flashes of black background bleeding through or even the desktop background bleeding through.  It's sparse and very quick.  Too quick to capture in a screenshot and quite random.  Overall, a huge improvement.  Do hope that it gets to the point where running OpenGL 3D desktop doesn't adversely affect video playback.  Still, it's quick and easy enough to enable and disable should I want to watch videos. :)

---

### Post by MCMcButtah on 2007-10-24
Just wanted to update that I have upgraded to gutsy and the newest nvidia drivers and still the same issue. Video stutters and has tearing in it using compiz-fusion when xvmc is not being used. When xvmc is being used video playback is super smooth, but I get this really annoying black flickering. Somettimes windows behing my full screen video break through to the top, like the flickering is being caused by windows fighting for focus. If I minimize all windows first the problem is somewhat less, but there is still the black flickering. The weirdest thing is some recording and broadcasts play perfectly and some videos cause massive flickering. The flickering is always in the same spots in the video as well. For example one of my pbs recordings plays flawlessly all the way through, until you get to the promo stuff they have at the end. Always happens in the same spot.

I guess I just have to give up on the idea of a 3d desktop for now.

---

### Post by splitriff on 2007-10-28
I had this same problem on gutsy and fixed it by adjusting the compizfusion vsync option by going 
system>preferences>advanced desktop effect settings> General Options>display settings>refresh rate
I then set my monitor's refresh rate (75) and checked sync to vblank. dont know what vblank is, but everything is working correctly now so I hope this helps

---

### Post by anderssb on 2007-10-28
> **splitriff said:**
> I had this same problem on gutsy and fixed it by adjusting the compizfusion vsync option by going 
system>preferences>advanced desktop effect settings> General Options>display settings>refresh rate
I then set my monitor's refresh rate (75) and checked sync to vblank. dont know what vblank is, but everything is working correctly now so I hope this helps
This worked for me too. It's great to not have the annoying jitter anymore.

Thanks for the solution. :)

---

### Post by BigSilly on 2007-10-29
> **splitriff said:**
> I had this same problem on gutsy and fixed it by adjusting the compizfusion vsync option by going 
system>preferences>advanced desktop effect settings> General Options>display settings>refresh rate
I then set my monitor's refresh rate (75) and checked sync to vblank. dont know what vblank is, but everything is working correctly now so I hope this helps

Help! I'm using Gutsy with restricted nVidia drivers, and I'm having this problem with video playback too. However, when I go to system>preferences> there are no options for advanced desktop effects. How do I enable this option? Many thanks.

---

### Post by cdekter on 2007-10-29
To enable the advanced desktop effects settings you need to go into Synaptic and install the package compizconfig-settings-manager

---

### Post by kura905 on 2007-11-28
I solved my horizontal lines problem on vlc with the "Preferences>Output Modules>Alternate Fullscreen Method" option, problem solved.

---

### Post by Miroku on 2008-03-04
> **splitriff said:**
> I had this same problem on gutsy and fixed it by adjusting the compizfusion vsync option by going 
system>preferences>advanced desktop effect settings> General Options>display settings>refresh rate
I then set my monitor's refresh rate (75) and checked sync to vblank. dont know what vblank is, but everything is working correctly now so I hope this helps

wow that is the strangest thing. so when i check vblank, the jitter goes away but then expo and window picker transitions slow down and it looks bad. argh, i hope this is just a 64 bit thing and not a 32 bit problem which im returning to on next update!!

---

### Post by PC_load_letter on 2008-03-17
Hi, I'm having a "dropped frames" problem in video playback (in both VLC and mplayer), during which,  I notice that the hd light turns on. The sound playback is perfect but the picture pauses for a second or two.
I'm running Feisty 64-bit on a 1Gb, AMD64 X2 3800+ machine. Of course, I do not know how to adjust the vsync using the "Advanced desktop effects". Any help is appreciated. 

Thanks.

---

### Post by PC_load_letter on 2008-03-17
...bump, anyone? Do I need to start a new thread or something? I thought I'd better re-up an old thread that discusses my exact problem. So, is there anything I can do or is this a known bug?

Peace.

---

### Post by Miroku on 2008-03-17
> **PC_load_letter said:**
> ...bump, anyone? Do I need to start a new thread or something? I thought I'd better re-up an old thread that discusses my exact problem. So, is there anything I can do or is this a known bug?

Peace.

You can get "Advanced Desktop Settings" from the Add/Remove application if that is what you are asking. It should appear under System -> Preferences. When you open it, you can find vblank in General Options i believe.

---

### Post by PC_load_letter on 2008-03-17
I have Feisty Fawn! My "Desktop Effects" sub menu is very simplistic and has no advanced options. So, do I need to edit the xorg file?

---

### Post by Miroku on 2008-03-18
O ok. well if you have compiz running, then you should be able to get advanced desktop settings. and i would not go about editing xorg.conf yet, i remember i messed around with its vsync option and it did not do much for me.

but if you do feel comfortable editing it, make a backup and then change it.

---

