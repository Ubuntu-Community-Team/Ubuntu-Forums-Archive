---
title: "nvidia tv-out screen size doesn't fit"
date: 2008-08-31
forum: Multimedia Software
---

### Post by brohmes on 2008-08-31
I have an 8800GT with a widescreen LCD on DVI and a 32" CRT on the Svideo connection. The LCD resolution is 1680x1050 while I think the CRT is 720x480.

Using the nvidia-settings gui, I have set up the displays to be "Separate X screens".  The problem I'm having now is that the image being sent to the TV is too large and the top, bottom and both sides of the screen run off the tv.  I can just barely see the top and bottom panels.  I have tried turning the resolution all the way down to 320x240, and while I do see more of the screen with this, it's still not all of it.

When i hook the same TV up to the same video card on my windows box, the screen fits perfectly within the tv's borders.

Is there some way that I can adjust the Horizontal / vertical size to fit my TV's screen properly?

I appreciate any help or suggestions on fixes I can try.

My xorg.conf file looks like:


```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "HP w2207"
    HorizSync       24.0 - 82.0
    VertRefresh     48.0 - 76.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GT"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GT"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
EndSection

Section "Screen"

# Removed Option "TwinView" "0"
# Removed Option "metamodes" "CRT: nvidia-auto-select +0+0"
# Removed Option "metamodes" "CRT: nvidia-auto-select +0+0, TV: nvidia-auto-select +1680+0"
# Removed Option "metamodes" "CRT: nvidia-auto-select +0+0, TV: 1024x768 +1680+0"
# Removed Option "metamodes" "CRT: nvidia-auto-select +0+100, TV: nvidia-auto-select +1680+0"
# Removed Option "metamodes" "CRT: nvidia-auto-select +0+0, TV: nvidia-auto-select +1680+0"
# Removed Option "metamodes" "CRT: nvidia-auto-select +0+0, TV: 800x600 +1680+0"
# Removed Option "metamodes" "CRT: nvidia-auto-select +0+0, TV: nvidia-auto-select +1680+0"
# Removed Option "TwinView" "1"
# Removed Option "metamodes" "CRT: nvidia-auto-select +0+0, TV: 800x600 +1680+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
EndSection

Section "Screen"

# Removed Option "metamodes" "TV: 800x600 +1680+0"
# Removed Option "metamodes" "TV: nvidia-auto-select +0+0"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "TV: 720x480 +0+0"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

Thanks,

Ryan

---

### Post by brohmes on 2008-09-01
I should also say that I've tried this using "TwinView" as well, with the same results.

Thanks,

Ryan

---

### Post by brohmes on 2008-09-02
I've now got MythTv working acceptably, using its built in x and Y offsets.  This isn't ideal though, and any program that does not have such features (particularly worried about the various emulators) will still cause a great deal of problems.

Has anyone got a solution?  Is there a way to define x and y offsets for the screen as a whole, rather than on a program by program basis?

Thanks,

Ryan

---

### Post by stoney39 on 2008-10-11
Hi
Have you had any luck fixing your problem of tv-out not fitting screen? I'm having the same problem

---

### Post by brohmes on 2008-10-12
Unfortunately, no.

I've gone back to XP, where the nvidia driver includes a utility that allows you to adjust both the x/y positioning as well as the overall screen size.  Using this, it works perfectly.

---

### Post by stoney39 on 2008-10-12
Crap, I was hoping to get it to work. Did not want to go back to XP. Hopefully someone will get this problem fixed. Love Ubuntu and the open source community.

---

### Post by anton2k on 2008-11-07
Bump

Also i have this problem i am using hdtv 37" lg hdmi to dvi dvi at gpu end any ways wondring if any one has got this working in 8.10 or that.:popcorn:

---

### Post by nicola76b on 2008-11-10
Same problem...
Ubuntu 8.10 and philips 32'' crt TV!!
:(

---

### Post by capnpayne on 2008-11-11
Same problem here...

I haven't been able to find a fix for this.  I've been dealing with it for awhile now, but I think I'm to the point where I'll just install XP this weekend.  I play lots of emulated arcade games with a sideways-rotated TV, and so obviously this issue is a big problem for me.

Funny that such a dumb little thing is causing such annoyance :(

---

### Post by anton2k on 2008-11-14
Yea i agree dude i have installed xp atm ud think the devs would look at the forums every now and then. man i want to have ubuntu running as my main desktop with compiz fusion but with all this over scan its to anoying plzzzzzzzzzzz!!!!!!!!!!!!!!!!!! some one help us ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

---

### Post by clancymf on 2008-11-14
I too am in the same boat as you all.  I have been reading up alot and my overscan is preventing me from using my TV.  

I am trying to learn everything I can about the xorg.conf file and how to insert custom modeline files.  What type of video cards do you all have. 

Mine is an onboard 9300 nvidia.  Its brand new so Im hoping the lastest driver release today will fix some of my issues.

---

### Post by anton2k on 2008-11-15
Hi clancymf i have a 8800gt i have tryed the restricted drivers and the ofical nvidia ones as well as the nvida controll panel and the build in resoulution thing that comes with ubuntu. We should not have to mess around with xorg.conf files it would be as easy as double clicking a button or resizing hdtv after all ubuntu is supose to be easyer to use than windows well from what i have see so for no it aint. COME ON DEVS OR FORUM ADMIN STICKY THIS AND HELP US ALL OUT !!!!!!!!!!! For god sakes we just want no over scan or a resize hdtv utility!!!!

---

### Post by anton2k on 2008-11-15
Could any one who views this thread plz BUMP it it needs to get noticed and fixed TIA.

---

### Post by clancymf on 2008-11-17
Well I messed around with it all weekend and still nothing.  I was thinking about buying a new video card since my onboard one is cutting edge and the linux drivers may not be fully there but if you cant get a 8800gt working than maybe that wouldnt be a good solution either.  

I really wish they would make it easier.  I have heard that no one has overscan issues with windows.  I really want to get my htpc working :(

---

### Post by hotstyle765 on 2008-11-30
I just plugged my 8800 GTS and noticed the same problems. No matter what resolution I changed to there was an overscan. This was using the svideo out to my TVs RCA in. I still have not figured out a way to remove the overscan though.

---

### Post by Thuffir on 2008-12-02
Same problem here with a 8400 GS, and TV-OUT.

The worst thing is, that I have recently switched from ATI due to bad linux driver quality (Tearing problems, buggy 64 bit driver, etc). ](*,) Apparently there is no perfect solution for TV-OUT under linux...

---

### Post by tonyh6243 on 2008-12-02
I am having the same problem with my 8800GT. I have it going out to a Samsung 46" LCD HDTV. I lose a portion of the top, bottom and both sides. Does anyone know what is causing this?

---

### Post by anton2k on 2008-12-04
Holy crap could every one bump this topix to get it noticed plz the dev arent doing jack about it!!!!!!

[size="100"]bump![/size]

---

### Post by johnkaiman on 2008-12-14
I guess I should be attaching myself to this string - I have just brought back to life an old desk top, with xubuntu and have plugged it into an old plasma with a 720x480 native resolution, meaning I've got black bars at either side.

I'm using the 'monitor in' jack at the back - is there a simple fix?

---

### Post by SyvanX on 2008-12-15
My TV-out was ok until I decided to install the proprietary drivers.  I discovered a setting called TV Overscan in the Nvidia settings application and I just changed the slider until the picture size fit the TV.

Open the nvidia settings application either from the menu or in an xterminal

```
nvidia-settings
```

Click on the TV-Out panel, then move the Overscan slider to the right and the screen should resize while you're sliding.

Hope it helps.

---

### Post by dannalboon on 2008-12-18
BUMP!

I too have had a problem with my 8800 video card displaying the correct size picture on my TV.  I have tried everything and can get very close but then when I click on "apply" it reverts back to being oversize.  I have tried contacting Nvidia and XFX support but they don't seem to care about after sales support.

Please, if anyone has a solution please let us know.

---

### Post by SyvanX on 2008-12-20
> **dannalboon said:**
> BUMP!
Please, if anyone has a solution please let us know.

Applications > System > NVIDIA Settings 

Select TV-0 under GPU0.  Change the slider on TV Overscan.

---

### Post by dannalboon on 2008-12-21
> **SyvanX said:**
> Applications > System > NVIDIA Settings 

Select TV-0 under GPU0.  Change the slider on TV Overscan.

You lost me.  Could you please explain?

Thanks.:confused:

---

### Post by SyvanX on 2008-12-21
Sorry for the terse response.  For me the problem was due to the video card not delivering the correct video size to the TV.  This can be corrected simply by changing an option in the nvidia settings manager called TV Overscan.

You can open the settings manager by opening the applications menu, expanding Settings, and selecting NVIDIA Settings.

You will see a window pop-up with lots of options on the left.  You need to find the "TV-0" line on the left side of the window.  If you select that, there should be a slider at the top called TV Overscan.  If you increase the value of the slider, the picture size should grow to fill the TV.

This only applies if you are running the nvidia proprietary driver.

---

### Post by dannalboon on 2008-12-21
> **SyvanX said:**
> Sorry for the terse response.  For me the problem was due to the video card not delivering the correct video size to the TV.  This can be corrected simply by changing an option in the nvidia settings manager called TV Overscan.

You can open the settings manager by opening the applications menu, expanding Settings, and selecting NVIDIA Settings.

You will see a window pop-up with lots of options on the left.  You need to find the "TV-0" line on the left side of the window.  If you select that, there should be a slider at the top called TV Overscan.  If you increase the value of the slider, the picture size should grow to fill the TV.

This only applies if you are running the nvidia proprietary driver.

I feel quite dumb right now.  I am sorry I don't understand what you are trying to explain.  I don't know where the nvidia settings manager, applications menu are.  I am using XP Pro - does that make any difference?  Thanks for your patience.

---

### Post by Thuffir on 2008-12-22
> **SyvanX said:**
> You will see a window pop-up with lots of options on the left.  You need to find the "TV-0" line on the left side of the window.  If you select that, there should be a slider at the top called TV Overscan.  If you increase the value of the slider, the picture size should grow to fill the TV.

Unfortunately my problem is not how to grow the picture, but how to shrink it. On my TV screen it's a bit oversized even with the lowest overscan value.

It is not much of problem if I watch fullcreen video, but a problem for Mythtv config screens. I think I will have to solve it with the Mythtv builtin border limiting feature.

---

### Post by madmaxnj on 2008-12-22
uh oh.  I'm resurrecting an old desktop to embed in my entertainment center so I can surf the web on my TV and stuff.  I just asked for the 8800 for xmas to get a decent video out.  Looks like I'm going to have my hands full.

---

### Post by SyvanX on 2008-12-23
> **Thuffir said:**
> Unfortunately my problem is not how to grow the picture, but how to shrink it. On my TV screen it's a bit oversized even with the lowest overscan value.

It is not much of problem if I watch fullcreen video, but a problem for Mythtv config screens. I think I will have to solve it with the Mythtv builtin border limiting feature.

I don't know if you've tried, but the slider starts at 8 and it can go in either direction, you may be able to shrink it down to a manageable size as well.

---

### Post by Thuffir on 2008-12-23
> **SyvanX said:**
> I don't know if you've tried, but the slider starts at 8 and it can go in either direction, you may be able to shrink it down to a manageable size as well.

Hm... Thanks for the hint. I will try it again. Probably I will have to install the newest nvidia drivers/utilities manually. The Mythbuntu Interpid 64 stock (177.80) driver did not seem to have a slider with my 8400GS. I was experimenting with the xorg.conf overscan option which did not seem to make any noticeable difference.

---

### Post by dannalboon on 2008-12-25
I ended up getting it working but now the way I wanted.  Instead of Clone I used Dual View.  It is a pain in the backside but at least I can watch movies on my TV now without cutting out half the picture.

---

### Post by El1iP3S01D on 2009-02-18
Fellow members can u tell me if this is the answer to our Overscan problem?

[http://analogbit.com/node/23](http://analogbit.com/node/23)  I'm trying my best to c if it works, but i get lost at the Output file...Thanks for answering...

---

### Post by JoshuaRL on 2009-02-28
> **El1iP3S01D said:**
> Fellow members can u tell me if this is the answer to our Overscan problem?

[http://analogbit.com/node/23](http://analogbit.com/node/23)  I'm trying my best to c if it works, but i get lost at the Output file...Thanks for answering...

Doesn't look like it.  It's just talking about text/rendering issues I think.  We're talking about overscaling, where the resolution size is too big for the monitor/TV.

This looks like its talking about the same issue, but in Windows.  It looks like its a HDTV/HDMI/Nvidia problem, but I'm not sure where the exact fault lies.  On #ubuntu some suggested using a Crop or Zoom feature on your desired resolution and that may work.  But from [this on the Nvidia forums](http://forums.nvidia.com/index.php?showtopic=61607&hl=overscaling) if you use a component cable to connect to your TV, it acts as a workaround.

---

### Post by stevedyndiuk on 2009-03-03
> **SyvanX said:**
> I don't know if you've tried, but the slider starts at 8 and it can go in either direction, you may be able to shrink it down to a manageable size as well.

I have an nvidia 8400gs and I am trying to use my hdtv 32inch crt television for a monitor.  I am have it set up with the s-video to composite adapter and first was dissapointed that the output was 480I not 1080I.  That aside, I too cannot get the screen to shrink down to fit the tv in any resolution. I have tried various nvidia drivers and I do not have an overscaling slider anywhere.  What driver are you running and also what card are you using?  I read somewhere someone had luck with driver 174 but cannot find it in synaptics package manager.

/bump

---

### Post by JoshuaRL on 2009-03-03
> **stevedyndiuk said:**
> I have an nvidia 8400gs and I am trying to use my hdtv 32inch crt television for a monitor.  I am have it set up with the s-video to composite adapter and first was dissapointed that the output was 480I not 1080I.  That aside, I too cannot get the screen to shrink down to fit the tv in any resolution. I have tried various nvidia drivers and I do not have an overscaling slider anywhere.  What driver are you running and also what card are you using?  I read somewhere someone had luck with driver 174 but cannot find it in synaptics package manager.

/bump

I've seen the same problem.  I think the issue there is with nvidia-settings.  Apparently, in an earlier version there was an overscaling slider that could be used to adjust the problems that Nvidia has with TVs.  Not sure why they would take it out.

---

### Post by PokeParadox on 2009-03-03
I'm also in this predicament... This is the final hurdle for me to completely let go of XP... and it seems with have Nvidia to blame for not including the scaling feature.

Does anyone have any *cough* resolution to this, please?

---

### Post by JoshuaRL on 2009-03-03
If we could find an old version of nvidia-settings, maybe we could use that to fix the overscaling issue.  But I'm not sure whether it would interact correctly with the new drivers.  That's the price you pay for proprietary drivers.  Actually, I'm starting to consider ATI ...

---

### Post by briancb on 2009-03-16
I am running 9.04 with s-video on nvidia drivers at 1024x768. The overscanning is a problem how ever for the moment I am managing by incresing the size of the top and bottom panels to 40 pixels. Not ideal but at least I can play my videos. It does not seem to effect the output size using VCL.

---

### Post by Scooter74 on 2009-10-12
I know this is an old post but I just bought a Panasonic 50" last week and had this same problem. There was an option on **the TV** to turn overscan off. This has fixed it and now the picture fits perfectly using DVI-HDMI and composite. I didn't even have an option in nvidia-settings to adjust the overscan. Hope this helps.

Cheers,
Scooter

---

### Post by shnurui on 2009-10-14
randr is missing on display :0.0 error.

---

### Post by nerdkingdan on 2009-11-12
I've been struggling with this for a few weeks now, any suggestions yet?

I have Nvidia Card, Svideo out, VLC works, however the main desktop doesn't fit.

---

### Post by Bugs318 on 2009-11-18
This is an ongoing problem even in 9.10 - does anyone have anything new on this?

---

### Post by tlp on 2009-11-22
I've found a solution for this on Karmic. You need to install the latest nVidia driver/nvidia-settings program. Instructions here:

[http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html](http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html)

Once you've done this, the overscan option should be available again within the nvidia-settings program. Increasing this value with the slider should shrink your display. 

After you've configured this the way you want it, you'll need to add the 'nvidia-settings -l' command to 'System -> Preferences -> Startup Applications' to make it persistent. 

I'm using an nVidia GeForce 8600 GT.

Hope this helps!

---

### Post by Bugs318 on 2009-11-22
Amazing!  Thanks so much for this post!  Hopefully it helps everyone else as well and this thread and problem can get marked as solved?

Note, that I logged out after the install and my system locked up (or at least the screen did).  Then I reboot and things went fine from there so I do recommend a reboot!

tlp - you deserve a raise! ;)

---

### Post by gfiolo on 2009-11-24
Thanks a lot tlp!!! I thought there were no solution for this. Thanks

---

### Post by nerdkingdan on 2009-11-26
> **tlp said:**
> I've found a solution for this on Karmic. You need to install the latest nVidia driver/nvidia-settings program. Instructions here:

[http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html](http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html)

Once you've done this, the overscan option should be available again within the nvidia-settings program. Increasing this value with the slider should shrink your display. 

After you've configured this the way you want it, you'll need to add the 'nvidia-settings -l' command to 'System -> Preferences -> Startup Applications' to make it persistent. 

I'm using an nVidia GeForce 8600 GT.

Hope this helps!

Well I see the new option, however... when I install the Nvidia driver 190, my older TV on the SVideo is not showing up as plug and play and no longer available, I see the boot up process on my tv but as soon as the desktop hits the Svideo cuts out.

Now what?

---

