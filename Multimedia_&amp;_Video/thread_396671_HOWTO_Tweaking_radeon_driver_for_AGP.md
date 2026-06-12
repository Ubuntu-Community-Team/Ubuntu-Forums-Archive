---
title: "HOWTO: Tweaking radeon driver for AGP"
date: 2007-03-29
forum: Multimedia &amp; Video
---

### Post by BungaMan on 2007-03-29
If there is incorrect information, please let me know and I'll correct ASAP.  This howto is written for novice to expert users and assumes a bit of knowledge about editing xorg.conf.

[SIZE="3"]**First my setup ...**[/SIZE]

Ubuntu version : Edgy Eft
kernel version : 2.6.17-50-generic
ATI card : Mobility Radeon 9700SE (recognized as VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10])
Cardslot : AGP

xorg.conf is attached for reference.  As a side note:  It comes with a dual monitor setup (laptop LCD and CRT) using merged framebuffer.  The max texture size capability of my card is 2024x2024 so my virtual desktop is too large for beryl to work.  However, disconnecting my CRT reduces the virtual desktop size so that beryl can work.

[SIZE="4"][COLOR="Red"]_And a bit advice ..._[/COLOR][/SIZE]

1. Most of the options I've discovered by reading the manpage of the driver.  Please do so when you want to experiment.  There is text describing what it does.
Run the following in a terminal to read it
```
man radeon
```

2. Xorg.0.log is your friend during tweaking.  Read through it to discover which options are on by default and which are off.  Which are on but fail etc...

3. Backup your xorg.conf file now!

4. When modifying your options, do it one-by-one.  This allows you to test if an option helps or not or even makes X fail to start up.

5. Install Midnight Commander.  This is a file manipulator (browsing, viewing, editing, copying, deleting, ...) with a graphical interface in the console.  Very easy to use.
Run the following in a terminal to install it
```
sudo apt-get install mc
```
Run the following in a terminal to start Midnight Commander
```
mc
```

[SIZE="3"]**Lets get started ...**[/SIZE]

**_Collecting info_**
1. discover the capabilities of your card and motherboard (I got these instructions from a gentoo tutorial for which I'd like to thank the author)
Run the following in a terminal
```
sudo lspci -vv
```
And look for your video card (probably 01:0.0) and the host bridge (first one probably).  For your video card it should start with "VGA compatible controller: " and for the host bridge it starts with "Host bridge: ".

Here's an example of the important lines in my output:

```
[FONT="Courier New"]01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10] (prog-if 00 [VGA])
        Capabilities: [58] AGP version 2.0
                Status: RQ=80 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- **FW+** AGP3- **Rate=x1,x2,x4**
[/FONT]
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 21)
        Capabilities: [a0] AGP version 2.0
                Status: RQ=32 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- **FW+** AGP3- **Rate=x1,x2,x4**
```

- FW+:  This means that FastWrite can be enabled.  If they do not have it both then you cannot enable FastWrite.
- Rate: Gives you the capable rates.  You cannot set it higher than the lowest maximum.  Meaning if my card would say x1,x2 and my host bridge says x1,x2,x4 then the maximum AGPMode I can set is 2.  According to the output shown above it is 4.

**_Benchmarking the options_**
Glxgears is not a true benchmark but it sure gives an idea on performance.  I've attached my benchmarking results so you can have a look at it.  Benchmarking was done by setting my options in xorg.conf and press Ctrl-Alt-Backspace.  This restarted X allowing to apply the new config and then I logged on.  I waited a few seconds to get all standard stuff loaded and then opened up a terminal and ran glxgears.  This means that there's no compiz or beryl running.  The first 5 FPS lines are taken and put in the document.

**_Discussing options_**
Not all possible options are discussed but just the most common ones.

_GARTSize_: This is the amount of system memory that can be used for OpenGL textures.  Search in Xorg.0.log for GART and find out what it is set to.  For me it was 8 so I increased it to 64.  This should help for games that need more texture memory.  It probably cannot be set to any value.  In the lspci output you can see GART64- so I don't recommend setting it higher than that number unless you're up for an experiment.
```
Option "GARTSize" "64"
```
_EnablePageFlip_: The video card draws the screen in memory and then sets it ready for output.  In stead of waiting for the output to finish, it can start drawing the second screen in a different area.  This means that the second frame will be ready for output when the output of the first finishes.  This is used for 3D and turned off by default. Turn it on and you should have a noticeable improvement.
```
Option "EnablePageFlip" "True"
```
_AGPFastWrite_: This option made X fail to start in combination with setting AGPMode.  It could be different for you.  In general, I read that it doesn't help for performance. You'll need to test for yourself if it works.  It is turned off by default.  Also check with the lspci output if you can turn it on.
```
Option "AGPFastWrite" "False"
```
_backingstore_: This option is not mentioned in the manual and is turned off by default.  Not sure what it does but it doesn't seem to make a difference so I keep it off
```
Option "backingstore" "off"
```
_AGPMode_: This is where you use the information gathered from lspci.  Set it accordingly.  The higher it is set, the bigger bandwidth can be used to transfer data to and from your video card.  Specially noticeable when loading textures.  It defaults to 1 so you'll definitely get a boost!
```
Option "AGPMode" "4"
```
_AccelMethod_: There are 2 accelerating methods that can be used. XAA (Xfree86 Acceleration Architecture) and EXA.  XAA is stable and EXA is new and potentially unstable.  For me EXA degraded performance so I use the default which is XAA.
```
Option "AccelMethod" "XAA"
```
_AccelDFS_: Not really sure what it does but it stands for accelerated EXA DownloadFromScreen.  If EXA works for you then this can be used as an extra performance increase.  The manual says it is turned off by default due to issues with AGP so you are warned.
```
Option "AccelDFS" "False"
```
_DynamicClocks_: This is to dynamically reduce the clock speed of your graphics card.  A lower clock speed will reduce heat and extend the battery life but it can get in the way of performance.  It defaults to off.
```
Option "DynamicClocks" "off"
```
_EnableDepthMoves_: This option is not available in the manual so I don't know what it means.  It will default to False.  I noticed a slight performance increase and therefore turned it on.
```
Option "EnableDepthMoves" "True"
```

[SIZE="3"]**Finally ...**[/SIZE]

It all comes down to testing.  Perhaps a combination of one is better than a combination of the other.  I hope this explanation will help you without having to go through all combinations.  Any suggestions to improve this HOWTO are more than welcome.

---

### Post by josephus on 2007-03-30
How did you decide that EXA degraded your performance compared to XAA.  Is it based only on the numbers generated from glxgears?  When you are in EXA mode, EnablePageFlip is turned off and that's the main reason why the fps using glxgears is lower.  This however doesn't necessarily translate to worse performance in everyday use.  For myself Compiz is unusable unless EXA enabled.  Otherwise, it's a nice post.

---

### Post by BungaMan on 2007-03-30
Yes, it is based on the numbers from glxgears.  In my benchmark file you can see that I have EXA enabled together with EnablePageFlip which took the FPS down with 25% compared to the exact same combination but using XAA.

I've used glxgears as a fist indication of what triggers a difference.  I still want to do some real benchmarking for 2D and 3D.

---

### Post by josephus on 2007-03-30
I made a mistake in my last post which made it sound like EXA was worse than XAA for Compiz (it's corrected now).

Even though you specify an option in xorg.conf doesn't mean that it's actually being used.  You should look at the log files (xorg.0.log) and it will probably tell you that pageflip is not enabled when you use EXA regardless of whether you specify it to be enabled in the configuration file.

---

### Post by BungaMan on 2007-03-30
yup, I know.  That's why I verified that they were all set AND used.  Pageflipping is enabled when using EXA.  At least in my case because I can't find anything in the log about turning it off.  But you sure have a point, the FPS roughly equals to XAA and no pageflipping.

---

### Post by josephus on 2007-03-30
just looked through my xorg logs, looks like you are right - there is no message about pageflip being disabled when exa is enabled.  but i've looked through a couple of other forums and it is pretty consistent in saying pageflip doesn't work with exa.

---

