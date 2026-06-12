---
title: "WizardPen tablet support broken in 10.10?"
date: 2010-07-05
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Noccy on 2010-07-05
My WizardPen tablet stopped working properly after an upgrade to 10.10. The tablet is properly detected, but touching the pen to the tablet simply makes the cursor jump to the top left corner.

Has anyone else experienced this or have you got any hints on how to troubleshoot or resolve it? 

I have gone over the guide available at [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen) numerous times to no avail. 

The tablet still works great on my 10.04 system.

---

### Post by AlexDS on 2010-07-30
I have the same problem over here.
But my tablet gets a little buggy form time to time, when i'm clicking the buttons on the pen, and i woul really like to see how it would work in ubuntu 10.10

What's happening to wizardpen for ubuntu 10.10 (alpha) ? Does anybody has a clue? :-s

---

### Post by ranch hand on 2010-07-30
I think you might do better in the 10.10-testing forum.  I am not sure about that but you might check with a mod and they could move it for you if they agree with me.

Have you checked the Wacom thread.  I think most of the tablets out there use some, if not all, of  the wacom project stuff.  I could be way off on that too.

---

### Post by cariboo on 2010-07-31
Moved to Maverick Testing & Discussion.

---

### Post by 23dornot23d on 2010-07-31
Just to confirm this  ......




                                  **Wizardpen**             
                                                                I thought I should bring this topic here as its to do with Maverick 10.10
( Brief explanation - these are used for the drawing tablets and pens - like G-Pen )
 The wizardpen drivers ....... do they need changing now ,,,,, so they will work on the new version,

It took me quite a long time setting these up in past versions of Ubuntu.

Has anything changed with the drivers to stop them working. as I noticed the following thread,

[wizardpen 10.10 problems thread]("http://ubuntuforums.org/showthread.php?t=1524847")

I have a link to how I set them up before - I will find it so that I can see what happens

Thread link to set up drivers ( [Paint Programs]("http://ubuntuforums.org/showthread.php?t=1322647&highlight=paint+program&page=3") - I addded it here - I need this information copying to try again)

```


     Code:
     but once I get the Genius Pen working on here .....

we will be on the right road ......... So how do I do that ?

we need a driver called ...........  wizardpen ......... 0.70 ....... or something .... 

find a link for it there is a Debian package somewhere .... ?       

I followed this once ....... but I never got it to work on the laptop .... 

**************************************************  *********************************

I HAVE NOW THOUGH WICKED ............ this works for a Genius ,,, Pen ... and Tablet ... on 9.10 ....

[http://www.mediafire.com/file/nyzyyn...lpha2_i386.deb]("http://www.mediafire.com/file/nyzyynygiyy/wizardpen_0.7.0-alpha2_i386.deb")

I added the fdi file after this as shown in the readme ...... here ..........

README - CONFIGURATION
======================
Primary author (documentation): Felix Leong (seh_hui at yahoo.com)

This document describes how to configure the Wizardpen driver.

**TODO** Proofreading and formatting polish

CONFIGURING THE DRIVER
----------------------
** RECOMMENDED CONFIGURATION STEPS FOR XORG 7.3 **

To fully exploit HAL-based hotplugging provided in Xorg 7.3, the following
steps should be observed:
    1. Connect your Wizardpen tablet
    2. ** IMPORTANT ** Find out the name of your tablet by executing
        `grep -i name /proc/bus/input/devices`
    3. Create a new file 
gksudo gedit /etc/hal/fdi/policy/99-x11-wizardpen.fdi
    4. Edit the fdi file and paste the following template:
            <?xml version="1.0" encoding="ISO-8859-1" ?>
            <deviceinfo version="0.2">
            <device>
                <!-- This MUST match with the name of your tablet obtained -->
                <!-- in Step 2 specified previously                        -->
                <match key="info.product" contains="NAME OF YOUR TABLET">
                <merge key="input.x11_driver" type="string">wizardpen</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>

                <!-- Modify these configuration accordingly -->
                <!-- See CONFIGURATION OPTIONS section for the full-set of -->
                <!-- configurable options                                  -->
                <merge key="input.x11_options.TopX" type="string">5619</merge>
                <merge key="input.x11_options.TopY" type="string">6554</merge>
                <merge key="input.x11_options.BottomX" type="string">29405</merge>
                <merge key="input.x11_options.BottomY" type="string">29671</merge>
                <merge key="input.x11_options.MaxX" type="string">29405</merge>
                <merge key="input.x11_options.MaxY" type="string">29671</merge>
                </match>
            </device>
            </deviceinfo> 


    5. Restart your computer


__________________________________________________  ____________________

This works just fine .......... love it ......... UBUNTU 9.10 ROCKS now ....... :wink: 
I will install and try it out ....... (now I have found how to do it again.)
UC-LOGIC Tablet WP5540U


```[B]

(The above was all that I previously had to do to get it working ok in 9.10)

CONFIRMED ...... THIS NO LONGER APPEARS to WORK ...... in 10.10

The pointer jumps straight to the left top corner of the screen and sits there,
[COLOR=Red]
[/COLOR][/B]

---

### Post by Noccy on 2010-08-01
> **23dornot23d said:**
> Just to confirm this  ......
(The above was all that I previously had to do to get it working ok in 9.10)

CONFIRMED ...... THIS NO LONGER APPEARS to WORK ...... in 10.10

Exactly the same problem as I have/had. Setting up the tablet in 10.04 is easy enough, but every single Ubuntu version has its own way to set this up. Files and folders come and go, configuration files are made obsolete while other files take over, internals change etc.

Shouldn't this really go into the base system? Wacom tablets work out of the box, why doesn't this apply to the Wizardpen tablets? Preferably with a little graphical utility to calibrate and troubleshoot it.

---

### Post by ranch hand on 2010-08-01
> **Noccy said:**
> Exactly the same problem as I have/had. Setting up the tablet in 10.04 is easy enough, but every single Ubuntu version has its own way to set this up. Files and folders come and go, configuration files are made obsolete while other files take over, internals change etc.

Shouldn't this really go into the base system? Wacom tablets work out of the box, why doesn't this apply to the Wizardpen tablets? Preferably with a little graphical utility to calibrate and troubleshoot it.
The folks at the Wacom Project supply the stuff for Wacom.  Many other tablets can use some of it too.

Some group would have to do the same for WizardPen products.  Big job I suspect.

---

### Post by Noccy on 2010-08-01
> **ranch hand said:**
> Some group would have to do the same for WizardPen products.  Big job I suspect.

I wouldn't mind helping out, but right now it's kinda hard since the internals change all the time. 

Would anybody be interested in creating a Google Group to act as some sort of a "unofficial tablet coordination group"? If we could just gather enough people with deep system knowledge to figure out what has to be done, as well as a few developers to write a "TabletSetup" utility that would help with calibration and tweaking the specific options. 

As for development I could help out with some C++ code, although I've got zero skills in GTK/QT development at this time. However, a well designed console tool could probably do the same job for starters.

Also, providing the TabletSetup utility through doctormo's ppa could be beneficial, and would minimize the setup instructions to "Run tabletsetup and follow the instructions".

---

### Post by Favux on 2010-08-01
Hi,

I understand you're eager but it seems to me you should give DoctorMO a little time.  He usually has the driver updated and working a month or two before the new release:  [https://launchpad.net/~doctormo/+archive/xorg-wizardpen](https://launchpad.net/~doctormo/+archive/xorg-wizardpen)

I'm sure he'd welcome anyone who could help him with the coding.  You could also join his testers site and help give him constructive feed back:  [https://launchpad.net/~wizardpen-testers](https://launchpad.net/~wizardpen-testers)  You'll see his latest test drivers are from 6-9-10 for Karmic and Lucid.

---

### Post by Noccy on 2010-08-01
> **Favux said:**
> 
I understand you're eager but it seems to me you should give DoctorMO a little time.  He usually has the driver updated and working a month or two before the new release

Thanks for the tip :) Since I needed the tablet support working I had to downgrade all my boxes back to 10.04 again a little while ago, but with the wizardpen-testers ppa an upgrade might be worth it on at least one of the systems.

The only thing the wizardpen drivers lack now tho is the userland tools for all things tablet, and that's where I think a community effort could possibly do good :)

---

### Post by DoctorMO on 2010-08-14
Noccy, what the wizardpen driver lacks is a push to get it into debian and then synced into ubuntu maverik.

If your interested, the reason why wacom is well supported and wizardpen is not is because people who own wizardpen hardware are poor and usually in the commodity market. People who have wacoms are businesses, professionals and the middle class.

Economics can be a bit of a SOB. Even I have a wacom.

---

### Post by 23dornot23d on 2010-08-15
Here is a link to all the information I manage to find on the [Wizardpen]("https://sites.google.com/site/problems7730zg/home/wizardpen-0-7-3") ....

We will get it going for Maverick ...... at some stage in the game .....

But at the moment how its meant to communicate and give me feed back eludes me.

We really need a test screen ..... like they used to have for joysticks and the likes .....


To see what works and what does not ......

buttons - screen size - sensitivity - orientation  ............ etc .....

does anybody know if this already exists in any shape or form ?

_____________________________________________________________________________________

(I am pretty sure that's right too [COLOR=Red]42[/COLOR] is not the answer to the universe but most definitely a error code )

---

### Post by techno-mole on 2010-08-23
> **DoctorMO said:**
> 

If your interested, the reason why wacom is well supported and wizardpen is not is because people who own wizardpen hardware are poor.

I have to disagree, I got my tablet because I'm tight and didn't see the point of getting a tablet that costs twice as much and does more or less the same thing :lolflag:

---

### Post by techno-mole on 2010-08-23
> **23dornot23d said:**
> 

We really need a test screen ..... like they used to have for joysticks and the likes .....


To see what works and what does not ......

buttons - screen size - sensitivity - orientation  ............ etc .

I gui for calibration would be a useful feature, I know very little about coding these types of things, but something like the js test application thats in the repo's would do the job.

Again not that I know much about these things, but I'm guessing the current issue with maverick and the driver isn't a mega problem, by that I mean it's not going to take a complete re-write of the driver ? because it works, that is the tablet does something when you try to use it, just not quite the right thing ;)

---

### Post by Favux on 2010-08-23
You should be able to use the xinput calibrator to get calibration anyway.  I don't know if the ppa works in Maverick yet:  [http://www.freedesktop.org/wiki/Software/xinput_calibrator](http://www.freedesktop.org/wiki/Software/xinput_calibrator)

---

### Post by techno-mole on 2010-08-23
I don't think that's going to work, for me anyway.

I will install it and see what happens, but as the cursor moves to the top left for me, that's as far as I'm going to get with calibration, I can't get the cursor to do any other movements.

I might have a go and see what happens on my wife's system, she's running mint isadora, I know the tablet works on that, so the calibration tool should as well.

---

### Post by ranch hand on 2010-08-23
While you are checking that out you might take a look and see why the tablet works there.  They must install something more than Ubuntu does.

Might be able to install that on Ubuntu.  I am sure hunting down the depends might be FUN.

---

### Post by techno-mole on 2010-08-23
The tablet and calibration tool will work on mint isadora because it's basically ubuntu lucid with some tweaks, you can install the wizardpen driver from the doctormo ppa and then configure the 70-wizardpen.conf to suit your needs, 
I'm thinking that when the next version of mint comes out then this problem will exist in that too, seeing as it will essentially be a tweaked version of maverick, unless of course the driver is working before the next version of mint is released.

I think that the driver should have been included by now, but I don't control these things, although having said that I can see why if it has to be re-worked for every release.

The example is in the thread I started last year for installing the driver in karmic I think it was, and other threads by other people, as well as the wiki the difference in installation instructions from release to release is quite a bit different in some cases.

The most hassle I had setting it up on lucid was to add the repo, reload synaptic, install driver, then edit the conf file and restart system, used to take about 5 minutes tops to get the tablet in a workable and more importantly usable state, eg - I could edit my photographs and draw with it, in lucid it ran smoother than previous releases, at least I think it did.

---

### Post by ranch hand on 2010-08-23
If what is missing in 10.10 is the driver then I would say that you are probably out of luck for about another month.

There is little sense in developing a driver for a moving target.  Most drivers for specific devices will be out in time for the release.  Probably between the beta (coming up fast) and the RC.

---

### Post by techno-mole on 2010-08-24
I'm just impatient I guess.

I get a bee in my bonnet about the little people (like me) the ones who don't use wacom tablets (for what ever reason) and other better known makes of peripherals.

Personally I think that if it wasn't for the likes of people like doctormo and the rest of the wizardpen team, and other teams that are doing the same sort of thing then I get the distinct impression that support for a lot of devices and such like would be forgotten in favour of better known devices, eg - wacom v's other tablets.

There's something about a situation like that I find very distasteful, but that's just me.
I'm not a total idiot, I know it is pretty much impossible to support every bit of kit out there, even for companies like apple and microsoft who have large wallets, but even so. 

Here's an example, I recently upgraded my windows drive from xp to windows 7, I was surprised at the amount of stuff I had trouble finding drivers for, the sound card I had wasn't supported, I had an old sb audigy card which was meant to work with 7 but didn't (although I think it was because I use 64bit) in the end I tried an old sound card from the loft, and it worked, it's an old via card (I think it's the oldest I have)

It took some time to get my tablet to work in windows 7 as well, just for the record :-)

---

### Post by techno-mole on 2010-08-24
I have another question regarding maverick and the wizardpen driver.

Although gnome shell isn't the default window manager type thing as yet (release was put back I think until september ?) I have noticed when I've been experimenting with it (gnome shell) that my graphics tablet behaves a little strangely.

It basically has a delay, when using it I can draw a line, and the cursor on screen will respond a second later, this makes it a little difficult to use effectively, so I'm wondering what may be the cause of it, and whether it will be a problem when gnome 3 and gnome shell get made the default ?

---

### Post by Favux on 2010-08-24
Hi techno-mole,

I'm going to reason by analogy from a known gtk/gimp bug with Wacom.

If mutter (that's the compositing manager for Gnome 3, correct?) and whatever app. are showing a lag it could be the stylus is generating so many events it's bogging down the CPU.  With Wacom you can partially alleviate this by increasing the RawSample (sampling rate) parameter.

---

### Post by techno-mole on 2010-08-24
That's most likely the issue then, I figured it was something to do with the compositing manager, mainly because with out gnome shell running the issue didn't occur, but it's something to think about.

I am still not sure whether I will run gnome shell when it gets made the default, I might see how it runs, but most likely I will end up going back to my normal set up, which is compiz and awn, the tablet works fine with compiz and awn.

Is it possible to do something similar with other tablets, and the wizardpen driver ?

---

### Post by Favux on 2010-08-24
Hi techno-mole,

> Is it possible to do something similar with other tablets, and the wizardpen driver ? 
I don't know.  We'd have to look at 'man wizarpen' or possibly 'man xinput' and see if there's something.

Just to be clear, increasing the RawSample parameter decreases the sampling rate, which is what we'd be looking for.

---

### Post by techno-mole on 2010-08-24
Maybe this could be something that could be incorporated into a gui for calibration and configuring the wizardpen driver.

Or if not a gui then an option in a config file somewhere ?

Does this have an adverse affect on the way the tablet behaves, decreasing the sampling rate ?

---

### Post by Favux on 2010-08-24
> Or if not a gui then an option in a config file somewhere ?
That's what you'd be looking at 'man wizardpen' or possibly 'man xinput' for.  To see if an option is already available.
> Does this have an adverse affect on the way the tablet behaves, decreasing the sampling rate ? 
If you decrease it too far the stylus gets jittery and isn't very useful.

---

### Post by 23dornot23d on 2010-08-26
> **Favux said:**
> You should be able to use the xinput calibrator to get calibration anyway.  I don't know if the ppa works in Maverick yet:  [http://www.freedesktop.org/wiki/Software/xinput_calibrator](http://www.freedesktop.org/wiki/Software/xinput_calibrator)


Two definate plus's here ..... the calibrator works with the wizardpen and it works in Mint 9
( I am happy now .... ;) )

Next Test with Maverick ......


```

checking for X... libraries , headers 
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking for working strtod... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for XINPUT... configure: error: Package requirements (x11 xext xi >= 1.2 inputproto >= 1.5) were not met:

No package 'xi' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XINPUT_CFLAGS
and XINPUT_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


```Not compiling here in maverick .....

xi is missing .... how do I get it ?

(Too many files with xi  in to choose from ?)

It never complained in Mint 9 ........ !!!

ok added **libxi-dev**
and [COLOR=Blue][B]now compiles ok
[/B][/COLOR] 
runs but the pen does not move

root@keith-laptop:/home/keith# xinput_calibrator
Calibrating EVDEV driver for "UC-LOGIC Tablet WP5540U" id=14
    current calibration values (from XInput): min_x=0, max_x=11000 and min_y=0, max_y=8000
root@keith-laptop:/home/keith# uname -r
2.6.35-14-generic
root@keith-laptop:/home/keith#



The Wizardpen drivers do not show up in synaptic ... with these as sources ..... "maverick" 
deb [http://ppa.launchpad.net/doctormo/xorg-wizardpen/ubuntu](http://ppa.launchpad.net/doctormo/xorg-wizardpen/ubuntu) maverick main [FONT=monospace]
[/FONT]deb-src [http://ppa.launchpad.net/doctormo/xorg-wizardpen/ubuntu](http://ppa.launchpad.net/doctormo/xorg-wizardpen/ubuntu) maverick main 


Only using "Lucid" ..... picks up the latest wizardpen drivers ....... 0.7.3 ..... same result though cursor shoots to top left.

---

### Post by techno-mole on 2010-08-27
I haven't had a problem compiling the driver on maverick, it just doesn't want to play once it's installed, cursor goes to the top left and that's all it does.

Runs fine in isadora though (mint 9)

---

### Post by techno-mole on 2010-08-28
I've just seen this on ubuntu geek.

It's a gui for configuring wacom tablets for ubuntu 10.4 something like this would be ideal for easy configuration of any tablet.

[http://www.ubuntugeek.com/wacom-control-panel-easily-configure-wacom-tablet.html]("http://www.ubuntugeek.com/wacom-control-panel-easily-configure-wacom-tablet.html")

---

### Post by 23dornot23d on 2010-08-28
That looks interesting - 

I have just installed it ... its a shame it does not pick up other pens .......

but its a step in the right direction ..... 

I will advise this to other users ..... thanks ,

---

### Post by techno-mole on 2010-08-30
I've been trying to figure out what might be causing the tablet to behave the way it is, not sure I have a clue what's going on.

I thought it might be an idea to set the tablet up on my wife's system, she's running mint isadora, and I know the tablet works on that (I was running it until recently) so I added the drmo ppa and installed the driver, restarted the system and the tablet works great.

I knew this was going to happen, so next I thought I'd compare the logs from my system and my wife's, maverick is using an up to date version of xorg (maverick - X.Org X Server 1.9.0 ) and mint 9 uses the older version (mint 9 - X.Org X Server 1.7.6 ) I don't know much about these things, but I assume that each version is pretty much the same in what they do ?


I then went through the xorg.0.log's from each machine, and working on what I said above I was sort of expecting some similarities between the 2 logs regarding the wizardpen driver, but it seems they are quite a bit different.

This is the section of xorg.0.log from my wife's system that mentions the tablet and wizardpen driver.

```
(II) config/udev: Adding input device UC-LOGIC Tablet WP8060U (/dev/input/event5)
(**) UC-LOGIC Tablet WP8060U: Applying InputClass "evdev pointer catchall"
(**) UC-LOGIC Tablet WP8060U: Applying InputClass "evdev tablet catchall"
(**) UC-LOGIC Tablet WP8060U: Applying InputClass "wizardpen"
(II) LoadModule: "wizardpen"
(II) Loading /usr/lib/xorg/modules/input/wizardpen_drv.so
(II) Module wizardpen: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.7.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Option "Device" "/dev/input/event5"
(--) UC-LOGIC Tablet WP8060U: MaxX:32767 MaxY:32767 MaxZ:1023
(--) UC-LOGIC Tablet WP8060U: aspect ratio:1.33:1
(**) UC-LOGIC Tablet WP8060U is in absolute mode
(**) UC-LOGIC Tablet WP8060U: TopX not set, defaulting to "5%"
(**) UC-LOGIC Tablet WP8060U: TopY not set, defaulting to "5%"
(**) UC-LOGIC Tablet WP8060U: BottomX not set, defaulting to "95%"
(**) UC-LOGIC Tablet WP8060U: BottomY not set, defaulting to "95%"
(II) UC-LOGIC Tablet WP8060U: ScreenX = 1360, ScreenY = 768
(**) UC-LOGIC Tablet WP8060U: TopX                   = 1638
(**) UC-LOGIC Tablet WP8060U: TopY                   = 1638
(**) UC-LOGIC Tablet WP8060U: BottomX                = 31128
(**) UC-LOGIC Tablet WP8060U: BottomY                = 31128
(**) UC-LOGIC Tablet WP8060U: TopZ    (min pressure) = 0
(**) UC-LOGIC Tablet WP8060U: BottomZ (max pressure) = 1023
(**) UC-LOGIC Tablet WP8060U: always reports core events
(II) XINPUT: Adding extended input device "UC-LOGIC Tablet WP8060U" (type: WizardPen Tablet)
(II) UC-LOGIC Tablet WP8060U Increment: 24
(II) config/udev: Adding input device UC-LOGIC Tablet WP8060U (/dev/input/mouse2)
(**) UC-LOGIC Tablet WP8060U: Applying InputClass "wizardpen ignore mouse dev"
```

And below is the section of xorg.0.log from my system, with the driver installed from the drmo ppa (I know the latest version in the ppa is for lucid)

```
[    26.242] (II) config/udev: Adding input device UC-LOGIC Tablet WP8060U (/dev/input/event6)
[    26.242] (**) UC-LOGIC Tablet WP8060U: Applying InputClass "evdev pointer catchall"
[    26.242] (**) UC-LOGIC Tablet WP8060U: Applying InputClass "evdev tablet catchall"
[    26.242] (**) UC-LOGIC Tablet WP8060U: always reports core events
[    26.242] (**) UC-LOGIC Tablet WP8060U: Device: "/dev/input/event6"
[    26.280] (II) UC-LOGIC Tablet WP8060U: Found 10 mouse buttons
[    26.280] (II) UC-LOGIC Tablet WP8060U: Found scroll wheel(s)
[    26.280] (II) UC-LOGIC Tablet WP8060U: Found relative axes
[    26.280] (II) UC-LOGIC Tablet WP8060U: Found x and y relative axes
[    26.280] (II) UC-LOGIC Tablet WP8060U: Found absolute axes
[    26.280] (II) UC-LOGIC Tablet WP8060U: Found x and y absolute axes
[    26.280] (II) UC-LOGIC Tablet WP8060U: Found absolute tablet.
[    26.280] (II) UC-LOGIC Tablet WP8060U: Configuring as tablet
[    26.280] (**) UC-LOGIC Tablet WP8060U: YAxisMapping: buttons 4 and 5
[    26.280] (**) UC-LOGIC Tablet WP8060U: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    26.280] (II) XINPUT: Adding extended input device "UC-LOGIC Tablet WP8060U" (type: TABLET)
[    26.280] (WW) UC-LOGIC Tablet WP8060U: touchpads, tablets and touchscreens ignore relative axes.
[    26.280] (II) UC-LOGIC Tablet WP8060U: initialized for absolute axes.
[    26.280] (II) config/udev: Adding input device UC-LOGIC Tablet WP8060U (/dev/input/mouse2)
```


As you can see they are quite a bit different, which is to be expected I guess, seeing as one is from mint 9 (which is basically lucid) and the other is from maverick, and also taking into consideration that the driver isn't meant for maverick.

Anyway, this is more me trying to figure out how the tablet works, how the system sees it and loads modules and does what's needed to run the thing, I'm not pretending to understand it, but I am trying to learn what it all means in a bid to understand it.

cheers.

---

### Post by Favux on 2010-08-30
The wizarpen driver is not working at all in Maverick, otherwise after:
```
**) UC-LOGIC Tablet WP8060U: Applying InputClass "evdev tablet catchall"
```
you would see:
```
(**) UC-LOGIC Tablet WP8060U: Applying InputClass "wizardpen"

```
like you do in Mint.  So it is the evdev driver that has your tablet.  It's possible you could improve function by adding:
```
Option "Ignore" "yes"
```
with the appropriate match lines to the "evdev tablet catchall" snippet in evdev.conf so that:
```
(II) config/udev: Adding input device UC-LOGIC Tablet WP8060U (/dev/input/mouse2)
```
is ignored like the wizardpen.conf does.

---

### Post by techno-mole on 2010-08-30
I've been looking at this file - /usr/share/X11/xorg.conf.d/10-evdev.conf

In particular this section - 

```
Section "InputClass"
        Identifier "evdev tablet catchall"
        MatchIsTablet "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection
```

Is this where I should add the ```
Option "Ignore" "yes"
``` I tried it anyway, it stops the cursor moving to the top left, in fact it stops the cursor moving at all, at least when trying to use the tablet.

Also does it make a difference that on my system (running maverick) that evdev.conf is in usr/share/X11/xorg.conf.d/ and on my wife's system that file is named 05-evdev.conf and is located in usr/lib/X11/xorg.conf.d/ ?

---

### Post by Favux on 2010-08-30
I think it would look something like:
```
Section "InputClass"
        Identifier "evdev tablet catchall"
        MatchIsTablet "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
	MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
	MatchDevicePath "/dev/input/mouse*"
	Option "Ignore" "yes"
EndSection
```
As far as the directories it looks like they changed the location in Maverick.

---

### Post by techno-mole on 2010-08-30
well I tried it, and some other messing around and the best I can do is no better than what I already have, that being the cursor moving to the top left.

I can't seem to get it to do anything else.

---

### Post by Favux on 2010-08-30
That's a little surprising.  Usually the evdev driver will give you some minimal kind of functionality.  Oh well.

---

### Post by techno-mole on 2010-08-30
Wouldn't the fact that where files get put in lucid is different to maverick cause issues ? 

The driver is built to put files where they are needed, and if the locations change does the driver still put the files in the original places ?

Perhaps it wasn't such a good idea to try and get a driver that's for lucid to work on maverick, but I don't know what has changed ?

Maybe it's something with the newer version of xorg ?

(Clutching at straws :D )

---

### Post by Favux on 2010-08-30
> Maybe it's something with the newer version of xorg ?
Most likely.  For example to get the wacom driver working nebosuke changed usb_buffer_alloc to usb_alloc_coherent and usb_buffer_free to usb_free_coherent respectively in the wacom_sys.c file before compiling.  See:  [http://ubuntuforums.org/showpost.php?p=9436635&postcount=5](http://ubuntuforums.org/showpost.php?p=9436635&postcount=5)

---

### Post by techno-mole on 2010-08-30
I am even more puzzled, I started to wonder if downgrading xorg to the lucid version might yield some results, so I had a look in synaptic to see what version it is, and this is why I'm puzzled.

Synaptic lists xorg as version - 1:7.5+6ubuntu3

However looking in my xorg.0.log it says at the top that xorg is version - 1.9.0


Or am I missing something here ? after some thinking about it I've decided not to try downgrading, I may think about going back to lucid until the driver is working for maverick.

---

### Post by 23dornot23d on 2010-08-30
> **techno-mole said:**
> I've been trying to figure out what might be causing the tablet to behave the way it is, not sure I have a clue what's going on.

I thought it might be an idea to set the tablet up on my wife's system, she's running mint isadora, and I know the tablet works on that (I was running it until recently) so I added the drmo ppa and installed the driver, restarted the system and the tablet works great.

I knew this was going to happen, so next I thought I'd compare the logs from my system and my wife's, maverick is using an up to date version of xorg (maverick - X.Org X Server 1.9.0 ) and mint 9 uses the older version (mint 9 - X.Org X Server 1.7.6 ) I don't know much about these things, but I assume that each version is pretty much the same in what they do ?


I then went through the xorg.0.log's from each machine, and working on what I said above I was sort of expecting some similarities between the 2 logs regarding the wizardpen driver, but it seems they are quite a bit different.

This is the section of xorg.0.log from my wife's system that mentions the tablet and wizardpen driver.

```
(II) config/udev: Adding input device UC-LOGIC Tablet WP8060U (/dev/input/event5)
(**) UC-LOGIC Tablet WP8060U: Applying InputClass "evdev pointer catchall"
(**) UC-LOGIC Tablet WP8060U: Applying InputClass "evdev tablet catchall"
(**) UC-LOGIC Tablet WP8060U: Applying InputClass "wizardpen"
(II) LoadModule: "wizardpen"
(II) Loading /usr/lib/xorg/modules/input/wizardpen_drv.so
(II) Module wizardpen: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.7.3
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Option "Device" "/dev/input/event5"
(--) UC-LOGIC Tablet WP8060U: MaxX:32767 MaxY:32767 MaxZ:1023
(--) UC-LOGIC Tablet WP8060U: aspect ratio:1.33:1
(**) UC-LOGIC Tablet WP8060U is in absolute mode
(**) UC-LOGIC Tablet WP8060U: TopX not set, defaulting to "5%"
(**) UC-LOGIC Tablet WP8060U: TopY not set, defaulting to "5%"
(**) UC-LOGIC Tablet WP8060U: BottomX not set, defaulting to "95%"
(**) UC-LOGIC Tablet WP8060U: BottomY not set, defaulting to "95%"
(II) UC-LOGIC Tablet WP8060U: ScreenX = 1360, ScreenY = 768
(**) UC-LOGIC Tablet WP8060U: TopX                   = 1638
(**) UC-LOGIC Tablet WP8060U: TopY                   = 1638
(**) UC-LOGIC Tablet WP8060U: BottomX                = 31128
(**) UC-LOGIC Tablet WP8060U: BottomY                = 31128
(**) UC-LOGIC Tablet WP8060U: TopZ    (min pressure) = 0
(**) UC-LOGIC Tablet WP8060U: BottomZ (max pressure) = 1023
(**) UC-LOGIC Tablet WP8060U: always reports core events
(II) XINPUT: Adding extended input device "UC-LOGIC Tablet WP8060U" (type: WizardPen Tablet)
(II) UC-LOGIC Tablet WP8060U Increment: 24
(II) config/udev: Adding input device UC-LOGIC Tablet WP8060U (/dev/input/mouse2)
(**) UC-LOGIC Tablet WP8060U: Applying InputClass "wizardpen ignore mouse dev"
```And below is the section of xorg.0.log from my system, with the driver installed from the drmo ppa (I know the latest version in the ppa is for lucid)

```
[    26.242] (II) config/udev: Adding input device UC-LOGIC Tablet WP8060U (/dev/input/event6)
[    26.242] (**) UC-LOGIC Tablet WP8060U: Applying InputClass "evdev pointer catchall"
[    26.242] (**) UC-LOGIC Tablet WP8060U: Applying InputClass "evdev tablet catchall"
[    26.242] (**) UC-LOGIC Tablet WP8060U: always reports core events
[    26.242] (**) UC-LOGIC Tablet WP8060U: Device: "/dev/input/event6"
[    26.280] (II) UC-LOGIC Tablet WP8060U: Found 10 mouse buttons
[    26.280] (II) UC-LOGIC Tablet WP8060U: Found scroll wheel(s)
[    26.280] (II) UC-LOGIC Tablet WP8060U: Found relative axes
[    26.280] (II) UC-LOGIC Tablet WP8060U: Found x and y relative axes
[    26.280] (II) UC-LOGIC Tablet WP8060U: Found absolute axes
[    26.280] (II) UC-LOGIC Tablet WP8060U: Found x and y absolute axes
[    26.280] (II) UC-LOGIC Tablet WP8060U: Found absolute tablet.
[    26.280] (II) UC-LOGIC Tablet WP8060U: Configuring as tablet
[    26.280] (**) UC-LOGIC Tablet WP8060U: YAxisMapping: buttons 4 and 5
[    26.280] (**) UC-LOGIC Tablet WP8060U: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    26.280] (II) XINPUT: Adding extended input device "UC-LOGIC Tablet WP8060U" (type: TABLET)
[    26.280] (WW) UC-LOGIC Tablet WP8060U: touchpads, tablets and touchscreens ignore relative axes.
[    26.280] (II) UC-LOGIC Tablet WP8060U: initialized for absolute axes.
[    26.280] (II) config/udev: Adding input device UC-LOGIC Tablet WP8060U (/dev/input/mouse2)
```As you can see they are quite a bit different, which is to be expected I guess, seeing as one is from mint 9 (which is basically lucid) and the other is from maverick, and also taking into consideration that the driver isn't meant for maverick.

Anyway, this is more me trying to figure out how the tablet works, how the system sees it and loads modules and does what's needed to run the thing, I'm not pretending to understand it, but I am trying to learn what it all means in a bid to understand it.

cheers.


Seems like a good place to start - so I have done the same ....... this is my output
First for Mint which works fine ... 

```

(II) config/udev: Adding input device UC-LOGIC Tablet WP5540U (/dev/input/event10)
(**) UC-LOGIC Tablet WP5540U: Applying InputClass "evdev pointer catchall"
(**) UC-LOGIC Tablet WP5540U: Applying InputClass "evdev tablet catchall"
(**) UC-LOGIC Tablet WP5540U: Applying InputClass "wizardpen"
(II) LoadModule: "wizardpen"
(II) Loading /usr/lib/xorg/modules/input/wizardpen_drv.so
(II) Module wizardpen: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.7.3
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Option "Device" "/dev/input/event10"
(--) UC-LOGIC Tablet WP5540U: MaxX:32767 MaxY:32767 MaxZ:1023
(--) UC-LOGIC Tablet WP5540U: aspect ratio:1.38:1
(**) UC-LOGIC Tablet WP5540U is in absolute mode
(**) UC-LOGIC Tablet WP5540U: TopX not set, defaulting to "5%"
(**) UC-LOGIC Tablet WP5540U: TopY not set, defaulting to "5%"
(**) UC-LOGIC Tablet WP5540U: BottomX not set, defaulting to "95%"
(**) UC-LOGIC Tablet WP5540U: BottomY not set, defaulting to "95%"
(II) UC-LOGIC Tablet WP5540U: ScreenX = 1440, ScreenY = 900
(**) UC-LOGIC Tablet WP5540U: TopX                   = 1638
(**) UC-LOGIC Tablet WP5540U: TopY                   = 1638
(**) UC-LOGIC Tablet WP5540U: BottomX                = 31128
(**) UC-LOGIC Tablet WP5540U: BottomY                = 31128
(**) UC-LOGIC Tablet WP5540U: TopZ    (min pressure) = 0
(**) UC-LOGIC Tablet WP5540U: BottomZ (max pressure) = 1023
(**) UC-LOGIC Tablet WP5540U: always reports core events
(II) XINPUT: Adding extended input device "UC-LOGIC Tablet WP5540U" (type: WizardPen Tablet)
(II) UC-LOGIC Tablet WP5540U Increment: 22
(II) config/udev: Adding input device UC-LOGIC Tablet WP5540U (/dev/input/mouse2)
(**) UC-LOGIC Tablet WP5540U: Applying InputClass "wizardpen ignore mouse dev"

```I will switch to Maverick and see if I get the same results as you have , I expect I will as it does the same thing
and just shoots to the top left of the screen.

```

[    32.184] (II) config/udev: Adding input device UC-LOGIC Tablet WP5540U (/dev/input/event10)
[    32.185] (**) UC-LOGIC Tablet WP5540U: Applying InputClass "evdev pointer catchall"
[    32.185] (**) UC-LOGIC Tablet WP5540U: Applying InputClass "evdev tablet catchall"
[    32.185] (**) UC-LOGIC Tablet WP5540U: always reports core events
[    32.185] (**) UC-LOGIC Tablet WP5540U: Device: "/dev/input/event10"
[    32.200] (II) UC-LOGIC Tablet WP5540U: Found 10 mouse buttons
[    32.200] (II) UC-LOGIC Tablet WP5540U: Found scroll wheel(s)
[    32.200] (II) UC-LOGIC Tablet WP5540U: Found relative axes
[    32.200] (II) UC-LOGIC Tablet WP5540U: Found x and y relative axes
[    32.200] (II) UC-LOGIC Tablet WP5540U: Found absolute axes
[    32.200] (II) UC-LOGIC Tablet WP5540U: Found x and y absolute axes
[    32.200] (II) UC-LOGIC Tablet WP5540U: Found absolute tablet.
[    32.200] (II) UC-LOGIC Tablet WP5540U: Configuring as tablet
[    32.200] (**) UC-LOGIC Tablet WP5540U: YAxisMapping: buttons 4 and 5
[    32.200] (**) UC-LOGIC Tablet WP5540U: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    32.200] (II) XINPUT: Adding extended input device "UC-LOGIC Tablet WP5540U" (type: TABLET)
[    32.200] (WW) UC-LOGIC Tablet WP5540U: touchpads, tablets and touchscreens ignore relative axes.
[    32.200] (II) UC-LOGIC Tablet WP5540U: initialized for absolute axes.
[    32.200] (II) config/udev: Adding input device UC-LOGIC Tablet WP5540U (/dev/input/mouse1)
[    32.200] (II) No input driver/identifier specified (ignoring)

```X.Org X Server 1.8.1.902 (1.8.2 RC 2)
Release Date: 2010-06-21

Just to confirm the situation - similar ends with this line not being actioned :-

(**) UC-LOGIC Tablet WP5540U: Applying InputClass "wizardpen"
(II) LoadModule: "wizardpen"

This did not exist in its directory even though It appeared to load the driver up ok ? ..... 
from the Lucid repository..... 
(although it may have happened after I set the source to Maverick - the driver does not exist there yet)
/usr/lib/xorg/modules/input/wizardpen_drv.so

root@keith-laptop:/usr/lib/xorg/modules/input# ls
evdev_drv.so  mouse_drv.so  synaptics_drv.so  vmmouse_drv.so  wacom_drv.so
root@keith-laptop:/usr/lib/xorg/modules/input#

The drivers are there in Mint ....  though .... 
root@keith-laptop:/usr/lib/xorg/modules/input# ls
evdev_drv.so  synaptics_drv.so  wacom_drv.so      wizardpen_drv.so
mouse_drv.so  vmmouse_drv.so    wizardpen_drv.la
root@keith-laptop:/usr/lib/xorg/modules/input#

So I have made sure that all the drivers are there now and added the rules .... still no luck .....

My best guess is its the evdev_drv.so ....... that seems to have totally changed for touch screen .....
( as I say this is my best guess just looking at the file  "evdev_drv.so" using KATE first in Mint and then in Maverick )

So how do you trace what's happening  ..... and correct it ..... other than not upgrading.
So the touch screen computers ...... which one do I buy that's compatible and working ok ?

I need to buy touch screen now to keep up with Mavericks fast pace ... and dump the wizardpen.
Just a case of cost .... !!! or learn how the evdev driver works !!! just a case of time and education.

evdev_drv.so
Search on it see what you can find out ......

Check the kernel
Aug 31 01:29:15 keith-laptop kernel: [   21.674343] input: UC-LOGIC Tablet WP5540U as /devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2.4/2-2.4:1.0/input/input10
Aug 31 01:29:15 keith-laptop kernel: [   21.674452] generic-usb 0003:5543:0004.0004: input,hidraw3: USB HID v1.00 Mouse [UC-LOGIC Tablet WP5540U] on usb-0000:00:1d.7-2.4/input0


Check how the device is being set up ( it seems to be finding it in Maverick )

```

keith@keith-laptop:~$ egrep "Name|Handlers" /proc/bus/input/devices
N: Name="Lid Switch"
H: Handlers=event0 
N: Name="Power Button"
H: Handlers=kbd event1 
N: Name="Sleep Button"
H: Handlers=kbd event2 
N: Name="Power Button"
H: Handlers=kbd event3 
N: Name="AT Translated Set 2 keyboard"
H: Handlers=sysrq kbd event4 
N: Name="Video Bus"
H: Handlers=kbd event5 
N: Name="HID 04d9:048e"
H: Handlers=mouse0 event6 
N: Name="CHESEN USB Keyboard"
H: Handlers=sysrq kbd event7 
N: Name="CHESEN USB Keyboard"
H: Handlers=kbd event8 
N: Name="Acer Crystal Eye webcam"
H: Handlers=kbd event9 
N: Name="SynPS/2 Synaptics TouchPad"
H: Handlers=mouse2 event11 
[COLOR=Red][B]N: Name="UC-LOGIC Tablet WP5540U"
H: Handlers=mouse1 event10 [/B][/COLOR]
keith@keith-laptop:~$ cat /proc/bus/input/devices 
I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
U: Uniq=
H: Handlers=event0 
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: EV=3
B: KEY=4000 0 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input4
U: Uniq=
H: Handlers=sysrq kbd event4 
B: EV=120013
B: KEY=10000 c0200 0 0 0 0 0 700f 2000003 3803078 f830f401 febfffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/LNXVIDEO:00/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=3
B: KEY=3e000b 0 0 0 0 0 0 0

I: Bus=0003 Vendor=04d9 Product=048e Version=0110
N: Name="HID 04d9:048e"
P: Phys=usb-0000:00:1a.1-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/input/input6
U: Uniq=
H: Handlers=mouse0 event6 
B: EV=17
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=103
B: MSC=10

I: Bus=0003 Vendor=0a81 Product=0101 Version=0110
N: Name="CHESEN USB Keyboard"
P: Phys=usb-0000:00:1d.7-2.1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2.1/2-2.1:1.0/input/input7
U: Uniq=
H: Handlers=sysrq kbd event7 
B: EV=120013
B: KEY=10000 7 ff9f207a c14057ff febeffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=1f

I: Bus=0003 Vendor=0a81 Product=0101 Version=0110
N: Name="CHESEN USB Keyboard"
P: Phys=usb-0000:00:1d.7-2.1/input1
S: Sysfs=/devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2.1/2-2.1:1.1/input/input8
U: Uniq=
H: Handlers=kbd event8 
B: EV=13
B: KEY=2020000 3878 d801d001 1e0000 0 0 0
B: MSC=10

I: Bus=0003 Vendor=064e Product=a103 Version=0100
N: Name="Acer Crystal Eye webcam"
P: Phys=usb-0000:00:1a.7-6/button
S: Sysfs=/devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/input/input9
U: Uniq=
H: Handlers=kbd event9 
B: EV=3
B: KEY=100000 0 0 0 0 0 0

I: Bus=0011 Vendor=0002 Product=0007 Version=81b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio4/input0
S: Sysfs=/devices/platform/i8042/serio4/input/input11
U: Uniq=
H: Handlers=mouse2 event11 
B: EV=b
B: KEY=420 0 3000f 0 0 0 0 0 0 0 0
B: ABS=11000003

[B][COLOR=Red]I: Bus=0003 Vendor=5543 Product=0004 Version=0100
N: Name="UC-LOGIC Tablet WP5540U"
P: Phys=usb-0000:00:1d.7-2.4/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2.4/2-2.4:1.0/input/input12
U: Uniq=
H: Handlers=mouse1 event10 
B: EV=1f
B: KEY=c01 0 3f0001 0 0 0 0 0 0 0 0
B: REL=303
B: ABS=100000f
B: MSC=10[/COLOR][/B]

keith@keith-laptop:~$ 


keith@keith-laptop:~$ hal-device | grep -B 15 input.x11_driver
  linux.device_file = '/dev/sg0'  (string)

53: udi = '/org/freedesktop/Hal/devices/pci_8086_2929_scsi_host_scsi_host'
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host0/scsi_host/host0'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2929_scsi_host'  (string)
  scsi_host.host = 0  (0x0)  (int)
  info.category = 'scsi_host'  (string)
  info.capabilities = { 'scsi_host' } (string list)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2929_scsi_host_scsi_host'  (string)

[B][COLOR=Red]54: udi = '/org/freedesktop/Hal/devices/usb_device_5543_4_noserial_if0_logicaldev_input'
  input.x11_driver = 'wizardpen'  (string)[/COLOR][/B]
keith@keith-laptop:~$ 




```[ArchLinux ]("http://wiki.archlinux.org/index.php/Xorg_Input_Hotplugging")seems the only place I can find much information on the  driver ..... even then its not going to be up to date ..... all I want to do is run it in Maverick and it does not matter about it changing as a USB device - it will always be plugged in the same place - once set up properly.

(I am just going to do a safe-upgrade to the very latest kernel just to see if anything has changed).

---

### Post by techno-mole on 2010-08-31
What kernel are you using ?

According to the system monitor I'm running - 2.6.35-19-generic

I installed the driver as soon as I upgraded to maverick, since then the kernel has had 3 updates (I think) and it's made no difference, I've also seen some updates to evdev as well, and again nothing has changed.

Thinking about it, maybe things have been changed a fair bit to allow for multi touch and such like, not that I'll be buying a multi-touch device any time soon, I'll stick with what I've got, and if it means down grading to lucid then that'll do until the drivers working.

I did start a bug report on launchpad ---> [https://bugs.launchpad.net/wizardpen/+bug/622152]("https://bugs.launchpad.net/wizardpen/+bug/622152")

---

### Post by 23dornot23d on 2010-08-31
I was using -14-generic now I have upgraded it no longer sets my graphics driver up and all the previous versions have stopped working too.

I can still get a console with network support in -19-generic ...... 

 - so I should be able to fix it and hopefully get maverick running again. 
(looks like GDM is failing so swapped to KDM .... now managed to get in - in low graphics mode)

I too had to do this problem so have done as said and added this to the end of etc/X11/xorg.conf
> 
     Code:
     Section "ServerFlags" Option    "IgnoreABI"    "True" EndSection 
added to the bottom of my xorg.conf file.  
What does  this code actually do ...... IgnoreABI ...... looked on Nvidia site and others have used it too ....

ok I seem to be working ok again ... in gdm .... 


but no alteration to how it works with the wizardpen .... still jumps to the top left of the screen.

_____________________________________________________


[B]*My machine is fully up to date now

[/B] I have added to your bug report as this also affects me .....  although mine is a 32 bit machine - it is the same problem - cursor jumps to the top left of the screen.

I would hope the others on here add to it too  .....

[https://bugs.launchpad.net/wizardpen/+bug/622152](https://bugs.launchpad.net/wizardpen/+bug/622152)

---

### Post by 23dornot23d on 2010-10-02
Just noticed these so thought I would post ..... someone has had some success .... 
but I am not sure how to implement the same thing on 32 bit
is there a difference .....  how do I do the same for 32 bit ?

Tried these files and no difference for me ........ the wizardpen_drv.la looks as if that would suit both 32 bit and 64 bit
so do I need to compile the driver for the latest kernel ?

```

# wizardpen_drv.la - a libtool library file
# Generated by ltmain.sh (GNU libtool) 2.2.6b Debian-2.2.6b-2ubuntu1
#
# Please DO NOT delete this file!
# It is necessary for linking the library.

# The name that we can dlopen(3).
dlname='wizardpen_drv.so'

# Names of this library.
library_names='wizardpen_drv.so wizardpen_drv.so wizardpen_drv.so'

# The name of the static archive.
old_library=''

# Linker flags that can not go in dependency_libs.
inherited_linker_flags=''

# Libraries that this one depends upon.
dependency_libs=''

# Names of additional weak libraries provided by this library
weak_library_names=''

# Version information for wizardpen_drv.
current=0
age=0
revision=0

# Is this an already installed library?
installed=yes

# Should we warn about portability when linking against -modules?
shouldnotlink=yes

# Files to dlopen/dlpreopen
dlopen=''
dlpreopen=''

# Directory that this library needs to be installed in:
libdir='/usr/lib/xorg/modules/input'

```**My guess is I need to recompile it too for my machine  ..... how do I go about doing this ?**



[Olaf Piesche]("https://launchpad.net/%7Eopiesche")             wrote             1 hour ago:                                                             [ #7]("https://bugs.launchpad.net/wizardpen/+bug/622152/comments/7")                                            
[LIST]
[*]         [Wizardpen drivers compiled for X 1.9 / Ubuntu Maverick]("https://bugs.launchpad.net/wizardpen/+bug/622152/+attachment/1665506/+files/wizardpen-0.7.3-x1.9-maverick-amd64.tar.gz")         (33.1 KiB,         application/x-tar)
[/LIST]
            I've had  problems using the wizardpen  driver with Maverick until i found a warning about a mismatched ABI in  xorg.0.log. So, I downloaded the 0.7.3 source and compiled it myself.  Other than that, I'm using the default setup (with 70-wizardpen.conf in  /usr/lib/X11/xorg.conf.d), and it works perfectly well, as it did in Lucid with the driver from doctormo's PPA.
 I've attached the recompiled driver files here, built for amd64. If anyone would like to try, simply rename your old /usr/lib/xorg/modules/input/wizardpen_drv.* to turn them off and copy the ones in this tgz into the same directory.
Disclaimer: this has not been tested anywhere except on my machine. It's  using doctormo's sources vanilla without any modifications.

        
                                                                                                                                    [Olaf Piesche]("https://launchpad.net/%7Eopiesche")             wrote             1 hour ago:                                                             [ #8]("https://bugs.launchpad.net/wizardpen/+bug/622152/comments/8")                                   
                     Some more info: If the driver can't be loaded, the evdev catchall specified in /usr/share/X11/xorg.conf.d/10-evdev.conf  kicks in, and the tablet is run with the evdev driver. From there, I  could move the pointer with the tablet, but no pressure was recognized,  and after moving the cursor with the tablet, mouse clicks wouldn't be  recognized anymore.  The driver above can be loaded by Maverick's Xorg,  so all is good now :)
 Grep xorg.0.log for 'EE' (without the quotes) to see if you have the  same problem. If you do, and you're running amd64, there's a good chance  the drivers attached above will fix the issue until an official fix is  released or the drivers in the PPA are updated.

cd /var/log
grep EE  Xorg.0.log

```

[    45.518] (II) config/udev: Adding input device UC-LOGIC Tablet WP5540U (/dev/input/event6)
[    45.518] (**) UC-LOGIC Tablet WP5540U: Applying InputClass "evdev pointer catchall"
[    45.518] (**) UC-LOGIC Tablet WP5540U: Applying InputClass "evdev tablet catchall"
[    45.518] (**) UC-LOGIC Tablet WP5540U: always reports core events
[    45.518] (**) UC-LOGIC Tablet WP5540U: Device: "/dev/input/event6"
[    45.524] (II) UC-LOGIC Tablet WP5540U: Found 10 mouse buttons
[    45.524] (II) UC-LOGIC Tablet WP5540U: Found scroll wheel(s)
[    45.524] (II) UC-LOGIC Tablet WP5540U: Found relative axes
[    45.524] (II) UC-LOGIC Tablet WP5540U: Found x and y relative axes
[    45.524] (II) UC-LOGIC Tablet WP5540U: Found absolute axes
[    45.524] (II) evdev-grail: failed to open grail, no gesture support
[    45.524] (II) UC-LOGIC Tablet WP5540U: Found x and y absolute axes
[    45.524] (II) UC-LOGIC Tablet WP5540U: Found absolute tablet.
[    45.524] (II) UC-LOGIC Tablet WP5540U: Configuring as tablet
[    45.524] (**) UC-LOGIC Tablet WP5540U: YAxisMapping: buttons 4 and 5
[    45.524] (**) UC-LOGIC Tablet WP5540U: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    45.524] (II) XINPUT: Adding extended input device "UC-LOGIC Tablet WP5540U" (type: TABLET)
[    45.524] (WW) UC-LOGIC Tablet WP5540U: touchpads, tablets and touchscreens ignore relative axes.
[    45.524] (II) UC-LOGIC Tablet WP5540U: initialized for absolute axes.
[    45.524] (II) config/udev: Adding input device UC-LOGIC Tablet WP5540U (/dev/input/mouse0)
[    45.524] (II) No input driver/identifier specified (ignoring)
[    45.525] (II) config/udev: Adding input device HID 04d9:048e (/dev/input/event7)
[    45.525] (**) HID 04d9:048e: Applying InputClass "evdev pointer catchall"
[    45.525] (**) HID 04d9:048e: always reports core events
[    45.525] (**) HID 04d9:048e: Device: "/dev/input/event7"

```Still not working for me in Maverick

keith@keith-laptop:~$ uname -a
Linux keith-laptop 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686 GNU/Linux


But maybe I need some more information on how to set this up for 32 bit ..... unless someone can help me out here.

---

### Post by techno-mole on 2010-10-02
I've tried this on ubuntu 10.10 64bit but it doesn't work for me, although I tried it using the driver from the dr mo ppa, haven't tried compiling from source as I'm not sure where to get the source files, there is a how to on the wizardpen page on launchpad, but it doesn't work for me.

Update ---> I thought I would try an compile the driver from the files I found on launchpad (xorg-input-wizardpen-0.8.0.tar.gz) how ever I can't compile it because it keep moaning about man pages, though if I'm honest I'm not entirely sure I'm doing it right :-) so if anyone has some tips I would appreciate it.

Cheers.

---

### Post by 23dornot23d on 2010-10-02
I just tried this too .... Techno-mole the link that you posted says to use bzr .....

although 

I installed bzr ...... it needs some link to my launchpad account ....

and I am not sure how to create this link .... so maybe it is just for developers ....

[Link bzr]("https://answers.launchpad.net/wizardpen/+faq/1021")

```

bzr branch [lp:wizardpen]("https://answers.launchpad.net/+branch/wizardpen")
cd wizardpen
bzr branch [lp:~doctormo/wizardpen/debian-packing]("https://answers.launchpad.net/+branch/%7Edoctormo/wizardpen/debian-packing") debian
./autogen.sh
dpkg-buildpackage -rfakeroot
sudo dpkg -i ../xserver-xorg-input-wizardpen*.deb


```I would love to have it running in Maverick ..... at the moment I switch to Mint to use the Pen ...... which is ok ..... 

but there are instances where I would have liked to have worked with it in Maverick.

here are the errors I get trying to use the information on that page .....


```

root@keith-laptop:/home/keith# bzr branch lp:~doctormo/wizardpen/debian-packing debian
You have not informed bzr of your Launchpad ID, and you must do this to
write to Launchpad or access private data.  See "bzr help launchpad-login".
bzr: ERROR: Invalid url supplied to transport: "bzr+ssh://bazaar.launchpad.net/~doctormo/wizardpen/debian-packing": no supported schemes


```[B]I guess that its still a work in progress and may not be ready to download yet ......

I think I will wait until it is available for general use ....
[/B]

---

### Post by techno-mole on 2010-10-03
That method is out dated I think, I get the same error when trying to run it, I think it's because there is no branch with the name ---> doctormo/wizardpen/debian-packing there was when I tested it on lucid, but then they changed it so it could be installed from dr mo's ppa. (I think)
I did download the tgz archive from the wizardpen launchpad page, but I couldn't get that to compile either, so now I'm stuck with maverick, which for the most part works well, and if I need to use the tablet I log into windows 7.
The funny thing is that the tablet won't work properly in gimp on windows, or my paint for that matter.
Never mind I dare say it'll get fixed at some point ? (fingers crossed)

---

### Post by al.do on 2010-10-06
I have the same problem, I installed the deb package **wizardpen_0.7.3-1_i386.deb** and modified the **70-wizardpen.conf** file but my tablet dont work. Someone found a solution?

---

### Post by techno-mole on 2010-10-07
Not that I know of, I've been using my tablet on windows (dual boot)not doing much for my productivity, all my games are on windows :-)
Have you added you problem to the launchpad bug report ?

Here's the link ---> [launchpad bug report.]("https://bugs.launchpad.net/wizardpen/+bug/622152")
[COLOR="Red"]********** Please consider adding you tablet **********[/COLOR]

Please consider adding you tablet info to this wiki ---> [graphics tablet wiki]("https://wiki.ubuntu.com/GraphicsTablet")

Please read this ---> [https://lists.launchpad.net/wizardpen-testers/msg00000.html]("https://lists.launchpad.net/wizardpen-testers/msg00000.html") for further information.

Thanks.
[COLOR="Red"]********** UPDATE **********[/COLOR]

I now have the wizardpen driver working on maverick, thanks to Negora and Martin Owens, if you want to try it out, add the dr mo ppa from launchpad (if you haven't already) and either install the driver if it's not installed or remove the old version and then install the new one.
I have upgraded to maverick to test this out, and in gimp it runs well and it has all it's functions as far as I can tell (my tablet anyway) pressure sensitivity is working as well.

Cheers

---

