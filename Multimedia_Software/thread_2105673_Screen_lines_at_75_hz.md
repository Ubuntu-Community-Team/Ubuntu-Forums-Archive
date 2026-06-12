---
title: "Screen lines at 75 hz"
date: 2013-01-16
forum: Multimedia Software
---

### Post by Flying Mandarine on 2013-01-16
Hi everyone,

I have made a clean install of Ubuntu 12.10 on a brand new HDD (my old one broke down a few days ago). I also dual-boot with Windows 7. This is the same configuration I had previously, with the same hardware, except of course for the HDD.

First of all, it is worth noting that I don't use a computer screen but a Techwood television, model VL22TV1001.

My screen experiences curious faint white lines, especially on the right side of the screen, and a little more toward the lower right side. However, it does this only when I put the screen refresh rate at 75 hz. If I put it to 60 hz, everything is fine. It looks like some white lines are moving too. However, this is hardly visible on a white background, but becomes very visible on a black one.

I wouldn't mind staying at 60 hz (although I've read it's not as good for your eyes); however, the resolution I'd like to use (1280x768) can only be used with 75 hz, so I'm stuck with 1024x768 which happens to have a 60 hz option available. It does the same on Windows 7, but it doesn't seem to happen when the computer is powering up (before choosing an OS), although I could be mistaken. I suppose this is because the screen resolution on start-up is pretty low, and the refresh rate too.

Don't take my word for it, but I seem to recall that I actually was using 1280x768 without those lines before (although I wouldn't know what refresh rate I was using). I may be wrong, though.

Is there a way to get rid of those lines? Are they mainly on the right side of the screen because of a screen problem? Can I force the refresh rate somehow, making sure my screen wouldn't be damaged in the process? Why would it do this now when there didn't seem to be any problem before?

I understand this doesn't seem to be linked to Ubuntu itself since the issue also takes place on Windows 7, but since I'm not so sure where the problem comes from...

Thank you very much,

Patrice


Screen: Techwood VL22TV1001
Motherboard: P35C-DS3R
Processor: Q9300 Intel Core 2 Quad
Memory: 8 gb
Graphics card: ATi Radeon HD5850
OS: Ubuntu 12.10 64 bit, Windows 7 64 bit

---

### Post by Flying Mandarine on 2013-01-17
A quick update to add two things:

-it looks like it actually does have these faint white lines even while booting up the computer, but they are harder to see.

-it also looks like those lines appear when I'm in 60 hz. I didn't see them before, because they are much, much less visible.

Anybody have any idea? In any case, those lines appear mainly on the right, toward the bottom right hand corner of the screen.

Thank you,

Patrice

---

### Post by Flying Mandarine on 2013-01-17
I took a picture of Ubuntu 12.10 in 1024x768. The first picture is with a refresh rate of 60, the second, a refresh rate of 75. You can clearly see the difference, although it is slightly less visible than that in reality.

Refresh rate of 60: [http://i46.tinypic.com/10d5do0.jpg](http://i46.tinypic.com/10d5do0.jpg)
Refresh rate of 75: [http://i48.tinypic.com/depe08.jpg](http://i48.tinypic.com/depe08.jpg)

Does anyone have any idea? I'm at a loss here!

---

### Post by BicyclerBoy on 2013-01-17
It should be possible to make a custom modeline that just shifts the start/end of each scanline & so hide the edge.
This is a form of overscan compensation.

Is this TV connected by VGA?
Are you using the std distro FOSS video driver "radeon"?

Post your /var/log/Xorg.0.log file..

xrandr --prop

If the TV is a CRT then could also be possible to adjust the TV geometry via factory mode.
The TV may have overscan settings but this could lose a lot of screen area.

---

### Post by Flying Mandarine on 2013-01-18
Thank you for your help, BicyclerBoy.

When I go to "Details" on Ubuntu 12.10, and then in the Graphics tab, it just tells me:
Driver  Unknown
Experience  Standard

I don't know if this is the answer you were waiting for, but if I go to Additional Drivers in Software Sources, the selected driver is "Using X.Org X server - AMD/ATI display driver wrapper from xserver-xorg-video-ati (open source, tested). I tried the other two ("Using Video driver for the AMD graphics accelerators from fglrx" and the same but with "fglrx-updates") and they didn't seem to work at all.

The TV is connected by HDMI. The funny thing is, I used another screen (a computer screen this time) for just a few minutes before plugging in my TV, and there was a strange behavior: it would keep on reacting as if I was pressing random buttons on the screen (Menu, Brightness, Contrast, etc.). That didn't happen the last time I used it. But I suppose there's no link between this problem and the one with my TV?


The result of xrandr --prop:

> xrandr --prop
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
DisplayPort-0 disconnected (normal left inverted right x axis y axis)
	underscan vborder: 0 (0x00000000)	range:  (0,128)
	underscan hborder: 0 (0x00000000)	range:  (0,128)
	underscan:	off
		supported: off          on           auto        
	coherent: 1 (0x00000001)	range:  (0,1)
HDMI-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 16mm x 9mm
	EDID:
		00ffffffffffff003cad003700000000
		0a120103801009780a6837a454489a25
		0f4a4c3fef8001010101010101010101
		010101010101011d8018711c1620582c
		250010090000009e011d007251d01e20
		6e28550010090000001e000000fc0032
		32575f4c43445f54560a2020000000fd
		00314b0f2e08000a20202020202000fc
	underscan vborder: 0 (0x00000000)	range:  (0,128)
	underscan hborder: 0 (0x00000000)	range:  (0,128)
	underscan:	off
		supported: off          on           auto        
	coherent: 1 (0x00000001)	range:  (0,1)
   1920x1080i     30.0 +
   1280x720       60.0  
   1024x768       75.1     70.1     60.0* 
   1024x576       60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   848x480        60.0  
   640x480        72.8     75.0     66.7     60.0  
DVI-0 disconnected (normal left inverted right x axis y axis)
	load detection: 1 (0x00000001)	range:  (0,1)
	underscan vborder: 0 (0x00000000)	range:  (0,128)
	underscan hborder: 0 (0x00000000)	range:  (0,128)
	underscan:	off
		supported: off          on           auto        
	coherent: 1 (0x00000001)	range:  (0,1)


My /var/log/Xorg.0.log is quite long. Should I just copy-paste it here like xrandr --prop above?

Finally, I think my TV is an LCD? If a CRT TV is necessarily those old TV sets, then no, it's not. I already tried going in the menu but I can't find anything to adjust anything except Contrast, Brightness and Colors (and it's not even accessible in Game Mode).

What feels really curious to me is that the more I'm using this computer since the clean install, the more I feel like this problem wasn't here before: the lines are far too visible on a dark background at 75hz, I would have noticed them before.

Thank you for your help!

---

### Post by BicyclerBoy on 2013-01-18
Internally most LCD (DFPs) refresh at 60Hz.
LCD TVs in US/Japan/SAm at 60Hz & most of the rest of world at 50Hz.
The next gen TVs push this to 100/120.

Most TVs & monitors have an input pre-scaler circuit block. That's how it can accepts lots of video modes etc..

With DFP the refresh rate only effects motion blur/judder; there is no eye strain with static images.

Pushing video at the display at non-native refresh scan rates is asking for terrible jitter motion juddering.

The best image PQ/sharpness is at the native resolution.
 
Why do you want a non-native resolution?
You can over-ride the screen dimensions to scale the desktop icons etc..
xrandr --fbmm XmmxYmm

You could try:
xrandr --output HDMI-0 --scale 0.99x0.99

Can you try just:
xrandr

---

### Post by Flying Mandarine on 2013-01-19
Alright, so I understand I better stick to one of the native resolutions. The reason I didn't want to was that all the native resolutions either do not fit the screen, or everything is way too small (this TV isn't too big).

But I understand, from what you say, that I can perfectly choose a native resolution that doesn't fit the screen, and then scale it down a little. That might work indeed.

However, when I try xrandr --output HDMI-0 --scale 0.99x0.99, it doesn't make any noticeable change. I tried 0.80x0.80, but it only seemed to resize the bottom and the right of the screen; I still couldn't see the top and left parts.

I am not sure how to use xrandr --fbmm XmmxYmm so I didn't try putting random numbers in case my screen explodes. How am I supposed to use it, say, with 1280x720 and with 1920x1980 (all 16:9 don't fit the screen entirely, while all 4:3 seem to do the trick)?

Finally, here is the output for xrandr:

> Screen 0: minimum 320 x 200, current 1268 x 713, maximum 8192 x 8192
DisplayPort-0 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected 1280x720+0+0 (normal left inverted right x axis y axis) 16mm x 9mm
   1920x1080i     30.0 +
   1280x720       60.0* 
   1024x768       75.1     70.1     60.0  
   1024x576       60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   848x480        60.0  
   640x480        72.8     75.0     66.7     60.0  
DVI-0 disconnected (normal left inverted right x axis y axis)


If I understand, this means 1920x1080 works only with a refresh rate of 30? Since I use this computer for gaming too, should I try 1280x720 instead?

My apologies for all the questions.
Thank you!

---

### Post by Flying Mandarine on 2013-01-19
Alright, I just managed to scale down the screen on Windows 7 by simply putting a 1280x720 resolution and then using the Catalyst Control Center (for ATi Radeon graphics cards) to put an underscan of 6%. Since it is in 59 hz, there are no white lines anymore.

I suppose that, if I have the correct Terminal command to do the same in Ubuntu 12.10, it would achieve the same result.

---

### Post by BicyclerBoy on 2013-01-19
The 1080i 30Hz mode is an interlaced mode; 30 frames/sec, 60fields/sec.
The field rate is 60Hz.
Good de-interlacering doubles the frame rate 30 -->60/sec.

If you TV is cheap then it's de-interlacer will be horrible better to output 720p (p denotes progressive frames=fields)

This line from xrandr:
> HDMI-0 connected 1280x720+0+0 (normal left inverted right x axis y axis) 16mm x 9mm
- it thinks your screen is 16mm by 9mm..I think your TVs EDID has been created by someone with no understanding..

"$xrandr --fbmm XmmxYmm"   where X & Y are in "mm" (m/1000)
Measure your screen with a ruler & use the right numbers..
i.e.
"$xrandr --output HDMI-0 --mode 1024x768"
"$xrandr --output HDMI-0 --scale 1x1"
"$xrandr --fbmm 400x200"
Can use --dpi to change the desktop text/gadget size.

You can use the linux AMD Catalyst fglx driver.

Aspect ratio:
get the screen size right first..
This issue is complicated because:
-  pixel aspect ratio of SD & HD material is different
-  your display has 4:3 screen pixel aspect ratio for 16:9 physical size

Is your display a true 16:9 or 16:10 or 4:3?

---

### Post by Flying Mandarine on 2013-01-20
The TV indeed seems to be a pretty cheap one given the deal my parents got on it.

I measured the TV and it is approximately 47,5 cm by 26,7 cm. Does that answer whether it's a 16:10, 16:9 or 4:3? I have no idea how to obtain this information.

When I input $xrandr --fbmm 47mmx26mm, it says --fbmm: command not found. The same goes for the two $xrandr --output HDMI-0 commands you advised: --output: command not found.

As for the linux AMD Catalyst fglx driver, I tried to install it via Software Sources (more information on my first post), but it didn't seem to be recognized. Tough luck!

---

### Post by BicyclerBoy on 2013-01-20
The measurement units cm are non-SI & only used by clothing industry.

How do you convert 47.5cm to 47mm..??

The leading character "$"  is meant to indicate the use of terminal shell.
Don't type it into terminal...

$xrandr --fbmm 475mmx267mm

aspect ratio = (475 / 267) = 1.779 ~= 16/9..

There is/was a problem with AMD Catalyst & the version of Xorg in 12.10..This should have been sorted by now.

---

### Post by Flying Mandarine on 2013-01-21
Hi!

Indeed it was completely careless of me to translate cm into mm like that...

I tried $xrandr --fbmm 475mmx267mm (without the $ sign) and it didn't do anything except show the help text for the function:

> xrandr --fbmm 475mmx267mm
usage: xrandr [options]
  where options are:
  -display <display> or -d <display>
  -help
  -o <normal,inverted,left,right,0,1,2,3>
            or --orientation <normal,inverted,left,right,0,1,2,3>
  -q        or --query
  -s <size>/<width>x<height> or --size <size>/<width>x<height>
  -r <rate> or --rate <rate> or --refresh <rate>
  -v        or --version
  -x        (reflect in x)
  -y        (reflect in y)
  --screen <screen>
  --verbose
  --current
  --dryrun
  --nograb
  --prop or --properties
  --fb <width>x<height>
  --fbmm <width>x<height>
  --dpi <dpi>/<output>
  --output <output>
      --auto
      --mode <mode>
      --preferred
      --pos <x>x<y>
      --rate <rate> or --refresh <rate>
      --reflect normal,x,y,xy
      --rotate normal,inverted,left,right
      --left-of <output>
      --right-of <output>
      --above <output>
      --below <output>
      --same-as <output>
      --set <property> <value>
      --scale <x>x<y>
      --scale-from <w>x<h>
      --transform <a>,<b>,<c>,<d>,<e>,<f>,<g>,<h>,<i>
      --off
      --crtc <crtc>
      --panning <w>x<h>[+<x>+<y>[/<track:w>x<h>+<x>+<y>[/<border:l>/<t>/<r>/<b>]]]
      --gamma <r>:<g>:<b>
      --primary
  --noprimary
  --newmode <name> <clock MHz>
            <hdisp> <hsync-start> <hsync-end> <htotal>
            <vdisp> <vsync-start> <vsync-end> <vtotal>
            [flags...]
            Valid flags: +HSync -HSync +VSync -VSync
                         +CSync -CSync CSync Interlace DoubleScan
  --rmmode <name>
  --addmode <output> <name>
  --delmode <output> <name>
  --listproviders
  --setprovideroutputsource <prov-xid> <source-xid>
  --setprovideroffloadsink <prov-xid> <sink-xid>


I tried to reinstall the Catalyst drivers again (my Ubuntu 12.10 is up to date), once via the Restricted Drivers in Software Sources, and another time via the Ubuntu Software Center. It didn't work: I couldn't access the menu bar on the left, and moving a window about was slow, which I suppose means that it was using the motherboard's graphic card chipset instead of my ATi Radeon. In details, there was written "VESA:CYPRESS" instead of "Unknown."

It looks like most xrandr commands I tried previously just weren't recognized. Am I missing a piece of software?

---

### Post by BicyclerBoy on 2013-01-21
My mistake:
$xrandr --fbmm 475x267

don't add the units after numbers..
I had it right in previous post..

I wouldn't bother with Catalyst driver until you can find information stating the *buntu distro driver is compatible with 12.10 Xorg version.

---

### Post by Flying Mandarine on 2013-01-22
Alright, the command does work in that it doesn't display an error, but there doesn't seem to be anything changing. I tried it while in 1024x768 and in 1280x720, but it did nothing in both cases.

Maybe there is another command that needs to be input first in order for this one to work?

Thanks for your help!

---

### Post by BicyclerBoy on 2013-01-22
Maybe all 3 in sequence:

$xrandr --output HDMI-0 --mode 1024x768
$xrandr --output HDMI-0 --scale 1x1
$xrandr --fbmm 475x267

then
$xrandr
post the output..

It is possible that EDID values of 16x9 is internally ignored because it is plainly incorrect..

---

### Post by Flying Mandarine on 2013-01-23
It didn't do anything either. However, 1024x768 did already work just fine (it's just completely stretched because it's 4:3), so I am not sure if you actually wanted me to do $xrandr --output HDMI-0 --mode 1024x768 or rather $xrandr --output HDMI-0 --mode 1280x720 . I tried both, here is the output:

> Screen 0: minimum 320 x 200, current 1280 x 720, maximum 8192 x 8192
DisplayPort-0 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected 1280x720+0+0 (normal left inverted right x axis y axis) 16mm x 9mm
   1920x1080i     30.0 +
   1280x720       60.0* 
   1024x768       75.1     70.1     60.0  
   1024x576       60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   848x480        60.0  
   640x480        72.8     75.0     66.7     60.0  
DVI-0 disconnected (normal left inverted right x axis y axis)


And:

> Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
DisplayPort-0 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 16mm x 9mm
   1920x1080i     30.0 +
   1280x720       60.0  
   1024x768       75.1*    70.1     60.0  
   1024x576       60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   848x480        60.0  
   640x480        72.8     75.0     66.7     60.0  
DVI-0 disconnected (normal left inverted right x axis y axis)


(I let it at 75.1 but I could have put it in 60.0 to prevent the white lines, which is what I do in 1024x768 so long as I can't put a 16:9 resolution that takes the whole screen.)

---

### Post by BicyclerBoy on 2013-01-23
I think you better post the /var/log/Xorg.0.log..
I starting to have doubts about the native screen size..

Can set rate :
$xrandr --output HDMI-0 --mode 1024x768 --rate 60.0

---

### Post by Flying Mandarine on 2013-01-24
I already tried the command you gave me; I actually put it as a startup application. No screen lines because it's 60 hz, but still not the resolution I wanted.

About the Xorg.0.log, sure; should I post the whole file using quote tags? It is pretty big.

---

### Post by BicyclerBoy on 2013-01-25
Make it an .txt file attachment then..
(rename Xorg.0.log.txt)

---

### Post by Flying Mandarine on 2013-01-27
I tried to upload the file here but it said "Your file of 58.9 KB bytes exceeds the forum's limit of 19.5 KB for this filetype."

So I uploaded it on another site:

[http://depositfiles.com/files/g0e2mubfv](http://depositfiles.com/files/g0e2mubfv)

Hopefully it works.

---

### Post by BicyclerBoy on 2013-01-28
I think the native is 1152x864 but 75Hz refresh is greater than max pixel clk in EDID..

```

$xrandr --newmode "1152x864_60.00"   81.75  1152 1216 1336 1520  864 867 871 897 -hsync +vsync
$xrandr --addmode HDMI-0 "1152x864_60.00"
$xrandr --output HDMI-0 --mode "1152x864_60.00"
$xrandr --output HDMI-0 --scale 1x1
$xrandr --fbmm 475x267

```

---

### Post by heli1 on 2013-01-28
trash unity   no good for nothing stupid make it better cant find nothing eny more 
worse then windows

---

### Post by Flying Mandarine on 2013-01-28
BicyclerBoy: Am I supposed to add your code at the end of the file, or in place of something else? And is it safe (meaning, is there a risk for my computer to break down if it's not a resolution that's supported)? I've never seen a choice for such resolution, even on Windows.

heli1: Actually, I would be quite satisfied with it were it not for this problem... I've had my share of problems over the year, but in recent years, Ubuntu seemed to work perfectly for me, with Unity. So if I can solve the problem without resorting to something other than Unity, I'd prefer that!

---

### Post by BicyclerBoy on 2013-01-29
Just enter those cmds in terminal or stick them in a text file/script & run it from terminal..

I don't believe you can damage any modern monitor (inc CRT).

The 75Hz rates of 1280x1024 & 1152x864 are excluded from "video mode pool" because the pixel clock is greater than max in EDID.
The 60Hz refresh makes more sense.
Alternatively it is possible to force the max pixel clock freq test to be ignored, I just don't know the ati/radeon keywords..

If you want to try 1280x768 60p:
```

$xrandr --newmode "1280x768R"   68.00  1280 1328 1360 1440  768 771 781 790 +hsync -vsync
or
$xrandr --newmode "1280x768_60.00"   79.50  1280 1344 1472 1664  768 771 781 798 -hsync +vsync

```

you have to craft the remaining cmds to use the "mode label".

The problem with Unity was forcing it on users with no obvious/easy way to get to gnome-fallback or similar.
There should have been a Canonical version of "cinnamon" desktop.

---

### Post by Flying Mandarine on 2013-01-30
Great! I think the problem is nearly solved.

I entered those commands (1152x864_60.00 just didn't work, resolution not supported):

> xrandr --newmode "1280x768_60.00"   79.50  1280 1344 1472 1664  768 771 781 798 -hsync +vsync
xrandr --addmode HDMI-0 "1280x768_60.00"
xrandr --output HDMI-0 --mode "1280x768_60.00"

And it worked!

However, when I restart the computer, it goes back to the 1024x768 resolution, even after I deleted the command line in Startup Applications.

So I decided to put each one of those three lines of code into a different startup application (or is there a way to maybe put all three into one "application?"), but it doesn't seem to do anything: it still goes to 1024x768.

Would you have any idea of how to set those three marvelous lines of code so that I don't have to type them every time I start the computer?

---

### Post by BicyclerBoy on 2013-02-01
I would try placing them in /etc/rc.local
or into a script with the script (full path) invoked/run from /etc/rc.local

Your script needs a shebang (#!/bin/sh) & execute bit set..

It is possible to create/use /etc/X11/xorg.conf but the syntax is a little different & not as flexible.

Try the reduced VB 60Hz timing as well. Should work on any DFP.
FYI.
The timings were generated from:
$cvt -r 1280 768 60

---

### Post by Flying Mandarine on 2013-02-03
Hi BicyclerBoy,

I spent a few hours trying what you said, but I'm afraid much of what you wrote is way too technical for me. I don't know whether to add those lines before or after the "exit 0" of the rc.local, I don't understand what you mean by "Your script needs a shebang (#!/bin/sh) & execute bit set.." and I don't know how to "Try the reduced VB 60Hz timing as well."

If this is too much work to explain, please disregard: you've helped me so much already, and the screen display now works fine if I enter those three commands each time I start the computer. Trying to do that automatically is just a minor issue.

Thank you,

FlyingMandarine

---

### Post by BicyclerBoy on 2013-02-04
Put the cmds in the rc.local file just before "exit 0"..

The "exit 0" sets the exit value to 0 (no error) if the script completes/gets to end.

The reduced (vertical blank) timings are the default 60Hz video modes over HDMI/DVI.

This cmd generates reduced blanking timings:
$cvt -r 1280 768 60

just try the reduced video modeline in place of the other "1280x768_60.00".
You need to change all 3 commands..

---

### Post by Flying Mandarine on 2013-02-08
Hi BicyclerBoy, sorry for the late answer,

I put the commands in /etc/rc.local; it looks like this:

> # By default this script does nothing.

xrandr --newmode "cvt -r 1280 768 60" 79.50 1280 1344 1472 1664 768 771 781 798 -hsync +vsync
xrandr --addmode HDMI-0 "cvt -r 1280 768 60"
xrandr --output HDMI-0 --mode "cvt -r 1280 768 60"

exit 0

But it still didn't do anything -- although writing them separately one after another in the Terminal works very well.

---

### Post by BicyclerBoy on 2013-02-09
I should try out cmds before suggesting them..

I guess the above failed because the rc.local file is run before the X server is loaded..

Short of using an xorg.conf file (to be avoided)...
a script in ~/.xinitrc/ (private to user; "~" means home path)

The suggested system wide Xinit script location seems to have vanished..

---

### Post by Flying Mandarine on 2013-02-10
I found only one .xinitrc file, in /etc/X11/xinit. Can I try this one out safely?

And am I just supposed to paste this:

> xrandr --newmode "cvt -r 1280 768 60" 79.50 1280 1344 1472 1664 768 771 781 798 -hsync +vsync
xrandr --addmode HDMI-0 "cvt -r 1280 768 60"
xrandr --output HDMI-0 --mode "cvt -r 1280 768 60"

exit 0 

in the new file? With or without the 'exit 0' bit?

Again, thank you for your help,

FlyingMandarine

---

### Post by BicyclerBoy on 2013-02-10
Don't know..
How much harm can it do?

The ~/.xinitrc/ I refer to is a hidden folder in your home folder..
It may not exist.

But your /etc/X11/xinit/xinitrc folder/file seems promising ..
The definitive answer should be found on Xorg.org website..

I would not add the "exit 0" to end of the new file.

---

### Post by Flying Mandarine on 2013-02-15
I found the file where you suggested it would be. However, I'm afraid it's still not working.

There is only one line of command in that file:

> . /etc/X11/Xsession

I tried adding the following both before and after that line of command:

> xrandr --newmode "cvt -r 1280 768 60" 79.50 1280 1344 1472 1664 768 771 781 798 -hsync +vsync
xrandr --addmode HDMI-0 "cvt -r 1280 768 60"
xrandr --output HDMI-0 --mode "cvt -r 1280 768 60"

But it didn't work. However, it still does work pretty well when I input those three commands manually in the Terminal after Ubuntu has booted.

---

### Post by BicyclerBoy on 2013-02-15
It's possible the full path to executable is required
/usr/bin/xrandr

It is possible the best soln is a script in hidden folder in user home
~/.xinitrc/my_script

---

### Post by Flying Mandarine on 2013-02-21
Well that's curious, I thought I had answered a few days ago...

I added this full path, but it didn't work either.

As for ~/.xinitrc/my_script, I didn't find it in my Home folder.

Although I would like to know what the problem actually is, the fact is, I just have to enter those three commands in the terminal when I start my computer and everything is fine, so I don't want to bother you any longer, as I don't think it's worth the trouble.

You've been incredibly helpful BicyclerBoy, and thanks to you my problem is practically solved, which is more than enough!

Thank you for your time and patience,

FlyingMandarine

---

### Post by BicyclerBoy on 2013-02-23
You most likely do not have the hidden folder (& therefore any contents)..

You have to create the hidden folder...& the script inside.

I'll try some experiments on my computer & get back to you..

Failing all that you could place the commands into a script (text file with execute bit set) & launch it from keyboard combo or desktop icon..

---

