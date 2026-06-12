---
title: "Video tearing in 11.10 :("
date: 2011-10-15
forum: Multimedia Software
---

### Post by keithy on 2011-10-15
Hi,

I am suffering from the dreaded video tearing in Oneiric.

Have tried the usual 'sync to vblank' settings and forcing a refresh rate match in compiz to no avail.

Am running intel corei7 sandy bridge HD3000 graphics and its a 64bit 11.10 clean installation.

Can anyone help??

Thanks

---

### Post by BicyclerBoy on 2011-10-15
If this is effecting full screen video overlays then try:

Install/Run
ccsm
- select General/Composite & tick "Unredirect Fullscreen Windows".
- select Utility/Workarounds tick "Legacy Fullscreen Support".

10.04 & 11.10 use Unity/compiz composite manager.
Composite uses blitter not overlays. Blitter seems to stuff up video overlay.

This fixes the problem with 11.04 unity/compiz & nVidia.

I'm sure there are lots of people interested in how well your PC works for full screen HD video playback..

---

### Post by keithy on 2011-10-15
> **BicyclerBoy said:**
> If this is effecting full screen video overlays then try:

Install/Run
ccsm
- select General/Composite & tick "Unredirect Fullscreen Windows".
- select Utility/Workarounds tick "Legacy Fullscreen Support".

10.04 & 11.10 use Unity/compiz composite manager.
Composite uses blitter not overlays. Blitter seems to stuff up video overlay.

This fixes the problem with 11.04 unity/compiz & nVidia.

I'm sure there are lots of people interested in how well your PC works for full screen HD video playback..

Thanks for the reply,

I had already tried "Unredirect Fullscreen Windows" and have now added "Legacy Fullscreen Support"

Sadly the problem still remains with fullscreen video.

I did not have this problem with 11.04 on the exact same hardware

any further suggestions gratefully received

Thanks

---

### Post by BicyclerBoy on 2011-10-15
Are you running intel i915 driver ?
glxinfo | grep OpenGL
I would use the driver from xorg-edgers launchpad ppa.

Are you using VAAPI ? splitted desktop systems..

Try running:
driconf
& setting the vsync ..

---

### Post by keithy on 2011-10-15
> **BicyclerBoy said:**
> Are you running intel i915 driver ?
glxinfo | grep OpenGL
I would use the driver from xorg-edgers launchpad ppa.

Are you using VAAPI ? splitted desktop systems..

Try running:
driconf
& setting the vsync ..

Hi,

I appreciate your time with this

glxinfo | grep OpenGL
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Desktop 
OpenGL version string: 2.1 Mesa 7.11
OpenGL shading language version string: 1.20
OpenGL extensions:

According to driconf, I am using i965 driver

Driconf was set to 'always synchronize with vertical refresh'

I am not (knowingly!) using VAAPI

I tried xorg-edgers under 11.04 for a while but it created more problems than it solved (i guess due to its experimental nature) 

I am reluctant to try it again as it almost killed my system after its removal (despite using ppa-purge)

Any other ideas??

Cheers

---

### Post by BicyclerBoy on 2011-10-15
How do you output full screen video ?
VLC using XVideo overlay ?

Could try using openGL ..
The XVideo method has another/separate vsync setting in nvidia driver.

VA-API is a good method if you can get it to work.

vainfo

There are builds of mplayer, VLC etc with VA-API support.
MythTV 0.25 is to support VA-API.

Your video h/w has caused lots of changes in kernel & i965 video driver so it is not surprising there was risk using xorg-edgers.

---

### Post by Raffo on 2011-10-26
Same identical problem with my i5 2500 with integrated graphic. Still looking for a solution...

---

### Post by hugmenot on 2011-10-27
Do you have SwapbuffersWait on? Grep Xorg.0.log.

---

### Post by stewacide on 2011-10-27
Also getting a lot of tearing in 11.10 w/ HD Graphics over HDMI. Vsync is on in Compiz. I suspect this is the fault of the current shipping driver, very interested in what people running the edgers xorg/mesa are reporting...

p.s. I checked w/ xrandr and it reports both my internal and external displays (which are mirrored) are running being fed at 63hz, although the HDTV reports 60hz. Is there anything suspect about that? The 'tear' is a slow crawl up the screen. No-redirected fullscreen doesn't seem to make any difference.

---

### Post by stewacide on 2011-10-27
Just incase I'm not clear this pic shows the sort of thing I'm talking about. Line crawls up the screen slowly but continuously, only noticeable when things are moving a lot on screen. Does this indicate a mis-matched refresh rate or what?

Also my HDTV supports refresh rates up to 240hz: is there a way to set the refresh rate of the HDMI-out to something else to see if it works? Is the GUI option for refresh rate gone from Ubuntu?

---

### Post by Roasted on 2011-10-27
Do you guys have dual monitors? If so, I question if that's the issue.

I have a desktop with 11.10 running. One monitor runs @ 59hz and the other runs @ 60hz. I'm running an Nvidia 9600GT on it. An extensive thread can be found here:

[http://ubuntuforums.org/showthread.php?t=1570135](http://ubuntuforums.org/showthread.php?t=1570135)

I did not start the thread however later on I got heavily involved with it.

I did a few quick tests at home. I would disconnect my 2nd monitor, save my xorg via nvidia-settings GUI, reboot, and suddenly tearing was gone. Hook the monitor back up, save new xorg, reboot, and bam - same video and I had tearing back.

Likewise, I just built an HTPC using an i3 processor and a GT 440 graphics card. This too is on 11.10. No tearing whatsoever - similar findings to what I had on my desktop when I only had one monitor (which of course the HTPC only has one monitor as it's the TV).

If you guys are running single monitors, then everything I said above is irrelevant. However if you're running dual monitors that aren't identical... it may hold water to the argument...

What video cards are you guys running? What computer hardware? Graphics cards? etc?

---

### Post by stewacide on 2011-10-27
That would make sense: a slightly different refresh rate causing one of the screens (external in my case) to tear.

Do both monitors necessarily receive the same refresh rate when mirroring? I'd like to fiddle around with the refresh rate settings but I don't see them anywhere in 11.10 (could swear they used to be exposed), and worry about doing it with xrandr since there's no automatic rollback ("keep these settings?") if anything goes wrong.

---

### Post by cuyo01 on 2011-10-28
for me no other solution worked except for disabling compositing; since I dont like that, Installed kubuntu desktop, gnome shell and unity 2d and start to mess with many configurations settings, my desktop environments are now "slighty broken" but think that found a possible solution that works with compositing enabled, im checking some settings to make sure these are the correct, **if anyone want to test these settings do at your own risk.**

Im using Ubuntu 11.10 upgraded from 11.04 and a video card nvidia gt240 with a monitor syncmaster 2233sn+ and proprietary drivers so dont know if this "workaround" works with intel, ati or any integrated video

with these setting i got tearfree video with mplayer/smplayer using xv, vdpau, gl, gl (fast), gl (yuv), gl2 and gl2 (yuv) driver outputs in unity3d, gnome classic, gnome classic (no effects), in gnome 3 works only with gl/gl2 outputs, in unity2d no matter what there is horrible tearing, in kubuntu a had no tearing with desktop effects enabled (default)

**Please read all before attempting to make these changes to your system**

Instructions:

you need to use a desktop environment which uses compiz, unity3d and gnome3 and gnome classic will do so log off and relogin with one of these

open a terminal and type gconf-editor

go to /apps/metacity/general/ and look for the *compositing_manager* option and make sure that is unticked and look the option *compositor_effects* and make sure is ticked

close gconf-editor

Is necessary to disable metacity as a compositing manager, when enabled there is tearing even with the all settings below enabled and all the driver outputs in mplayer

launch compiz settings manager, if you dont have it you can install it with synaptic.

in general:
composite plugin enabled (tick)
opengl plugin enabled (tick)
gnome compatibility plugin enabled (tick)

in utility
workarounds plugin enabled (tick)

in general/composite:
detect_refresh_rate -untick
refresh_rate n[COLOR="Red"]*[/COLOR] (you need put input a value **higher** than your current refresh rate, in my case my monitor is running at 60hz and the setting i used was 85, why? details in the end).
unredirect_fullscreen_windows -tick

in general/opengl:
sync_to_vblank -tick

in utility/workarounds:
legacy_fullscreen -tick
no_wait_for_video_sync -tick
force_swap_buffers -tick[COLOR="Red"]**[/COLOR] (warning: use with care, will cause a masive increase in gpu and cpu usage).

and in my case since im using nvidia drivers opened nvidia-settings

in xcreen 0/xserver video settings:
Sync to vblank -tick

in xcreen 0/opengl settings:
sync to vblank -tick
allow flipping -tick

dont know about ati catalyst drivers but i think there must be similar options

[COLOR="Red"]*[/COLOR] when setting the refresh rate the same as my monitor i dont have tearing but the video gets choppy when images moves horizontally, increasing this value gives me a smooth playback, with a value of 70 there is still some choppiness, with a value of 85 is perfect for me (60hz monitor)

[COLOR="Red"]**[/COLOR] the tooltip in compiz manager options alerts that this option can cause a masive overwork to the gpu and/or the cpu, in my case this never happened, with the sistem monitor my cpu in idle stays in ~4%; since there is no software similar to GPU-Z under linux that I where aware of the only way to check the load on the gpu was in nvidia-settings/Thermal settings where the temp of the gpu is the same with/without force_swap_buffers and the fan speed has no increased.


I suppose that disabling metacity as a compositing manager will disable compiz effects under gnome classic but dont have a way to check this since my desktops environments are somewhat broken (i lost all effects before when messing with many settings :P the only way to have effects in gnome classic for me is with fusion-icon)

If you use more than one desktop environment you need to apply these settings for every desktop environment since (in my case) compiz manager options uses diferent options for every desktop environment or only one if compiz is loaded with fusion-icon but dont recommend that since it will be a mess when changing from on environment to another.

For some strange reason these settings are persistent even when compiz is no loaded! for example when login in gnome-classic (without effects)

If anyone want to test these setting please report if it worked.

forgot to mention im using nvidia 285.05.09 proprietary drivers



sorry for the bad english.

---

### Post by Roasted on 2011-10-28
> **stewacide said:**
> That would make sense: a slightly different refresh rate causing one of the screens (external in my case) to tear.

Do both monitors necessarily receive the same refresh rate when mirroring? I'd like to fiddle around with the refresh rate settings but I don't see them anywhere in 11.10 (could swear they used to be exposed), and worry about doing it with xrandr since there's no automatic rollback ("keep these settings?") if anything goes wrong.

I think this is a reaction of using twin view. Think about it, my resolution gets pegged as 3360x1080. Well, I don't have a monitor @ 3360x1080!

Instead I have 1440x900 and 1920x1080 individual monitors. Since 1080 is higher than 900, that by default is used as the height. Meanwhile, since 1920 and 1440 are getting added together for width, you get 3360, hence 3360x1080.

So that is seen as one solid pane. One screen. Yes, you see it on two, but it's as if the system recognizes it as one. Couple that with improperly matched refresh rates and you have a car with 45psi on the front right tire and 30psi on the front left tire; you'll notice some inconsistencies as things won't be evenly balanced.

But like I mentioned before, if you drop one monitor and edit your nvidia (or ati, whichever you have) settings accordingly and reboot, you should see better performance. Now if you're on a single monitor with video tearing, THEN I'd be completely "what the...?!" 

In the future I intend to not jump-the-gun when buying monitors. I plan to get matching LCD panels instead of having one large one and one that I kick misc windows over to. Perhaps that, or at the very least, getting mismatched monitors that have the same refresh rate, could be the ticket to working around this issue. That said, hardware and driver support is getting better by the day, so maybe my entire synopsis above will be irrelevant with a simple update. One can only hope, right? :D

---

### Post by stewacide on 2011-10-28
Problem isn't TwinView since I'm mirroring. There's just a slow, crawling tear that goes up the external display and then starts at the bottom again when it's reached the top. I'm sure this means something obvious to someone who knows a lot about video but I do not.

---

### Post by Roasted on 2011-10-28
> **stewacide said:**
> Problem isn't TwinView since I'm mirroring. There's just a slow, crawling tear that goes up the external display and then starts at the bottom again when it's reached the top. I'm sure this means something obvious to someone who knows a lot about video but I do not.

I wonder if the same might still apply... I say that because I see that same thing on my twinview setup where I have video tearing... the only difference is my tear mark travels from top to bottom, not bottom to top like you describe.

What are you mirroring? Are you using a laptop and mirroring it to your TV or something?

---

### Post by stewacide on 2011-10-28
> **Roasted said:**
> I wonder if the same might still apply... I say that because I see that same thing on my twinview setup where I have video tearing... the only difference is my tear mark travels from top to bottom, not bottom to top like you describe.

What are you mirroring? Are you using a laptop and mirroring it to your TV or something?

Yes, mirroring laptop to TV.

I had trouble doing this at first, since the (1080p) external display didn't advertise (via HDMI) as supporting the laptops native 1600x900. I copied this mode to the HDMI output via xrandr to allow mirroring and the TV handles the upscaling just fine. 

What I think *might* be wrong is that xrandr reports both the internal and external displays operating at 60.3hz, whereas perhaps the external monitor wants an even 60.0? (could such a tiny difference matter? the TV says it supports up to 240hz but I doubt the video card is capable of that). I should be able to create a custom mode w/ xrandr to test this theory but it's a bit intimidating / I'm worried about having no display if something goes wrong, particularly since VNC also seems to be broken on 11.10 (ugh!!)

---

### Post by stewacide on 2011-10-28
Forced 60.0hz and 59.94 refresh rates with xrandr. This resulted in a much faster / less noticeable bottom-to-top moving tear. I'm pretty sure now this is 100% a refresh rate issue; I just have no idea how to figure which of xthousand possible rates is the right one!!?!?

I can't find any documentation for the HDTV (an LG 1080p LCD) specifying an ideal refresh rate, so I guess I need to keep experimenting? This is pretty annoying... I tried sending it 85hz and while the laptop's screen had no problem the TV reported no signal. If there's some other intermediate refresh rate the TV does support I don't have a clue how to find it :(

p.s. does anyone know how to force the default/prefered mode w/ xrandr? As is I can add the new modes at start-up w/ a .sh script, but I dunno the syntax to enable them by default.

---

### Post by Sir Rodness on 2011-10-29
I'm using split screen and outputting video to my TV and saw the same tearing, but I've found something that works for me though I'm not sure if this will work for everyone. After I did the vsync option in my nvidia setting and noticed the tearing still stuck around I put the same video on my main monitor and noticed tearing disappeared. My monitor and my TV were running at different screen resolutions. Figuring I had nothing to lose I decided to match screen resolutions between my monitor and tv. Interestingly enough the tearing disappeared. Again this may or may not work for you, but it's something to try. Hope this helps a few out there.

I have a Nvidia 7800 GT, HP 25" monitor and LG 42" HDTV plasma running at 1920x1080 screen resolution with no tearing.

---

### Post by stewacide on 2011-10-31
No matter what I set the refresh rate and/or resolution to manually, I can't get ride of the tearing so long as the external display is either mirrored, or the secondary display (i.e. to the right of the primary viewport). The 'nature' of the tearing will change though depending on refresh rate.

However setting the external display to the primary display (i.e. the leftmost viewport) gets rid of the tearing entirely, so that's what I'm stuck with (this is with Intel HD graphics, so the same solution seems to apply regardless of graphics hardware).

Conclusion: **turn mirroring off and move the display you want to be tear-free to the furthest left in display properties.**

---

### Post by KBD47 on 2011-10-31
> **keithy said:**
> Thanks for the reply,

I had already tried "Unredirect Fullscreen Windows" and have now added "Legacy Fullscreen Support"

Sadly the problem still remains with fullscreen video.

I did not have this problem with 11.04 on the exact same hardware

any further suggestions gratefully received

Thanks

This sounds so familiar. My video was excellent in 11.04 but in 11.10 was slow and choppy. This can offer some relief:
[http://www.youtube.com/html5](http://www.youtube.com/html5)

---

### Post by Raffo on 2011-11-06
> **Raffo said:**
> Same identical problem with my i5 2500 with integrated graphic. Still looking for a solution...

In my case the problem doesn't seem to be related to the refresh rate. I have tried to modify it, but I just managed to break unity that is not working anymore -_-

---

### Post by ian.d.rossi on 2011-11-06
For anyone this may apply to: I was facing this problem on:
- a Dell PowerEdge T100 with 
- an ATI HD5450 with 
- Ubuntu 11.10 (64 bit)

that I'm using only for an HTPC in the living room, so I don't need fancy desktop effects. 

I loaded the LXDE desktop and I'm running  with Tear Free disabled in Catalyst Control Center. HD video from Amazon and Hulu look spectacular. There isn't one bit of tearing or chopping.

Ian

---

### Post by beew on 2011-11-07
> **BicyclerBoy said:**
> Are you running intel i915 driver ?
glxinfo | grep OpenGL
I would use the driver from xorg-edgers launchpad ppa.

Are you using VAAPI ? splitted desktop systems..

Try running:
driconf
& setting the vsync ..

Hi, normally I would recommend xorg-edgers as well, but unfortunately it breaks Unity in 11.10. 

See point #2
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

Another reason not to update to 11.10.

---

### Post by Gremlyn1 on 2011-11-17
> **BicyclerBoy said:**
> If this is effecting full screen video overlays then try:

Install/Run
ccsm
- select General/Composite & tick "Unredirect Fullscreen Windows".
- select Utility/Workarounds tick "Legacy Fullscreen Support".


Just wanted to report in that this seems to have fixed it for me, at least in XBMC video playback.

Update: Live TV playback in MythTV is looking great as well!

---

