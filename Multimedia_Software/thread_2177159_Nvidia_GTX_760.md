---
title: "Nvidia GTX 760"
date: 2013-09-27
forum: Multimedia Software
---

### Post by DeMus on 2013-09-27
[COLOR=#000000][FONT=sans-serif]Hi,[/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]I installed Kubuntu 12.04 (latest version) and I am wondering which nvidia driver should I install for my GTX 760 card. At the moment, when I look in Muon I see installed:[/FONT][/COLOR]
```
[COLOR=#000000][FONT=sans-serif]jockey-common[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]jockey-kde[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]linkwinnvidiahack4[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]libvdpau1[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]nvidia-319[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]nvidia-common[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]nvidia-settings-319[/FONT][/COLOR]
```

[COLOR=#000000][FONT=sans-serif]It is a powerful card but when I watch a video, or when I scroll in my webbrowser, I see "lines" on the screen which seem to divide the picture into two parts, one updating a fraction of a second later then the other part. It is annoying to say the least.[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]I had that with my previous card (FX 8500GT) but with this new card I thought I had a fast card, plenty of RAM (2GB) so the whole picture (1920*1080 pixels) should be updated fast enough to see a smooth picture. Turns out this is not possible.[/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]After installing the OS what should I do to get the perfect driver, which one should I install? Do I need the libvdpau1, do I need the others I installed, do I need something else?[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]Who can help me with this? Please. I have a fast computer, a nice full HD monitor, a great graphics card but a terrible picture.[/FONT][/COLOR]

---

### Post by peeteedee on 2013-09-28
What's the recommended video driver under System/Additional Drivers? :confused:

As for what packages to install first, I'd say the restricted-extras are a good start.

---

### Post by Yellow Pasque on 2013-09-28
> nvidia-319
That's the one.

---

### Post by DeMus on 2013-09-29
I have the 319 driver, but I have more, see the list in my original post. Are they all necessary or is it better to uninstall some of them?
I really would expect that with this new computer I would have power enough to fill a screen without hickups:
Asus M5A97 R2.0 Motherboard
AMD FX-8350 4000 AM3+ processor (running at 4400MHz)
Geil D316GB 1866-919 RAM (16GB)
Asus 2GB D5 X GTX760-DC2OC Graphics card

What else is there to do?

---

### Post by Bucky Ball on 2013-09-29
*Thread moved to **Multimedia & Video**.*

---

### Post by Yellow Pasque on 2013-09-29
That list is correct. It sounds like you are experiencing "video tearing" issues..

---

### Post by Tyler_Dence on 2013-09-29
run `jockey-gtk` and make sure your driver is selected as active.

---

### Post by DeMus on 2013-10-08
Temüjin,

Sorry for the late response but I have been on holiday. "Video tearing" issues sounds about right. But what can I do about that?
Is it possible to use the GTX 760 card with Kubuntu 12.04? reason for asking is I use kernel 3.2.0-54-generic. Are there any modules available for this kernel to work with the 319 nvidia driver?
I could install a newer version of Kubuntu but thing is I installed the alternate version on 5 raid disks. Since 12.10 (k)ubuntu stopped releasing the alternate versions and now it is impossible for me to install the OS on raid disks. I have seen several ways how to do it but I think I will be completely lost. So I have to stay with 12.04 for the time being.
Hate to see the screen like this, but what to do?

---

### Post by Yellow Pasque on 2013-10-08
You may want to try some different KWin settings in systemsettings -> Desktop Effects

You can also install a newer kernel if that's holding you back:
```
sudo apt-get install linux-lts-raring xserver-xorg-lts-raring
```

---

### Post by DeMus on 2013-10-08
I now use 3.8.0-32-generic and the problems are over. So it must have something to do with a kernel module which is available for this kernel and not for the older 3.2.
Thank you so much Temüjin, you made my day.


Edit:
It's not over yet. Also now when the screen is changing quickly I see the division in the picture, especially on those places where the picture moves a lot.
What else can I do to make this go away?

---

### Post by TiberiusT on 2013-10-10
I never quite got to the root problem of tearing on NVidia either, but I always do this and it sorts it out. Edit /etc/X11/xorg.conf and add:

```
Section "Extensions"
  Option "Composite" "Disable"
EndSection

```

OFC that stops desktop compositing (trendy effects which I don't care too much about) but tearing is gone.

T

---

### Post by DeMus on 2013-10-13
Thanks for the tip TiberiusT, but unfortunately it did not help.
Why is this happening? I now switched to Linuxmint 15 KDE which is a year newer than the 12.04 I used to have. Still I have this problem.
Who has some more ideas, any help is appreciated.

Edit:

Some extra info:
Nvidia driver 310.44
kernel 3.8.0-26-generic

---

### Post by TiberiusT on 2013-10-14
Hmmm...that works for me on XFCE. Anyway your problem is definitely 'tearing' - a well known issue. I can't offer any more solutions but I would install XBMC (in the repos), try playing thru that and if that doesn't work then post on their forums. That's where the pros are for issues like this. There's a tonne of threads about tearing there and it's nearly always a choice of 'compositing=video tearing' or 'no compositing=clean video'.

Here's one to get yu started [http://forum.xbmc.org/showthread.php?pid=805496%23pid805496](http://forum.xbmc.org/showthread.php?pid=805496%23pid805496)

T

---

### Post by DeMus on 2013-10-15
I made some of the changes in my xorg.conf file and I did install XBMC (not my favorite though). When I open a file in XBMC I still have the tearing, when I boot into an XBMC session it is either gone or as good as gone.(bit hard to see)
So it definitely made a change. Thing is it is a bit much to reboot every time just to watch a video and to reboot again after having seen it. Pls I have to switch off the autologin or I will boot into Mint.
In the thread you mentioned they are talking about Ubuntu 11.04, I now use the Mint variation of Ubuntu 13.04, meaning 2 years later, several new kernels, new video-cards and drivers and this problem still exists. How is that possible?
I will see if I can post something on an Nivida forum just to get some attention to the problem.
Thanks TiberiusT for your help.
Maybe you can tell me something about your setup, which card do you use, which driver, show me your xorg.conf file and maybe other files as  well just to be able to compare. It is strange that the solution you mentioned worked for you and does not do it for me. Thanks.

---

### Post by TiberiusT on 2013-10-15
> when I boot into an XBMC session it is either gone or as good as gone
That leads me to think that an XBMC session automatically kills compositing on startup - which would be logical. Yu shud go thru all settings to try and kill it in KDE.

I agree :( . Unfo tearing has always been an issue for me and it's nowhere near to being banished yet - I watch a lot of video and the issue is still there in my Xubuntu 13.04x64 install that I use now. I am also using driver 310.44. I have rolled back from 313 since I didn't find it stable.

 Without the xorg.conf mod I get tearing (OK, not too much, but enuf to annoy me), but with the Option "Composite" "Disable" line all tearing is gone. My xorg.conf is generated by nvidia-settings GUI (except last 3 lines which are my mod) and it looks like this:
```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 313.30  (buildd@lamiak)  Wed Apr 10 17:19:51 UTC 2013

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
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
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 520"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Extensions"
  Option "Composite" "Disable"
EndSection


```

IMHE, having dealt with video tearing for years now, it's all to do with the interaction between the video driver and desktop compositing. I am using XFCE which uses xfwm4 as compositor, so there's not much point comparing your and my systems. I am sure KDE (never used it) has MUCH more fancy compositing in place so I think you're best off posting in a KDE specific forum or xbmc. The latter group are a very helpful bunch and heavy Linux users so u have a good chance of getting specific advice there. Overall though I have found that testing different proprietary drivers and turning off everything to do with compositing/3D nearly always fixes the issue completely.

T

---

### Post by DeMus on 2013-10-16
Update, I am working on XBMC and Nvidia forums. Will let you know what happens. Thanks for your  help.

---

### Post by mc4man on 2013-10-16
I'd think you'll need to find a way to turn off compositing/desktop effects, ect. or use compiz/emerald instead of kwin
(compiz 0.9.x by default should eliminate tearing on most setups thru it's default enabled OpenGl settings of
Framebuffer object
Always use buffer swapping


edit:
You could look at some of the various attempts thru out this thread, you never know...
[http://www.kubuntuforums.net/showthread.php?62548-nvidia-tearing](http://www.kubuntuforums.net/showthread.php?62548-nvidia-tearing)

---

### Post by DeMus on 2013-10-16
I did switch of compositing/desktop effects all together, did not change a thing.
I saw I could install driver 319.49, did not change a bit.
How do I change the buffer swapping thing?

I also took a look at the page you recommended, but found nothing I had not done already. I am speechless.
Why does this happen? What is wrong with my system?

Thanks mc4man for your advice.

---

### Post by mc4man on 2013-10-16
I went ahead & did a kubuntu install (13.04) but i fear what I found may be less than helpful for your hardware.
Atm I only have 2 laptops, the one with a fairly recent nvidia card (660m) is of no value here as there seems to be no practical way to test video thru the nvidia adapter in linux (and the intel adapter, with some addons,  works quite well.

So the only other machine here has an older, nvidia only adapter (8400m, nv50 in nouveau
On that machine video tearing is non existent by default with nouveau unless I disable vsync in the kwin setting. Part of the reason why is nouveau supports vsync in nv50 family cards, whether your card is likewise supported in nouveau I'm not sure though probably not at the moment. (have you tried nouveau?

As far as nvidia drivers - 
I tried the 304 drivers as I know vsync in OpenGl is default enabled, available in nvidia-settings & figured there was no 'adaptive vsync' ( if adaptive vsync is in later nvidia drivers it could work against you in video payback
Again, like nouveau, there was no video tearing on the Desktop, scrolling in large files or in video's (using a tear test video), with the default settings of vsync enabled in kwin & vsync enabled in nvidia settings > OpenGl

This was again confirmed by disabling vsync in kwin which brought about tearing in all 3 area's.
(I also tested the option in kwin to disable desktop effects in fullscreen which worked fine to eliminate tearing while vsnc  was disabled (ie. tearing present in window mode

So maybe try the nvidia-304 or nvidia-304-updates, whether your card is supported I don't know, maybe ck. first. Otherwise try the nvidia-310 drivers 
(if unsure if your card is supported with those drivers & trying anyway then  be prepared to remove the driver & /etc/X11/xorg.conf from recovery if need be, pretty straightforward procedure

If still no go & no value for you in nouveau it's possible your card may get kernel side support for vsync in nouveau in the near future, again not really sure.
Otherwise you may get some relief if you used compiz instead of kwin though not sure you want to do that?/

---

### Post by DeMus on 2013-10-17
Man, you have been busy for me, haven't you? Well thank you very much.
It looks like the problem is solved. I just watched a video with fast horizontal movements and I didn't see the tearing anymore.
The situation I have now is this:

Driver: xserver-xorg-video-nouveau, Version 1:1.0.7-ubuntu1

Desktop effects: enabled, improved window management, various animations, compositing type: OpenGL, QT graphics system: native, Suspend desktop effects for full screen windows, Use Vsync.

xorg.conf file (whether in use or not I have no idea, guess not since it does mention the Nvidia driver)
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 304.51  (buildd@batsu)  Fri Oct 12 12:53:54 UTC 2012




Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection


Section "Files"
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


    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LG Electronics 24EN43"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection


Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GK104"
EndSection


Section "Screen"
# Removed Option "metamodes" "nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TripleBuffer" "True"
    Option         "Stereo" "0"
    Option         "nvidiaXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "1920x1080_60 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


mc4man and TiberiusT, thank you both so much for helping me out. You guys are great.
Thanks.

---

### Post by DeMus on 2013-10-26
Well, later it turned out things did not work like they should and I shouted too soon that the problem was solved.
I continued searching at the Nvidia forum and finally I found what could be the solution.
At the moment I use the Nvidia 331.13 driver and although in beta it is working great with the correct settings.
I use composite, have all my desktop effects again and no tearing at the moment just because of this one change I had to make in the xorg.conf file:
In section Screen:
[COLOR=#333333][FONT=Lucida Grande]Option "metamodes" "nvidia-auto-select +0+0 [/FONT][/COLOR][COLOR=#333333][FONT=Lucida Grande]**{ ForceFullCompositionPipeline = On }**[/FONT][/COLOR][COLOR=#333333][FONT=Lucida Grande]"

Everything else is back to normal, to standard, only the part in bold is added and finally after 4 weeks I can watch videos like I was used to when I still had my previous computer and monitor.
To all of you who helped me with giving ideas I say Thank you very much. I couldn't have done it without you.
Thanks again.

[/FONT][/COLOR]

---

