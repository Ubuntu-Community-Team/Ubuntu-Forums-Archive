---
title: "Horse isn't dead yet - NVidia &amp; multiple monitors"
date: 2011-08-04
forum: Multimedia Software
---

### Post by v0rt3_x86 on 2011-08-04
I realize I won't make any friends by starting off this way, but I feel it's better to be up-front and get it out there.  I've been searching these forums both directly & via Google for four days and I've found thread after thread after thread (& so-on,) about this issue with no real solution for me.  I've seen several work-arounds, but I'm not interested in circumventing the issue; I want to fix it.  Forgive me if I come off as a jerk but I'm noticeably frustrated (just ask my family.)

Having said that, let's get started.

==================================================

Ubuntu 11.04 64-bit

[NVidia driver version 280.13](http://www.nvidia.com/object/linux-display-amd64-280.13-driver.html)

Palit NVidia GeForce 8800-GT

Two screens. 1600 x 1200 @ 85Hz & 1920 x 1080 @ 60Hz

==================================================

Steps taken so far:
 Fresh install of Ubuntu 11.04.
 Boot & login.
 Run updates.
 Reboot.
 Download & install NVidia driver via the included .run file.
 - I allowed the installer to disable the Nouveau kernel driver.
 Reboot.
 Run install - success.
 Reboot.
 Try to fix it myself for four days before joining forums.

==================================================

Notes:
 I want Unity and I don't want to hear suggestions to the contrary.
 I know Xinerama hates Unity and it's not going to work until one or both are patched.

==================================================

Goals:
 Windows maximize per monitor, not across one big fake desktop.
 **Full-screen videos & games do so only on one monitor, not in the middle of both of them.**
 Mouse will _not_ lock to one screen when playing a video in full-screen mode.
 - I want to be able to watch videos/movies while doing other stuff on the other monitor.
 - I realize many people want the mouse to lock for gaming, but if you're gaming (eg. FPS,) you'd be better off dedicating resources to one monitor anyways so there's no reason for both to be on. It takes 10 seconds to switch primary monitors *shrugs*.

==================================================

Xinerama and Compiz have apparently slept with the same woman and are not only ignoring each other, but fighting when we make them try to talk to each other and neither has any interest in reconciliation.

TwinView is a failboat because full-screen video goes in the middle so it's only suitable for projectors.

Separate XScreens is nice if you want to look at a blank desktop on your 2nd monitor...  and here's why I'm starting this thread.

I've read no less than five threads where someone will say something like "I don't know what you mean," or "just download (insert workaround application,) and switch around," and so-on.
 - If I **have** to do it that way, fine, but I don't want to.

Here's what I'm trying to figure out:  My second monitor has wallpaper and my mouse will scroll to it.

No Unity
No bar at the top
No icons
No ability to do anything but right-click.

==================================================

I want to:

1.) Be able to either
 - a.) Drag a window over & have it act like it's on it's own computer.
 - b.) Start applications and have them launch on that screen...and act like they're on their own computer.

2.) Not fight with my computer about full-screen video.

Suggestions?

---

### Post by BicyclerBoy on 2011-08-05
Firstly I not using multi monitors on 11.04 yet or any time soon.
The 11.04 box is running gnome 3 in classic mode.
Unity is nice on a netbook.

Xinerama does not work properly any more or with good openGL performance. It is not likely to be fixed, it is history..
You have to use twinview or seperate X screens or SLI mosaic or base mosaic (quadro only).
Twinview only works with 2 screens & the refresh rate must be same.
Mosaic (base & SLI) is only supported on professional priced quadro cards (really sucks).

Twinview setup can be made to trick apps to full screen on one screen..
Separate X screens is the only setup that allows full independent screen config & no video or openGL degradation. 
Seperate X screens will not allow window dragging & icons only on primary.

Well written apps will open & full screen on the screen they are launched from..(inc MythTV, VLC, Clementine etc)
To launch from any screen/script/menu you can redirect with DISPLAY variable.

e.g.
```

#!/bin/sh
# Run MythTV front end on display 1
export DISPLAY=:0.1
mythfrontend

```This can be run from icons/menu/other script..

Possibly Unity messes all this up..don't know.
Can you try the gnome classic desktop login ?

Twinview problems
NoTwinViewXineramaInfo" X config Option
[http://us.download.nvidia.com/XFree86/Linux-x86/275.09.07/README/configtwinview.html](http://us.download.nvidia.com/XFree86/Linux-x86/275.09.07/README/configtwinview.html)

Note that the nvidia driver xinerama extension is not the same as X server xinerama & they are mutually exclusive.

---

### Post by realzippy on 2011-08-05
[I]Notes:
I want Unity and I don't want to hear suggestions to the contrary.
[/I]
Unity is a no-go with dual monitors..if you want to hear or not.
Horse is dead,get off.

---

### Post by BicyclerBoy on 2011-08-05
Thanks for clarifying..I did not know for sure that unity does not work with multi screen desktops..

---

### Post by v0rt3_x86 on 2011-08-05
> **realzippy said:**
> Horse is dead,get off.

TwinView works fine, so you're wrong.
Separate XScreens works fine, so you're wrong again.
Xinerama doesn't work, but it wouldn't work for what I need it to do anyways.

@BicyclerBoy - What you're saying seems to be exactly what I need, however I need help with the commands.

I tried doing what you did there, but it still opened in XScreen 0.  Any suggestions?  Most of what I find on the forums & online is for older versions of Ubuntu and the codes don't work or no longer apply.

:edit:
Also, I managed to launch my home folder in it by mistake (No lie - fell asleep on the keyboard,) but it didn't have a toolbar (close, minimize/maximize, etc.) on it so I couldn't make it go away. wtf?

---

### Post by BicyclerBoy on 2011-08-06
Remember I'm still using 10.04.

The DISPLAY variable only works with separate X screens.

DISPLAY=":0.1" vlc
launches VLC on 2nd screen for me..

Are you logged into a gnome classic desktop or unity ?

---

### Post by v0rt3_x86 on 2011-08-06
> **BicyclerBoy said:**
> Remember I'm still using 10.04.

The DISPLAY variable only works with separate X screens.

DISPLAY=":0.1" vlc
launches VLC on 2nd screen for me..

Are you logged into a gnome classic desktop or unity ?

Ubuntu 11.04 64-bit

[NVidia driver version 280.13](http://www.nvidia.com/object/linux-display-amd64-280.13-driver.html)

Palit NVidia GeForce 8800-GT

Two screens. 1600 x 1200 @ 85Hz & 1920 x 1080 @ 60Hz
 - Setting: "Separate XScreens"

I have a blank desktop to my right which I can a.) move my mouse over to. b.) right click for the standard desktop drop-down menu BUT it does NOT have keyboard focus.

:edit: I tried that code and it yelled at me.

---

### Post by BicyclerBoy on 2011-08-06
Are you logged into gnome classic desktop or unity ?

Shame nvidia will not let the consumer masses use mosaic...

That keyboard focus is very odd..certainly different to 10.04 (& Xorg 1.7.6).
I have mouse & keyboard (& IR RC) input active on both screens.

---

### Post by v0rt3_x86 on 2011-08-06
> **BicyclerBoy said:**
> Are you logged into gnome classic desktop or unity ?

Shame nvidia will not let the consumer masses use mosaic...

That keyboard focus is very odd..certainly different to 10.04 (& Xorg 1.7.6).
I have mouse & keyboard (& IR RC) input active on both screens.

I'm a 'tard; I thought it was in the other post.

Unity.

---

### Post by BicyclerBoy on 2011-08-06
Well logout...then select your user....then select gnome classic ...type in password-login...

Does that work any better ?

---

### Post by v0rt3_x86 on 2011-08-06
I don't want to work around the problem. I want to know why I can't get anything to show up on that XScreen unless by mistake lol.

Assume I had Ubuntu Classic going.  If I had it setup for two separate XScreens, what would I be seeing?

---

### Post by BicyclerBoy on 2011-08-06
Trying classic is as simple as logging out & in again..
It would be a debugging step..if it works then Unity is very likely the problem.
If it does not work then it could be kernel, Xorg or nVidia driver..

Finding out if the keyboard works with classic could be very useful info..

---

### Post by v0rt3_x86 on 2011-08-06
It's already been established that it actually only works the way it should in Ubuntu Classic (No Effects.)

Unity: No control over 2nd screen with no task bars, launchers, icons, etc.

Ubuntu Classic: You get your top & bottom bars back, but the keyboard still doesn't focus on the second screen and the min/max/close bar is missing.

Classic (No Effects): Works as expected.
- Only thing I have a problem with is full-screen video won't stay that way when you move your mouse to the other window.

So we need to address:

How to make video stay full-screen when I move to the other monitor to do other tasks.
:EDIT:
YouTube (Flash,) is causing the problem. Totem seems to be behaving.

How to bind the "Windows," key to the top bar. Unity already had it setup to open the lil' Windows 7-like search box.

How to get it to work with effects.

How to get it to work with Unity.


Where would you like to start?

---

### Post by v0rt3_x86 on 2011-08-06
New glitch:  I can only run a program in one screen or the other.

For example, if I have Chromium on XScreen 0, any new instances will also open here and vice-versa.

---

### Post by BicyclerBoy on 2011-08-06
> 
It's already been established that it actually only works the way it should in Ubuntu Classic (No Effects.)
Well not in anything you posted previously that I can see..
And your current setup, in classic mode, is NOT working anything like it should either..

Your current experiences just reinforce my decision to not break a working HTPC by using 11.04.

The fact that classic does not work must point the blame at kernel, Xorg or nVidia driver.
The nVidia driver can be used with 10.04 or 10.10, I have not seen any more than the normal number of complaints.
So all I could suggest is try using 10.10 or a different ubuntu 11.04 distro desktop like kde or Xfce.
I have no other suggestions.

---

### Post by realzippy on 2011-08-06
> **BicyclerBoy said:**
> Thanks for clarifying..I did not know for sure that unity does not work with multi screen desktops..

No,I never said this.With
*Unity is a no-go with dual monitors..*
I wanted to say that it does not improve the work flow,what a dual monitor system should.Open gimp,edit a picture,different layers in different windows
eg...then try to browse through the layers,it becomes a horror....
More ?:
[http://ubuntuforums.org/showthread.php?t=1754606](http://ubuntuforums.org/showthread.php?t=1754606)

---

### Post by BicyclerBoy on 2011-08-06
Well your definition of "no-go" does not marry with mine..

So for the OPs sake..
In your experience should 11.04  & the unity3d desktop be functional with dual monitors using twinview or separate X screens ?
And by "functional" I mean function as intended by the developers.

Your posted Unity thread was interesting..
I don't read the 11.10 forums, 11.04 running gnome classic just looks the same as 10.04 so I can wait for the next LTS release.

---

### Post by realzippy on 2011-08-06
..imho unity isn 't functional at all when using gimp or open office
with a few instances of a document simultaneously opened.
With 2 monitors it becomes even worser.
..but don 't want to turn this thread into another unity discussion.

---

### Post by v0rt3_x86 on 2011-08-06
> **realzippy said:**
> ..but don 't want to turn this thread into another unity discussion.

Good.


> **BicyclerBoy said:**
> So for the OPs sake..
In your experience should 11.04  & the unity3d desktop be functional with dual monitors using twinview or separate X screens ?
And by "functional" I mean function as intended by the developers.

TwinView works for the most part, but going full-screen in video makes it center. The idea is that if you have two projectors, for example, it would display one screen. Since one screen is a CRT on my desk and the other is my TV, this doesn't work so well lol.

Let's put it like this: If I run Ubuntu Classic (no effects,) and Xinerama, it works nearly exactly how I want it.
The **only** thing that doesn't work yet is Flash videos drop out of full screen when they lose focus (which is pretty stupid, but oh well... it's the ONLY thing that isn't working in this situation so I won't complain.)

The million-dollar question is this: How do we get Unity to do the same thing I can do w/o effects in Classic?

(p.s. - Classic with effects (Compiz,) doesn't work... You get the desktop, but nothing else.)

---

### Post by BicyclerBoy on 2011-08-06
That twinview full screen problem may not be fixable..

Chapter 13 of nVidia driver readme states..
The nVidia driver automatically loads a xinerama extension that is used to communicate the screen info to desktop managers.
This extension can not load if xinerama (Xorg) is enabled.

Maybe there is some config in the compiz settings tool CCSM that can be used to fix the screen reporting.

Xorg xinerama means:
-  no openGL
-  maybe no VDPAU
-  no composite extension  (compiz etc)

Twinview
- hardware video overlay only on primary monitor

The only proper functioning nVidia  solution is quadro mosaic..or windows.

---

### Post by bcschmerker on 2011-08-06
> **BicyclerBoy said:**
> ...Chapter 13 of nVidia driver readme states..
The nVidia driver automatically loads a xinerama extension that is used to communicate the screen info to desktop managers.
This extension can not load if xinerama (Xorg) is enabled.

Maybe there is some config in the compiz settings tool CCSM that can be used to fix the screen reporting.

Xorg xinerama means:
-  no openGL
-  maybe no VDPAU
-  no composite extension  (compiz etc)

Twinview
- hardware video overlay only on primary monitor

The only proper functioning nVidia  solution is quadro mosaic..or windows.Thanks for a confirmation on an issue that I anticipated in preparing a rebuilt eMachines®/Acer® EL1210-09 for projection-computer duty.  The nVIDIA® FGLRX package X server runs both the planar GeForce® 8200 and an Asus® EN210/DI/512MD2(LP) well, but I did not anticipate, nor can I use for my project, a two-display-wide desktop that could be attributable to the Xinerama port in the FGLRX package.

As of 6 August 2011, the GF8200 runs a 26" RCA LCD television via the HDMI port; the EN210, the DVI side of an eMachines®/Acer® T19E6:  It looks as though I'll be reconfiguring the EN210 as primary, the planar GF8200 as secondary for the tests that I need continue in my projection-computer development.

---

### Post by BicyclerBoy on 2011-08-07
I should have defined "properly functioning multi-head multi-GPU solution".

Not using ubuntu 11.04 may lead to improved functionality.

Note that GT210 is not a suitable video card for HD video playback.
The 8200 is suitable for office duty.

There are no video-overlay/openGL/VDPAU problems with separate X screens.
Just that it is not a nice multi-display desktop environment.

The FGLXR driver is the AMD/ATI behemoth ??

---

### Post by v0rt3_x86 on 2011-08-08
So basically NVidia is saying "FUUUUUUUUUUUUUUUUUUUU," when it comes to Unity/Compiz & they don't care?

---

### Post by bcschmerker on 2011-08-08
The EL1210-09 project is performance-limited at the display units anyway.  The 26" RCA® LCD television that I'm using on the projector output (run at 1024x768), for configuration and application-testing purposes, has similar performance limitations to an Optima® projector at the site of installation; and I reckon the T19E6 (1440x900) good enough for command and control.  As a slimline, the EL1210-09 is already limited in what upgrade video cards it can use, as it requires half-height PCI-Express x16; even with the retrofitted Shuttle® PC6300002 PSU, it has only 17A available on the +12VDC bus for the planar (which is still better than the 14A of the LiteOn® PS-5221-06 that it supersedes), not counting the separately-powered ATX12V for the CPU (the PC6300002 has two 16A busses in addition to the aforementioned 17A).  So far, most cards with the GeForce® GT 520 require that 18A of +12VDC be available at the motherboard, and the 210 can get by with 16-17A at the mobo.

The issue at hand for me is how to isolate one GPU for the slideshow output of Sun® OpenOffice.org, meaning no Xinerama or TwinView needed or desirable.

---

### Post by BicyclerBoy on 2011-08-08
GT520 & GT210 are probably the best video card for your requirement then.
I doubt there are any lower power video cards that still have any performance.

I believe you should be able to use the same video driver for both cards, so one X server with 2 screens.


I would blame Unity, if anyone, for the current mess.

---

### Post by .... on 2011-08-08
> **v0rt3_x86 said:**
> So basically NVidia is saying "FUUUUUUUUUUUUUUUUUUUU," when it comes to Unity/Compiz & they don't care?
The same problem occurs with ATI's blob (Catalyst). Unity is under heavy development and Ubuntu devs use open-source drivers for development. Getting proprietary drivers to work is a secondary priority. In the mean time, there's Unity2D for whoever wants to use Unity with proprietary or deficient 3D drivers.

---

### Post by v0rt3_x86 on 2011-08-09
> **.... said:**
> In the mean time, there's Unity2D for whoever wants to use Unity with proprietary or deficient 3D drivers.

Care to elaborate?  I'd like to know what the key differences are. Also, does it still run Compiz? If so, that also seems to be a key limiter in running dual monitors since Ubuntu Classic with Compiz doesn't do it right, either.

---

### Post by Elfy on 2011-08-09
@ bcschmerker - please do not hijack threads, create your own support thread.

---

### Post by BicyclerBoy on 2011-08-09
> 
@ bcschmerker - please do not hijack threads, create your own support thread.@piskie
Who pressed your buttons ?
The hijacker wasn't really looking for support just a discussion..too bad.

---

