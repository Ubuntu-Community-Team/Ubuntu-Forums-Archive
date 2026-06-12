---
title: "HOW TO Setup a Wacom Tablet with Multi-Monitors in Maverick and Natty"
date: 2010-12-30
forum: Multimedia Software
---

### Post by Favux on 2010-12-30
**along with Aiptek, Hanwang, N-trig, Waltop, & WizardPen (Ace Cad, KYE Systems, UC-LOGIC) Tablets**

Last updated:  November 21, 2011

**[SIZE="3"]Preliminaries[/SIZE]**
1) **You must have** X server 1.8 or up (Maverick has 1.9).


**[SIZE="3"]Sources[/SIZE]**
"[xsetwacom: Support MapToOutput for TwinView]("http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=commit;h=7fe557d404a2e7aa192ff68ebdec5436696c9f4a")" by Jason Gerecke
"[xsetwacom: add "MapToOutput" parameters]("http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=commit;h=239822f9f4973dc2b3a51fd8af74bfda0349dece")" by Peter Hutterer
"[dix: add 3x3 transformation matrix xinput property for multi-head handling]("http://www.mail-archive.com/xorg-devel@lists.x.org/msg08731.html")" by Peter Korsgaard
xf86-input-wacom from part II of the [Bamboo P & T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") or section 2 of the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").
"man xrandr"
"[Transformation matrix]("http://en.wikipedia.org/wiki/Transformation_matrix")"
"[Matrix multiplication]("http://en.wikipedia.org/wiki/Matrix_multiplication")"


**[SIZE="3"]Miscellaneous Notes[/SIZE]**
First Wacom testers to report success were [dsavi]("http://ubuntuforums.org/showthread.php?t=967147&page=68") & [mugginz]("http://sourceforge.net/mailarchive/forum.php?thread_name=AANLkTi%3D7HSGkfAtMJypCss%3DVXm_5ZNNE6c9mcLfGeGQ_%40mail.gmail.com&forum_name=linuxwacom-discuss").
First WizardPen (Genius MousePen 8x6/UC-LOGIC) testers to report success were [elnaureth]("http://ubuntuforums.org/showpost.php?p=10348699&postcount=5") & [1script]("http://ubuntuforums.org/showthread.php?t=1571365&page=5").


**[SIZE="3"]Summary[/SIZE]**
This HOW TO is divided into three sections.  The first is the **xsetwacom MapToOutput Method** for tablets on the Wacom drivers.  MapToOutput has been extended to apply to the Nvidia proprietary driver, i.e. **TwinView** starting with the xf86-input-wacom-0.12.0 release.  The second is the **Coordinate Transformation Matrix Method** which works for all tablets.  The third deals with getting either method to work through a reboot.


**[SIZE="3"]I. xsetwacom MapToOutput Method[/SIZE] - for Tablets using the xf86-input-wacom driver:  Hanwang, N-trig, Wacom, & Waltop**
The nice thing about MapToOutput is it does all of the matrix calculations for you automatically.

1) **You must have** xf86-input-wacom 0.10.9 (0.10.8+ after the 8-11-10 commit "xsetwacom: add "MapToOutput" parameters."; the default in Maverick is 0.10-8 ) if you have a 32-bit install.  Otherwise if you have a 64-bit install you must have xf86-input-wacom 0.10.10+ (after the 1-11-11 commit "xsetwacom: fix 64-bit issues with MapToOutput").

First determine the "device name" of what you want bound on a specific screen.  Your choices will be the stylus, eraser, or cursor (Wacom tablet mouse).  In a terminal enter:
```
xinput --list
```
The output should contain the "device names" you are after.  For example for the stylus it might be:
> "Wacom BambooFun 2FG 6x8 Pen stylus"
Quotes added because you'll need them.

The new method relies on a new xsetwacom command in the form:
> xsetwacom set <device name> MapToOutput VGA1
Enter in a terminal:
```
xrandr
```
and select the name of the monitor, among the monitors you see in the output, that you would like the device on.  Substitute that monitor name for VGA1 in the command.  Using your "device name" (in quotes) from 'xinput list' you can now use the xsetwacom command:
```
xsetwacom set "device name" MapToOutput VGA1
```

2) **TwinView** (NVidia proprietary driver binary).  Support was added with the "xsetwacom: Support MapToOutput for TwinView" commit on 6-23-11 (in the 0.11.99+ tree) and is available in the xf86-input-wacom-0.12.0 release tar.

Choose the monitor you want the input tool on using "HEAD-0", "HEAD-1", etc., e.g.:
```
xsetwacom set "device name" MapToOutput HEAD-0
or
xsetwacom set "device name" MapToOutput HEAD-1
```

**Note**:  the above MapToOutput commands only apply to the current xrandr configuration, they will need to be re-applied with a restart (or rotation).  So you'll have to set up the xsetwacom *MapToOutput* command(s) in a startup script.  See below.


**[SIZE="3"]II. Coordinate Transformation Matrix Method[/SIZE] - for all Tablets**
While the following may seem a little daunting if you look at the examples you'll find it is not that hard.  The code does the matrix multiplication for you.  You are determining the matrix values by solving fractions involving your monitors' dimensions.

First determine the "Device name" of what you want bound on a specific screen.  Your choices will be the stylus, eraser, or cursor (Wacom tablet mouse).  In a terminal enter:
```
xinput --list
```
Using the "Device name" (in quotes) enter in a terminal:
```
xinput list-props "Device Name"
```
For example:
```
xinput list-props "Wacom BambooFun 2FG 6x8 Pen stylus"
```
This will give an output that contains your current 'Coordinate Transformation Matrix' for the device as the X server sees it:
```
Coordinate Transformation Matrix (123):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000

```
Now let's do a quick overview of the math involved.  Notice that while it is an Identity matrix:
```
[ 1 0 0 ]
[ 0 1 0 ]
[ 0 0 1 ] 
```
which has the effect of multiplying by 1, or in other words no transformation, the addition of a third vector value (beyond X & Y) makes it an affine transformation with homogeneous coordinates.  We need to determine the transform matrix appropriate to the monitor you want to place the device on.

What we will do with the transform is translate the currently assigned pixel coordinate vector X,Y of your tablet device to a new pixel coordinate vector X',Y'.

The numbers in the X server "Coordinate Transformation Matrix" are a 3x3 matrix read out row by row.  Using an affine transformation means translation can be expressed with matrix multiplication.  The equation we are looking at is in the form of:
```
[ x' ]   [ c0 c1 c2 ]   [ x ]
[ y' ] = [ c3 c4 c5 ] * [ y ]
[ 1  ]   [ c6 c7 c8 ]   [ w ]
```
The third vector value w (the row) 0 0 1, with c8 or w always equal to 1, is what makes it affine.

The associated linear equations would be:
```
x' = (c0x + c1y + c2) / w'
y' = (c3x + c4y + c5) / w'
w' = (c6x + c7y + c8) = 1
```
So c0 and c4 corresponds to the scaling on the X and Y axes, c2 and c5 corresponds to the translation (X & Y offsets) on those axes, and c6, c7, and c8 are always 0, 0 and 1.

Rumtscho describes how to calculate the general case in [post #8]("http://ubuntuforums.org/showpost.php?p=10330180&postcount=8") below.

**[SIZE="3"]I.  Dual Monitors[/SIZE]**
**a) Two monitors with the same resolution**:  is the simplest case.

Say both monitors are 1280x1024.  You first set up the linear transform (matrix) like so.
```
  left:                               right:
[ 1280/(1280+1280)  0         0 ]   [ 1280/(1280+1280)  0          1280/(1280+1280)]
[ 0                 1024/1024 0 ]   [ 0                 1024/1024  0               ]
[ 0                 0         1 ]   [ 0                 0          1               ]
```
Using fractions amounts to scaling from 0-1 so you end up with the following.
```
  left:           right:
[ 0.5 0 0 ]     [ 0.5 0 0.5 ]
[ 0   1 0 ]     [ 0   1 0   ]
[ 0   0 1 ]     [ 0   0 1   ]
```
With the c2 = 0.5 on the right matrix being the x offset.

Now that you've determined the transform use the appropriate xinput command for the monitor you want your device on:
***Left monitor***:
```
xinput set-prop "Device name" --type=float "Coordinate Transformation Matrix" 0.5 0 0 0 1 0 0 0 1
```
***Right monitor***:
```
xinput set-prop "Device name" --type=float "Coordinate Transformation Matrix" 0.5 0 0.5 0 1 0 0 0 1
```

**b) Two monitors with different resolutions**:  example by Rumtscho
[IMG]http://i.imgur.com/L5PNk.png[/IMG]
* image courtesy of Rumtscho

Setting  up the linear transform (matrix).
```
  left:                                right:
[ 1280/(1280+2560)  0          0 ]   [ 2560/(1280+2560)  0          1280/(1280+2560)]
[ 0                 1024/1440  0 ]   [ 0                 1440/1440  0               ]
[ 0                 0          1 ]   [ 0                 0          1               ]
```
Since for Rumtscho 'xinput --list' returned the stylus "Device name" as "Wacom BambooFun 2FG 6x8 Pen stylus" the appropriate xinput commands for device placement on the monitors are:
***Left monitor***:
```
xinput set-prop "Wacom BambooFun 2FG 6x8 Pen stylus" --type=float "Coordinate Transformation Matrix" 0.333333 0 0 0 .711111 0 0 0 1
```
***Right monitor***:
```
xinput set-prop "Wacom BambooFun 2FG 6x8 Pen stylus" --type=float "Coordinate Transformation Matrix" 0.666666 0 0.333333 0 1 0 0 0 1
```

**c) Two monitors with one rotated**:  example courtesy of lejono
Left monitor 1600x1200 & right monitor (tablet pc) 1280x800.  Tablet pc in laptop mode.
```
  left:                                right:
[ 1600/(1600+1280)  0          0 ]   [ 1280/(1600+1280)  0         1600/(1600+1280)]
[ 0                 1200/1200  0 ]   [ 0                 800/1200  0               ]
[ 0                 0          1 ]   [ 0                 0         1               ]
```
***Left monitor***:
```
xinput set-prop "Serial Wacom Tablet stylus" --type=float "Coordinate Transformation Matrix" 0.555555 0 0 0 1 0 0 0 1
```
***Right monitor***:
```
xinput set-prop "Serial Wacom Tablet stylus" --type=float "Coordinate Transformation Matrix" 0.444444 0 0.555555 0 0.666666 0 0 0 1
```
* lejono established 6 decimal accuracy; matrices changed to reflect that

Now if we rotate to tablet mode we are adding a rotional transformation.  Let's use rotation by an angle A counter-clockwise about the origin.  The functional form would be x' = xcosA &#8722; ysinA and y' = xsinA + ycosA but we want to make it affine so we can use multiplication.  And we need to add it to the current matrix.  So written in matrix form, it becomes something like:
```
[ x' ]   [ cosA*c0 -sinA*c1 c2 ]   [ x ]
[ y' ] = [ sinA*c3  cosA*c4 c5 ] * [ y ]
[ 1  ]   [ c6       c7      c8 ]   [ w ]
```
representing the equations:
```
x' = (cosA*c0x + -sinA*c1y + c2) / w'
y' = (sinA*c3x +  cosA*c4y + c5) / w'
w' = (c6x      +  c7y      + c8) = 1
```
If we rotate the tablet 180 degrees to inverted, since cos(180) = -1 and sin(180) = 0 you end up with:
```
   right:
[ -1280/(1600+1280)  0        1280/1280 ]
[  0                -800/1200 800/1200  ]
[  0                 0        1         ]

[ -0.444444  0        1        ]
[ 0         -0.666666 0.666666 ]
[ 0          0        1        ]
```
***Right monitor* rotated to inverted**:
```
xinput set-prop "Serial Wacom Tablet stylus" --type=float "Coordinate Transformation Matrix" -0.444444 0 1 0 -0.666666 0.666666 0 0 1
```
Now what happens if we rotate the tablet pc to portrait mode?  Note X & Y swap, becoming 800x1280.  Since cos(270) = 0 and sin(270) = -1 you end up with this matrix.
```
   right:
[  0          800/(1600+800) 1600/(1600+800) ]
[ -1280/1280  0              1280/1280       ]
[  0          0              1               ]

[  0  0.333333 0.666666 ]
[ -1  0        1        ]
[  0  0        1        ]
```
***Right monitor* rotated to portrait**:
```
xinput set-prop "Serial Wacom Tablet stylus" --type=float "Coordinate Transformation Matrix" 0 0.333333 0.666666 -1 0 1 0 0 1
```

**[SIZE="3"]II.  Three Monitors - simple case[/SIZE]**
Three monitors with the same resolution.  You set up the linear transform and since we're scaling from 0-1 if all three monitors have the same resolution you'd end up with:
```
  left                           center                                     right
[ 1280/(3*1280) 0         0 ]  [ 1280/(3*1280) 0         1280/(3*1280) ]  [ 1280/(3*1280) 0         (2*1280)/(3*1280) ]
[ 0             1024/1024 0 ]  [ 0             1024/1024 0             ]  [ 0             1024/1024 0                 ]
[ 0             0         1 ]  [ 0             0         1             ]  [ 0             0         1                 ]

  left:              center:                 right:
[ 0.3333 0 0 ]     [ 0.3333 0 0.3333 ]     [ 0.3333 0 0.6666 ]
[ 0      1 0 ]     [ 0      1 0      ]     [ 0      1 0      ]
[ 0      0 1 ]     [ 0      0 1      ]     [ 0      0 1      ]
```
* tested by mugginz, he used 3 decimal accuracy
* Rumtscho was able to use 4 decimal accuracy; matrices changed to reflect that

So now the xinput commands to set the device to the desired monitor are:
***Left monitor***:
```
xinput set-prop "Device name" --type=float "Coordinate Transformation Matrix" 0.333333 0 0 0 1 0 0 0 1
```
***Center monitor***:
```
xinput set-prop "Device name" --type=float "Coordinate Transformation Matrix" 0.333333 0 0.333333 0 1 0 0 0 1
```
***Right monitor***:
```
xinput set-prop "Device name" --type=float "Coordinate Transformation Matrix" 0.333333 0 0.666666 0 1 0 0 0 1
```

**Note**:  The xinput command does not last through a restart.  See below.


**[SIZE="3"]III. To Have the Settings Last Through a Reboot[/SIZE]**
You have to apply the xinput or xsetwacom command with each restart.  You should be able to add it to your xsetwacom start up script, if you have one.  Otherwise run it from a convenient start up script.  Sample start up scripts are attached to posts 1 & 2 of the **[Bamboo P & T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562")** thread.  Add the appropriate command for each device (stylus, eraser, and cursor) to its section.

To set it up to auto-start, download a sample file or make your own, and rename it .xsetwacom.sh (or whatever you want) and place it in your home directory. Remember it will be a hidden file. To enable the xsetwacom commands in the .xsetwacom.sh file to apply to Xserver through a reboot you enter in a terminal:
```
chmod +x ~/.xsetwacom.sh
```
or you could right click on the file and in Properties, in the Permission tab, check Execute as program. Then go to System->Preferences->Startup Applications and click on add and for the command write "sh /home/yourusername/.xsetwacom.sh" (without the quotes). You can also change your settings on the fly using the xsetwacom parameters in a terminal. They only apply during the current session.

Once the script is executable you can double click on it to apply it's settings or reboot to check the auto-start set up.

**Note**: In the sample scripts both "device name" and ID # are used. Be sure to check for yours using 'xinput --list' (without the quotes) in a terminal and use them. When you use a xorg.conf the "device names" will be stylus, eraser, touch, and pad. If you are hot plugging your tablet or other devices be sure to use "device name" as the ID # can change.


**Appendix 1 - Tablet PC Rotation with CTM**
Evdev rotation for those of you using evdev for touch seems to be broken currently on Natty.  You can use the CTM to do it instead.

The CTM for none/normal or no rotation is the identity matrix:
```

 [ 1  0  0 ]
 [ 0  1  0 ]
 [ 0  0  1 ]
```
and the command to implement it:
    xinput set-prop "Wacom Bamboo 2FG 4x5 Finger" "Coordinate Transformation Matrix" 1, 0, 0, 0, 1, 0, 0, 0, 1

The CTM for ccw/left rotation is:
```

 [ 0  1  0 ]
 [-1  0  1 ]
 [ 0  0  1 ]
```
and the command to implement it:
    xinput set-prop "Wacom Bamboo 2FG 4x5 Finger" "Coordinate Transformation Matrix" 0, 1, 0, -1, 0, 1, 0, 0, 1

The CTM for half/inverted rotation is:
```

 [-1  0  1 ]
 [ 0 -1  1 ]
 [ 0  0  1 ]
```
and the command to implement it:
    xinput set-prop "Wacom Bamboo 2FG 4x5 Finger" "Coordinate Transformation Matrix" -1, 0, 1, 0, -1, 1, 0, 0, 1

The CTM for cw/right rotation is:
```

 [ 0 -1  1 ]
 [ 1  0  0 ]
 [ 0  0  1 ]
```
and the command to implement it:
    xinput set-prop "Wacom Bamboo 2FG 4x5 Finger" "Coordinate Transformation Matrix" 0, -1, 1, 1, 0, 0, 0, 0, 1

Use your touch "device name" from *xinput list* of course.

---

### Post by Favux on 2010-12-30
**[SIZE="3"]Using xsetwacom commands to set TopX & Y and BottomX & Y[/SIZE] - this should work with any Xorg and xf86-input-wacom or linuxwacom**

**by SnickerSnack** from the "How to limit pen tablet to one display out of two?" thread, [post #33]("http://ubuntuforums.org/showpost.php?p=10299356&postcount=33").

I'm fairly sure that the instructions below are correct.

I followed [post #15]("http://ubuntuforums.org/showpost.php?p=9853590&postcount=15") by blady_pirat in the thread "Configuring Xorg for dual screen, single wacom" and it seems correct, if cryptic.  I'm going to state my interpretation of that here, and I'll also cover changing vertical values for those who have different resolutions on their monitors.

**_Preliminaries_**:
These instructions assume that you haven't changed anything using xsetwacom. If you have, you should reset to default values (that is, the stylus should work normally when no external monitor is connected); rebooting should accomplish this. Also, I'm using xf86-input-wacom 0.10.8. I'm using
```
xsetwacom set "Serial Wacom Tablet Stylus" Screen_No -1
```
I don't fully understand this setting yet, though it doesn't appear to do anything.

I'm using xrandr to use an external monitor, so this may not work for those using the Nvidia or ATI proprietary drivers.

**Using xsetwacom**:
To start with, we're going to need to get some values using xinput. Read the output of
```
xinput list
```
and find the lines that correspond to your stylus and eraser (if you have one). For me, it's this:
> &#9116;   &#8627; Serial Wacom Tablet eraser              	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet stylus              	id=14	[slave  pointer  (2)]
Also notice the id for each device; this will make the commands a fair bit shorter. The device ids can change, so if you're going to write scripts to automate this, then you need to use the device names in quotes. Run the following commands:
```
xsetwacom get [device name/id] BottomX
xsetwacom get [device name/id] BottomY
```
the first value will be called **Wxsw(Left+Right)** and the second will be called **Hxsw(Large)** (these labels will make sense later). It's a good idea to record these somewhere. They appear to correspond to the resolution of the wacom digitizer, and better tablets will have larger values......I think.

**Example**:
```
~$ xsetwacom get "Serial Wacom Tablet stylus" BottomX
```
Returns the output:
> 24576
Of course the stylus only works by pointing it at the tablet screen, but we can easily control which screen the pointer appears on, and we'll scale it correctly so that pointing the stylus at the bottom right corner of the tablet screen will move the pointer to the bottom right corner of whichever screen we've chosen, regardless of the resolution. You'll generally use this only to restrict the stylus to the tablet screen, but I found it more clear to write this more generally since an external monitor can be on the right or the left.

**_Horizontal settings_**:
Using "Left" and "Right" to refer to our monitors only with regard to their xinput topology (that is, we don't care which is physically on the left, only which X thinks is on the left), we'll use the following notation:

**Wxsw(monitor)** = the width that xsetwacom seems to ascribe to the screen,
**Wact(monitor)** = the "actual" physical width in pixels of the screen.

These can also be used for the whole display, so **Wact(Left+Right)** is the sum of the physical widths of the two displays; in other words, it's the same as **Wact(Left)**+**Wact(Right)**. The number we found earlier for **Wxsw(Left+Right)** is how wide xsetwacom thinks the whole display is.

Now, for reasons unknown:

**Wxsw(Left)*****Wact(Left)** = **Wxsw(Right)*****Wact(Right)** = **Wxsw(Left+Right)*****Wact(Left+Right)**

In other words, the width ascribed to a screen by xsetwacom is inversely proportional to its physical width, with **constant of proportionality** equal to **Wxsw(-)*****Wact(-)** for any of the screens involved. Since we know **Wact(-)** for each of our screens, knowing **Wxsw(-)** for any one of them gives us a numerical value for the constant of proportionality and allows us to determine **Wxsw(-)** for each of the others. For example, if we know:

**Wxsw(Left+Right)** = 24576
**Wact(Left+Right)** = **Wact(Left)**+**Wact(Right)** = 1280+1024 = 2304
**Wact(Right)** = 1024

Then the **constant of proportionality** is:

**Wxsw(Left+Right)*****Wact(Left+Right)** = 24576*2304 = 56623104

and therefore:

**Wxsw(Right)** = **Wxsw(Left+Right)*****Wact(Left+Right)**/**Wact(Right)** = 56623104/1024 = 55296

so xsetwacom sees the Right display as being 55,296 units wide.

So how do we use this? Disconnect any external monitor and restart your computer to reset the xsetwacom values (simply restarting X may be enough). Use xrandr to connect the secondary display and check that the stylus is (incorrectly) mapped across both screens. Use
```
xsetwacom get [device name/id] BottomX
```
as detailed above to find **Wxsw(Left+Right)**. Use this number to find **Wxsw(Left)** and **Wxsw(Right)**.

Now, if you wish to map the stylus to the Left screen, use "xsetwacom set" to set the following values:

TopX = 0
BottomX = **Wxsw(Left)**

We set TopX = 0 since we want the stylus to abut the left edge of the whole display, and we set BottomX = **Wxsw(Left)** so that the stylus uses the proper width, that is we want:

BottomX-TopX = **Wxsw(Left)**

If you wish to map the stylus to the Right screen, use "xsetwacom set" to set the following values:

TopX = **Wxsw(Left+Right)**-**Wxsw(Right)**
BottomX = **Wxsw(Left+Right)**

We set BottomX = **Wxsw(Left+Right)** so the the stylus abuts the right edge of the display (remember that **Wxsw(Left+Right)** is the width that xsetwacom assigns to the whole display) and set TopX = **Wxsw(Left+Right)**-**Wxsw(Right)** so that the stylus uses the proper width, which is:

BottomX-TopX = **Wxsw(Left+Right)**-[**Wxsw(Left+Right)**-**Wxsw(Right)**] = **Wxsw(Right)**

To continue the earlier example, if I want to map my stylus to the Right screen only, then I use, with "Device name" or ID #:
```
xsetwacom set 14 TopX -30720
xsetwacom set 14 BottomX 24576
```
Yes, I use a negative value for TopX, which seems odd, but it works.

To recap:

1. Find **Wxsw(-)** for the default (wrong) setting.
2. Compute the **constant of proportionality**.
3. Find **Wxsw(Left)** or **Wxsw(Right)**.
4. Input values.

Unless you change the resolutions for your screens, you should only have to find the constant of proportionality once.

**_Vertical settings_**:

When you use xrandr to use a second monitor, the stylus should scale according to the larger screen, so if you intend to use the stylus with the larger screen, no changes are needed.

If you want to use the stylus with a screen which is the smaller of the two screens, then you'll want to adjust the vertical as well. All you should need to do is scale things. Let:

**Hact(Large)** = Larger screen height in pixels
**Hact(Small)** = Smaller screen height in pixels
**Hxsw(Large)** = height xsetwacom assigns to the larger screen
**Hxsw(Small)** = height xsetwacom assigns to the smaller screen

Again, these values are related by:

**Hact(Large)*****Hxsw(Large)** = **Hact(Small)*****Hxsw(Small)**

To get the value needed to restrict the stylus to the vertical region spanned by the smaller screen, obtain Hxsw(Large) using:
```
xsetwacom get [device name/id] BottomY
```
and set:

BottomY = **Hsxw(Small)** = **Hxsw(Large)*****Hact(Large)**/[B]Hact(Small)
[/B]
using the command:
```
xsetwacom set [device name/id] BottomY VALUE
```
For me, this is 18342*1024/768 = 24456, so:
```
xsetwacom set 14 BottomY 24456
```
sets my stylus to have the desired height range. Of course, I still have TopY = 0.

**_Eraser_**:

If you have an eraser on your stylus, don't forget to adjust the eraser as well. Use the same commands you used for the stylus but with the "Device name" or id for the eraser instead.

I hope this is clear enough.


**[SIZE="3"]Using the old xsetwacom Multi-monitor commands[/SIZE]**[SIZE="3"][COLOR="Blue"] - Pending[/COLOR][/SIZE]

You may benefit from using these versions of the Wacom drivers:
For **xf86-input-wacom **(X server 1.7 or up) use the snapshot from the 9-7-10 "Allow 0 for TwinView resolution if TwinView is NONE." commit:  [http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=snapshot;h=f968420695d72240ef6cb56febd195f8724b9f6e;sf=tgz](http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=snapshot;h=f968420695d72240ef6cb56febd195f8724b9f6e;sf=tgz)
The commit is at:  [http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=shortlog;pg=1](http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=shortlog;pg=1)  

For **linuxwacom** (X servers less that 1.7) use 0.8.8-10:  [http://sourceforge.net/projects/linuxwacom/files/linuxwacom/0.8.8-10/linuxwacom-0.8.8-10.tar.bz2/download](http://sourceforge.net/projects/linuxwacom/files/linuxwacom/0.8.8-10/linuxwacom-0.8.8-10.tar.bz2/download)


**Sources**:
Linux Wacom Project HOWTO "11.0 - Tablet-Screen Mapping":  [http://linuxwacom.sourceforge.net/index.php/howto/multimonitor](http://linuxwacom.sourceforge.net/index.php/howto/multimonitor)
LWP HOWTO "5.1 - Adding the InputDevices":  [http://linuxwacom.sourceforge.net/index.php/howto/inputdev](http://linuxwacom.sourceforge.net/index.php/howto/inputdev)
LWP HOWTO "9.0 - Command Line Configuration Interface (xsetwacom)":  [http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom](http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom)


**wacom.fdi version**:
These are the 3 basic lines you need:
```
          <merge key="input.x11_options.TwinView" type="string">Horizontal</merge>
          <merge key="input.x11_options.TVResolution" type="string">1440x900,1280x1024</merge>
          <merge key="input.x11_options.ScreenNo" type="string">0</merge>
```
Notice in TV resolution you have to specify both monitors.
* TwinView applies only to those using the Nvidia proprietary driver TwinView.

**xsetwacom version**:
```
xsetwacom set "Device name" Twinview Horizontal
xsetwacom set "Device name" Screen_No 1
xsetwacom set "Device name" TopX ??
xsetwacom set "Device name" BottomX ??
```

**xorg.conf version**:
```
Option  "Twinview"  "Horizontal"
Option  "Screen_No"  "1"
Option  "TopX"  "??"
Option  "BottomX"  "??"
```

---

### Post by SnickerSnack on 2010-12-31
Here is what I have using the old method: [http://ubuntuforums.org/showpost.php?p=10299356&postcount=33](http://ubuntuforums.org/showpost.php?p=10299356&postcount=33)

I believe that it is fairly complete (though I don't have 3 screens to test with).  If you think it belongs in this thread, you can of course either incorporate what I have or just link to my post.

---

### Post by Favux on 2010-12-31
Hi SnickerSnack,

Great!  Thanks.  I'll look at it.

I reserved the second post for the "old" method or alternative methods.  If I have the energy to comb through all the threads to figure it out.  It seemed like it was constantly changing and depended a lot on the video drivers.

---

### Post by Rumtscho on 2011-01-07
Favux, I find the idea behind this post great. But I am afraid that I don't have enough grasp of math and Linux tools to follow it through. Could you please provide a more thorough explanation for the points below? 

My case is not the simple one. 
[IMG]http://i.imgur.com/L5PNk.png[/IMG] 

First, I didn't understand how you arrived at the new matrices at all using the matrix multiplication and the linear equations. I looked up "affine transformation" on Wikipedia, thought about how they have to work in the simple case, and arrived at a method to calculate my own. I think that my matrices should be 

```

left:                                right:
[ 1280/(1280+2560)  0          0 ]   [ 2560/(1280+2560)  0          1280/(1280+2560)]
[ 0                 1024/1440  0 ]   [ 0                 1440/1440  0               ]
[ 0                 0          1 ]   [ 0                 0          1               ]

```

please correct me if I am wrong. 

When I have the (hopefully) correct matrices, you say to 

> use the appropriate xinput command for the monitor you want your device on:
Left monitor:
Code:

xinput set-prop "Device name" --type=float "Coordinate Transformation Matrix" 0.5 0 0 0 1 0 0 0 1



If I just type in 
```
xinput set-prop "Wacom BambooFun 2FG 6x8 Pen stylus" --type=float "Coordinate Transformation Matrix 0.333 0 0 0 1 0 0 0 1
```

how is xinput to know that this is meant for the left monitor? Am I missing something here?

---

### Post by Favux on 2011-01-07
Hi Rumtscho,

Great, first non-simple dual monitor case.  The diagram is very helpful, thanks.

Looks like you've done it correctly.  So now:

Left monitor:
```
xinput set-prop "Wacom BambooFun 2FG 6x8 Pen stylus" --type=float "Coordinate Transformation Matrix" 0.3333 0 0 0 .7111 0 0 0 1
```
Right monitor:
```
xinput set-prop "Wacom BambooFun 2FG 6x8 Pen stylus" --type=float "Coordinate Transformation Matrix" 0.6666 0 0.3333 0 1 0 0 0 1
```
And with your setup you shouldn't need a y offset for your left monitor.  Using your "Device names" of course.  And let's try 4 decimal accuracy.

---

### Post by Rumtscho on 2011-01-07
Thank you for the quick reply. I am happy to know that my matrix calculation was right. 

Using each of the lines you posted (my device name happens to be "Wacom BambooFun 2FG 6x8 Pen stylus" too) I was able to restrict the stylus to the desired area. 

I have trouble with the next step, the xsetwacom set line. Could you please explain a) what it is this command supposed to do? And b) how many times do I have to run it, once per monitor or only once, period? My xrandr only gives me a single identifier for the whole virtual monitor, and when I run the line with it, I get an "output not connected" error. Is this normal?

[COLOR="Gray"]
---
The detailed TL;DR version of the problem (questions still as above): 
---

This is how I understood your instructions.

1. calculate matrices, build matrix lines for each monitor. 

2. run the matrix line for the left monitor (the xinput -set-prop command). This confines the stylus input to the area on the virtual screen corresponding to the left monitor. 

3. find out the name of the left monitor by running xrandr 

4. run the mapping line for the left monitor (the xsetwacom set "Device name" "MapToOutput" VGA1 command). I looked into the Linux wacom project xsetwacom howto, but did not find a description of the MapToOutput option. My wild guess is that this binds the current input settings to the monitor specified as VGA1. 

5. run the matrix line for the right monitor

6. run the mapping line for the right monitor. 

Step 1 and 2 were OK. This is what I get at step 3: 
```

rumtscho@bradbury:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 3840 x 1440, current 3840 x 1440, maximum 3840 x 1440
default connected 3840x1440+0+0 0mm x 0mm
   3840x1440      50.0* 

```

I was expecting two names from xrandr, one for the left monitor and one for the right monitor. If I have understood it correctly, running steps 4 and 6 with the same monitor name is nonsence. 

Of course, this sequence depends on my interpretation of step 4. Maybe it does something else than what I thought, it is correct for xrandr to provide the name of a single virtual screen, the correct sequence is 1-2-3-5-4 and I should use the single output of xrandr instead of VGA1. 

I tested this possibility and ran step 4 as ```
xsetwacom set "Wacom BambooFun 2FG 6x8 Pen stylus" "MapToOutput" Screen\ 0
```
and got in response ```
Unable to find output 'Screen 0'. Output may not be connected.
```

This confused me thoroughly. I opened xorg.conf to see how the screens are called there. This are the relevant parts of my xorg.conf (colour added manually): 
```

Section "Monitor"
    [COLOR="RoyalBlue"]Identifier     "Monitor0"[/COLOR]
    VendorName     "Unknown"
    [COLOR="RoyalBlue"]ModelName      "CRT-1"[/COLOR]
    HorizSync       63.0 - 67.0
    VertRefresh     58.0 - 62.0
    Option         "DPMS"
EndSection

Section "Screen"

    [COLOR="RoyalBlue"]Identifier     "Screen0"[/COLOR]
    Device         "Device0"
    [COLOR="RoyalBlue"]Monitor        "Monitor0"[/COLOR]
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes"[COLOR="RoyalBlue"] "CRT: 1280x1024 +0+0, DFP: nvidia-auto-select +1280+0"[/COLOR]
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

There is no monitor section for the Dell. Besides, the CRT part is wrong, because the small monitor is an LCD. It never gets recognized correctly under Linux. 

Anyway, I tried running the command from step 4, using following identifiers instead of VGA1: Monitor0, CRT-1, Screen0, CRT, DFP. All produced the same "device not found" output as Screen 0.[/COLOR]

---

### Post by Rumtscho on 2011-01-07
I needed a long time to understand how to calculate a matrix for my case, but it is actually quite simple. I am posting a description for anybody who needs it. Favux, you can link it from the first post or copy it there if you think it is useful. 

This description can be applied for any monitor in any case, simple or complicated. It does not depend on the number of monitors you might have. 

This matrix is calculated once for every monitor. 
[B]
Monitor width[/B] is the horizontal resolution of the monitor. 

**Monitor height** is the vertical resolution of the monitor. 

**Total width** is the horizontal size of the combined area of all your monitors. 

**Total height** is the vertical size of the combined area of all your monitors. 

**Horizontal offset** is the horizontal distance between the upper left corner of the combined area of all monitors and the upper left corner of the monitor. 

**Vertical offset** is the vertical distance between the upper left corner of the combined area of all monitors and the upper left corner of the monitor. 

**Relative horizontal size** = monitor width / total width 

**Relative vertical size** = monitor height / total height 

**Relative horizontal offset** = horizontal offset / total width 

**Relative vertical offset **= vertical offset / total height 

Matrix: 
[IMG]http://i.imgur.com/xOshS.png[/IMG]

Example (screenshot taken from the GUI of the proprietary nvidia driver): 

[IMG]http://i.imgur.com/kFW7I.png[/IMG]

Matrix for this example (for the righthand monitor): 
```
0.6666  0      0.3333
0       1      0     
0       0      1
```

---

### Post by SnickerSnack on 2011-01-07
Eh, nevermind me.  I misunderstood your problem.

---

### Post by Favux on 2011-01-08
Hi Rumtscho,

First thank you for your contributions to the thread.

Could you answer some questions for me?
> Using each of the lines you posted (my device name happens to be "Wacom BambooFun 2FG 6x8 Pen stylus" too) I was able to restrict the stylus to the desired area.
So you didn't need the xsetwacom command?  The xinput command restricted your stylus to the monitor you selected without it?
Were you able to use 4 decimal accuracy?
Does the new transformation matrix from xinput last through a reboot?
Or do you need to implement it after each reboot?

On the whole I'd say your explanation is a lot more lucid (pun intended) than my original one.  Love the diagram.  We will need to work it and your explanation into the HOW TO.  However:
> **Total height** is the vertical size of the combined area of all your monitors. 
I don't believe that is correct.  I think it would be correct if the monitors were stacked not side by side.  In the side by side configuration I believe it is:
> **Total height** is the vertical size of the largest monitor.
So if the monitors are stacked then:
> **Total width** is the horizontal size of the largest of all your monitors.
How you handle X & Y reverses in the stacked case.  I think xrandr allows you to do that with the --above and --below switches.

SnickerSnack and I have been working on the "old" way of doing it and I think SnickerSnack has it figured out now.  Albeit with some things still being mysterious.  So I'll need to include it in the HOW TO also.  Meanwhile he points out 'man xrandr' also has an explanation of the transformation matrix.

I've already revised the HOW TO a little.  Is it clearer?

---

### Post by Rumtscho on 2011-01-10
Hi Favux, 

first some answers. 
> So you didn't need the xsetwacom command? The xinput command restricted your stylus to the monitor you selected without it?
Yes to both. 

Long explanation what I understand under "restricted to the screen" (maybe the xsetwacom command is needed to achieve some other effect?): When I type > xinput set-prop "Wacom BambooFun 2FG 6x8 Pen stylus" --type=float "Coordinate Transformation Matrix" 0.3333 0 0 0 .7111 0 0 0 1
the stylus is mapped to the left screen. I.e., when the stylus is put to the middle of the tablet, the pointer appears at the middle of the tablet. When the stylus is put to the righthand border of the tablet, the pointer stays at the righthand border of the left monitor. The same for all other monitor borders. The mapping is consistent, the pointer movement over the 16:9 area of the tablet is stretched to match the 5:4 area of the left monitor. The experience is at it should be, left and right mouse buttons interact as expected with the pixel under the pointer. Moving the cursor to the other monitor is possible by using another input device (including touch on the Wacom tablet), but when the stylus is put close to the tablet, the pointer jumps to the corresponding point on the screen. Running the line for the right monitor functions in the same way as for the right, when the "right monitor" line is used. 

This description applies to the stylus input, which for me is set to respond to the absolute position of the stylus tool over the tablet. I tried running the line for the Finger touch input, which moves the mouse relative to the current pointer position. This tool does not get confined to a single monitor. Running the "right monitor line" for it results in the pointer behaving as expected on the visible parts of both screens, but the pointer doesn't stop its movement on the righthand and lower edges of the righthand monitor, disappearing across the border when the finger is drawn in these directions. 

> Were you able to use 4 decimal accuracy?
I think yes. I typed the command as shown in the answer above, with the 4 decimal accuracy. The command produced no output at all, no error codes or warnings, but the command functioned as described. However, I don't know if xinput is actually using my transformational matrix with the 4 decimal accuracy, or if it is doing some internal rounding. I don't know of a way to test that, if you do, I can do it and give you the results. 

> Does the new transformation matrix from xinput last through a reboot?
No, it doesn't. I need to do it again after reboot, or to use the startup script. 

And something about my description post. I probably wasn't clear enough when describing the intent of my contribution. I didn't mean it as a thorough explanation of my own case, but as a guide for any possible case, which should cover the wildest monitor configurations, with my case thrown in as an illustration (because I did not have the resources to make screenshots of more complicated configurations :)). This is why I chose a phrasing which is consistent with both multiple stacked and adjacent monitors and the special case of only two monitors in a row. 

I realise that this hasn't been tested in a more general case, but I think we can assume that the transformation matrix will always behave according to the theory behind affine transformations, so we can use my explanation safely enough as a general how-to on calculating a transformational matrix. I think that such a generic explanation is needed beside the common simple cases, because each complex case is bound to differ from most other complex cases, and making a case-based guide for complex cases would lead to a very voluminous and difficult-to-read guide. This is why I prefer to keep the information in my post as it is. If you want to include a description of my case in your original post, feel free to do it any way you want, as long it produces the correct results. 

As for the edit of your original explanation, I think that the new wording definitely makes it more clear and easier to follow. Cheers! ;-)

---

### Post by Favux on 2011-01-10
Hi Rumtscho,

> Yes to both.
Excellent.  The two things I was looking into were how to use "MapToOutput" and how to accomplish the same thing with other tablets like the Aiptek's and Genius (WizardPen) tablets.  It's looking like I stumbled onto a way for both.
> This description applies to the stylus input, which for me is set to respond to the absolute position of the stylus tool over the tablet. I tried running the line for the Finger touch input, which moves the mouse relative to the current pointer position. This tool does not get confined to a single monitor. Running the "right monitor line" for it results in the pointer behaving as expected on the visible parts of both screens, but the pointer doesn't stop its movement on the righthand and lower edges of the righthand monitor, disappearing across the border when the finger is drawn in these directions. 
I'm guessing this is because you have your touch set to Relative rather than Absolute like the stylus and eraser.  The default setting or an xsetwacom script?  You can check with:
```
xsetwacom get "Wacom BambooFun 2FG 6x8 Pen stylus" Touch Mode
```
You could try changing it to Absolute with the set command.  On a tablet pc anyway touch is Absolute.
> I think yes. I typed the command as shown in the answer above, with the 4 decimal accuracy.
I think we'll go ahead and assume it works.  You aren't having any issues with pointer placement location at the monitor borders it sounds like, so we're good with 4 digits.
> No, it doesn't. I need to do it again after reboot, or to use the startup script. 
Can just put the xinput line in the xsetwacom start up script then.
> And something about my description post. I probably wasn't clear enough when describing the intent of my contribution. I didn't mean it as a thorough explanation of my own case, but as a guide for any possible case, which should cover the wildest monitor configurations, with my case thrown in as an illustration (because I did not have the resources to make screenshots of more complicated configurations ). This is why I chose a phrasing which is consistent with both multiple stacked and adjacent monitors and the special case of only two monitors in a row. 
I understood you were describing the general case and I will at least point to your post.


Now onto "**MapToOutput**".  It appears it was broken, at least for 64-bit installs, see:  [http://sourceforge.net/mailarchive/forum.php?thread_name=20110110024713.GA501%40barra.bne.redhat.com&forum_name=linuxwacom-devel](http://sourceforge.net/mailarchive/forum.php?thread_name=20110110024713.GA501%40barra.bne.redhat.com&forum_name=linuxwacom-devel)  Hopefully this patch fixes it.  Peter's looking for some testers before he commits the patch to the xf86-input-wacom git repository.

And it is suppose to work the way I originally thought.  You just use the xsetwacom command and specify the monitor you want and your device is suppose to be there.  No need to figure out the matrix.  So that should be the preferred way for Wacom tablets.  In fact, if what I gathered from him is correct, he had thought the xinput command wouldn't work for Wacom!

The developer has his tablet on his laptop and it is hooked up to an external monitor, hence his example of:
```
xsetwacom set <device name> "MapToOutput" VGA1 
```
And his external monitor shows up in xrandr (I think) as VGA1.

My current guess is that he set up the monitor through xrandr, which is why he's seeing it.  This makes sense since he is a Red Hat developer.  However others (including you) using the proprietary Nvidia or ATI configuration gui's aren't able to query xrandr for the target monitor description.  I see this as a problem for "MapToMonitor" because I believe the vast majority of people with multiple monitor setups are using the proprietary drivers and not Intel motherboard video chipsets with strictly open source set ups.  Does this make sense?

---

### Post by Rumtscho on 2011-01-11
> Peter's looking for some testers before he commits the patch to the xf86-input-wacom git repository

I would be glad to test it. I have been using open source for years, I feel like I should start giving something back to the community. There are however some difficulties: 1) I don't know how (I don't even know where to get a version which is not yet in the repository) and 2) I need the proprietary driver on my home PC. If the MapToOutput option only works with an open source driver and a xrandr multimonitor setup, I'll have to think of something (probably deinstall the proprietary driver from the Ubuntu installation on the laptop, which will take time, as I usually don't take the laptop home on weekdays). 

But if you could give me a short explanation how to solve 1), I'll give my best to help.

---

### Post by Favux on 2011-01-11
Hi Rumtscho,

The link I gave you above points to the linuxwacom-devel post that has the patch at the top of the post.  Just click on the patch link and download it onto your Desktop.  Then clone the git and go into the xf86-input-folder and run the patch command.  Pointing to wherever you put the patch.  Probably with the p1 switch, depending on the directory level you're at.

I'm sure you'll first try with the proprietary driver in place, because that would be great if you could get "MapToOutput" working with it and explain it to us.

Unfortunately touch is broken currently but we've bisected the commits and think we've located the problem-some ones.  Chris is working on that.

---

### Post by Rumtscho on 2011-01-12
Hi Favux, 

I wanted to try the patch out. However, I reasoned that an option called "MapToOutput" only makes any sense if there is more than one output on the system. As I posted above, in my current settings, xRandR only recognizes a single output of the size 3840x1440, so mapping the stylus to it wouldn't be any use. 

Actually, I tried the option out just to see what happens (with the xsetwacom version I currently have, from the xf86-input I installed three days ago from git). The pointer got moved to the pixel in the upper left corner of the left monitor and could not be moved away with the stylus. Moving away with another input device worked, but when the tablet sensed the stylus, it (the pointer) got "captured" again. This could be due to the non-standard behaviour of xRandR resp. its bad cooperation with the video driver. 

I switched TwinView off and spent the evening rewriting xorg.conf in an attempt to get two xRandR-managed outputs. It turns out that this is not possible due to limitations of the proprietary nvidia driver: [http://ubuntuforums.org/showthread.php?t=1283640](http://ubuntuforums.org/showthread.php?t=1283640). I will have to take the laptop home, set it up with the nouveau driver and try again. 

On the mailing list there was some talk of bugs on 64 bit systems. Is that what you wanted me to test, or would a test on a 32 bit do? I think I have a 32 bit on the laptop. If needed, I can reinstall a 64 bit, I barely use Ubuntu on the laptop so it isn't customized there.

---

### Post by Favux on 2011-01-12
Hi Rumtscho,

Thank you for your testing.

Peter was confident enough of the 64-bit fix to commit it to the git repository last night.  So if the laptop is 32-bit go ahead and use your current xf86-input-wacom or clone the git again if you'd like.  This thread or LWP will get reports if the 64-bit fix doesn't work, I'm sure.

I've got the "MapToOutput" instructions set up as I understand them currently.  So I'd love confirmation that it works.

I'm almost certain now from what you're saying that it won't work with the proprietary drivers setting up the monitors.  Or apparently trying to use xrandr rather than the proprietary configuration gui to set up the monitors while on the proprietary drivers.  I guess I want a little more confirmation, including someone using the ATI proprietary before I go ahead and add that limitation/restriction to the HOW TO.

---

### Post by lejono on 2011-01-24
I really like the "Coordinate Transformation Matrix" option.  But what do I do if my tablet screen is inverted?  I have two screens, and my tablet is on the right.  So when it's in laptop mode I have: 

xinput set-prop "Serial Wacom Tablet stylus"  --type=float "Coordinate Transformation Matrix" 0.4444 0 0.5556 0 .6667 0 0 0 1

But when I'm in tablet mode (I.e. my screen is upside down), then I need to flip the coordinates through the origin.

This seems to do the trick but I don't completely understand why: 
xinput set-prop "Serial Wacom Tablet stylus"  --type=float "Coordinate Transformation Matrix" -0.4444 0 1 0 -.6667 .6667 0 0 1

but it isn't perfect (a few millimeters off).  Not sure how to calibrate better.  Also, I'm not sure why the value of 1 is needed for the X offset.  

Thanks for any help!

Jonathan

---

### Post by Favux on 2011-01-24
Hi Jonathan,

Welcome to Ubuntu forums!

Trying to stretch my mind are you?  Going right for a complicated case...

Since you are adding a rotional transformation let's use rotation by an angle A counter-clockwise about the origin.  The functional form would be x' = xcosA &#8722; ysinA and y' = xsinA + ycosA but we want to make it affine so we can use multiplication.  And we need to add it to the current matrix.  So written in matrix form, it becomes something like:
```
[ x' ]   [ cosA*c0 -sinA*c1 c2 ]   [ x ]
[ y' ] = [ sinA*c3  cosA*c4 c5 ] * [ y ]
[ 1  ]   [ c6       c7      c8 ]   [ 1 ]
```
representing the equations:
```
x' = (cosA*c0x + -sinA*c1y + c2) / w'
y' = (sinA*c3x +  cosA*c4y + c5) / w'
w' = (c6x      +  c7y      + c8) = 1
```
Correct?  You're rotating the tablet 180 degrees to inverted I think.  Now since cos(180) = -1 and sin(180) = 0 you end up with:
```
-0.4444  0      1
 0      -0.6667 0.6667
 0       0      1
```
Do you have any thoughts now on the offset?
> but it isn't perfect (a few millimeters off). Not sure how to calibrate better.
Well notice the default returns 6 decimal accuracy and so far we've shown 4 digits works.  So try 5 and 6 and see if that improves your calibration.  And let me know so I can add it to the HOW TO!

---

### Post by lejono on 2011-01-26
Thanks!  And that also works for portrait orientations, so very cool.

It's still a few mm off, but it seems that that's an overall calibration issue, rather than an issue with the rotation.

---

### Post by Favux on 2011-01-26
Great!  Could you post the resolutions of the monitor and the tablet pc so I can add it as an example to the HOW TO?  What x & y offsets, i.e. matrix commands, did you use for portrait?  Thanks.

---

### Post by lejono on 2011-01-31
Thanks Favus for putting it up.  My desktop monitor is 1600x1200 and my tablet is 1280x800 and located to the right.  I've attached a screenshot of the geometry I use for inverted and portrait. 

So,if I want a portrait orientation, we have sinA = -1 and cosA==0

This gives

xinput set-prop "Serial Wacom Tablet stylus"  --type=float "Coordinate Transformation Matrix" 0 .33334 .66667 -1 0 1 0 0 1

Note that here, to determine the offset and scaling in the horizontal direction, you have to use the X resolution of the desktop display and the Y resolution of the tablet.  So, the X-offset is 1600/(1600+800)
and the X-scaling is 800/(1600+800).

For inverted, see the three previous posts.

There does however seem to be some issues with the above configuration, so not sure I have it right.  For example, Xournal with Xinput and the gnome panel seems to be using a different set of coordinates.  So, if I click on the gnome panel, it interprets the click as coming from a place which is different to where the mouse pointer is.  Likewise, Xournal works fine if I unclick the Xinput option, but if I leave the Xinput option checked, then the mouse is interpreted as being somewhere other than where the pointer is.

---

### Post by Favux on 2011-01-31
Hi lejono,

Thank you for the additional information.  I think I need to process it for a bit.  Do you mind going over what you've posted, esp. in terms of the xinput matrix commands, and confirm them?
> Likewise, Xournal works fine if I unclick the Xinput option, but if I leave the Xinput option checked, then the mouse is interpreted as being somewhere other than where the pointer is. 
This is ringing a dim bell somewhere but I can't pull it up right now.

How bad is the offset?  Is it consistent in one direction?  Along the X or Y axis?

---

### Post by Favux on 2011-02-05
Hi lejono,

I finally put up all your stuff, i.e. portrait too.  Please check it over and make sure I got it right.

---

### Post by Ambush Commander on 2011-02-17
Hey all, I was thinking of writing a script that does the maths automatically for this. Has anyone tried this yet?

---

### Post by Favux on 2011-02-17
Hi Ambush Commander,

Sounds like a good idea.  I don't think I've seen anybody do a script for this stuff yet.  Just the C code in xsetwacom.c for the "MaptoOutput" parameter.

---

### Post by mpw on 2011-07-08
Great Howto, thank you very much!

---

### Post by Reason NL on 2011-08-05
For what it's worth, I had some trouble getting the aspect of the tablet right and because I use nVidia the multiple monitor config isn't really an issue for me because of twinview, but the aspect ratio is. I have a combined resolution of 3840x1200 and a A5 sized Wacom tablet.
Since the provided aspect option doesn't seem to work properly I decided to make a shell script to resize the sensitive area of the tablet to match the screen resolution based on width and height of both devices.
Hope it's gonna be useful to others..

```

#!/bin/bash

# Config active tablet area position
positionX=center    #left, center, right
positionY=top         #top, center, left

# Start script
precision=10000
resolution=`/usr/bin/xrandr -q | grep "connected [0-9]\+x[0-9]\+" -o | tr -d "connected "`
resX=`echo $resolution | grep "^[0-9]\+" -o`
resY=`echo $resolution | grep "[0-9]\+$" -o`
resRatio=$(((resX*precision)/resY))
echo Wacom Aspectratio script 0.1 \(ReasonNL\)
echo ""
echo Trying to match aspect ratio of $resolution to the tablet
echo Positioning area on horizontal $positionX and vertical $positionY
echo ""
xsetwacom --list | while read line; do
    device=`echo $line | grep "id: [0-9]\+" -o | tr -d "id: "`
    xsetwacom set "$device" ResetArea 1
    area=`xsetwacom get "$device" Area | grep "[0-9]\+ [0-9]\+$" -o`
    areaX=`echo $area | grep "^[0-9]\+" -o`
    areaY=`echo $area | grep "[0-9]\+$" -o`
    if [ "$areaX" != "" -a "$areaY" != "" ]; then
        if [ $resRatio -gt $precision ]; then
            newAreaX=$areaX
            newAreaY=$(( (areaX*precision)/resRatio ))
        elif [ $resRatio -lt $precision ]; then
            newAreaX=$(( (areaY*resRatio)/precision ))
            newAreaY=$areaY
        else
            if [ $areaX -gt $areaY ]; then
                newAreaX=$areaY
                newAreaY=$areaY
            else 
                newAreaX=$areaX
                newAreaY=$areaX
            fi
        fi
        newTop=0
        newLeft=0
        if [ $areaX -gt $newAreaX ]; then
            if [[ $positionX == center ]]; then
                newLeft=$(( (areaX-newAreaX)/2 ))
            elif [[ $positionX == right ]]; then
                newLeft=$(( areaX-newAreaX ))
            fi
            newAreaX=$((newAreaX+newLeft))
        fi
        if [ $areaY -gt $newAreaY ]; then
            if [[ $positionY == center ]]; then
                newTop=$(( (areaY-newAreaY)/2 ))
            elif [[ $positionY == bottom ]]; then
                newTop=$(( areaY-newAreaY ))
            fi
            newAreaY=$((newAreaY+newTop))
        fi
        xsetwacom set "$device" Area "$newLeft $newTop $newAreaX $newAreaY"
        echo Area of $line set to `xsetwacom get "$device" Area`
    else
        echo $line doesn\'t have an area
    fi
done

```

---

### Post by mpw on 2012-01-29
Hello,

this is a really gread thread.

Is there a way to transfer the command e.g.

```

xinput set-prop "WALTOP International Corp. Slim Tablet stylus" --type=float "Coordinate Transformation Matrix" 0.5 0 0.5 0 1 0 0 0 1

```

into an xorg.conf.d file? So that I can place it in /usr/share/X11/xorg.conf.d/ and set the options automatically?

Bye
MPW

---

### Post by Favux on 2012-01-29
Hi mpw,

Glad you like it.  :)
> Is there a way to transfer the command into an xorg.conf.d file? So that I can place it in /usr/share/X11/xorg.conf.d/ and set the options automatically?
Not that I'm aware of.  Xinput requires that X is running.  The same is true of the xsetwacom MapToOutput parameter.

---

### Post by Dimitree on 2012-02-09
Hey guys!
I just went trough the nightmare of calculating this stuff for my two monitors.
Since I'm a lazy person I though I would help a fellow lazy person out :)
In the attachment is a LibreOffice Calc file (Excel) where you can input the resolution of your monitors and it will give you the values in the order needed for your case.
This is only for two monitors with no rotations and so on...
Feel free to expand on it :) like i said I'm lazy ^-^v
Take care!

---

### Post by Falcata on 2012-03-16
I've got a wizardpen tablet (UC-LOGIC Tablet WP8060U) and an nVidia TwinView setup, which I was trying to get to work using these instructions.  I was able to get it to map output to the primary screen, but now I'm getting an issue where, for a frame or two, the cursor will suddenly jump to the left side of the screen and back, which messes up my drawings.  These occurs randomly, and at worst it happens several times per second.

I tried these instructions, but without any luck:
[https://help.ubuntu.com/community/TabletSetupWizardpen#Clicking_does_weird_things_or_the_cursor_jumps](https://help.ubuntu.com/community/TabletSetupWizardpen#Clicking_does_weird_things_or_the_cursor_jumps)

And a friend of mine was having this same issue as well.  Can anyone help me figure out what's going on?


This is my xorg.conf file:
```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 285.05.09  (buildmeister@swio-display-x86-rhel47-02.nvidia.com)  Fri Sep 23 17:55:42 PDT 2011


Section "ServerLayout"

# Removed Option "Xinerama" "0"
# Removed Option "Xinerama" "1"
# Removed Option "Xinerama" "0"
# Removed Option "Xinerama" "1"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" 3360 56
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "evdev"
    Option         "Device" "/dev/input/by-id/usb-Logitech_Gaming_Mouse_G400-event-mouse"
    Option         "Protocol" "auto"
#    Option         "Device" "/dev/psaux"
#    Option         "Emulate3Buttons" "no"
#    Option         "ZAxisMapping" "4 5"
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
    ModelName      "Ancor Communications Inc ASUS VH242H"
    HorizSync       30.0 - 85.0
    VertRefresh     55.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "DELL E171FPb"
    HorizSync       31.0 - 80.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 460"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 460"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"

# Removed Option "TwinViewXineramaInfoOrder" "DFP-0"
# Removed Option "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-2: nvidia-auto-select +1920+180"
# Removed Option "metamodes" "DFP-2: nvidia-auto-select +1920+180, DFP-1: nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-1"
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0, DFP-2: nvidia-auto-select +1920+180"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"

# Removed Option "metamodes" "CRT: nvidia-auto-select +0+0"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: 1280x1024 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Disable"
EndSection

```


And my xorg.conf.d/10-evdev.conf file:
```
#
# Catch-all evdev loader for udev-based systems
# We don't simply match on any device since that also adds accelerometers
# and other devices that we don't really want to use. The list below
# matches everything but joysticks.

#Section "InputClass"
#        Identifier "evdev pointer catchall"
#        MatchIsPointer "on"
#        MatchDevicePath "/dev/input/event*"
#        Driver "evdev"
#EndSection

Section "InputClass"
        Identifier "evdev keyboard catchall"
        MatchIsKeyboard "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev touchpad catchall"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev tablet catchall"
        MatchIsTablet "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev touchscreen catchall"
        MatchIsTouchscreen "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection
```

In the evdev.conf file I had to comment out the "evdev pointer catchall" section and manually configure my mouse in the xorg.conf in order to get my tablet to only register with one entry in xinput, but the problem still persists.

Also, I'm on Arch Linux and not Ubuntu.  I'm posting here because I couldn't find anything helpful on the Arch Linux forums.

Any help with this will be appreciated.

---

### Post by Favux on 2012-03-16
Hi Falcata,

What's your kernel and X Server?  Post the ouput of:
```
Xorg -version
```
Also what version of evdev do you have?

The cursor jump to the left edge indicates that the X coordinate is lost and it is going to 0.  If it went to the top left corner then both X and Y are being lost and it is going to 0,0.

Am I correct that you are using the evdev driver for the tablet and not the WizardPen driver?

I wouldn't do the mouse or keyboard in the xorg.conf.  I'd let them be handled automatically.  I need to know more about the duplicate tablet xinput entry.  Same <device name> but two separate input nodes?

---

### Post by Falcata on 2012-03-16
Here's the output of Xorg -version:

$ Xorg -version

X.Org X Server 1.12.0
Release Date: 2012-03-04
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.2.9-1-ARCH x86_64 
Current Operating System: Linux myhost 3.2.11-1-ck #1 SMP PREEMPT Tue Mar 13 17:27:16 EDT 2012 x86_64
Kernel command line: root=/dev/disk/by-uuid/bf44433a-f2df-48b8-8e7b-1f01f7fbc0fb ro elevator=bfq
Build Date: 05 March 2012  05:59:48AM
 
Current version of pixman: 0.24.4

And the driver versions I have installed are evdev 2.7.0 and version 0.14.0 of wacom.

As far as drivers, the tablet is using the hid_uclogic driver.  I had attempted to use the wizardpen driver, but the AUR package for it seemingly didn't have any driver included with it, so I couldn't do anything with it.

In the 10-evdev.conf file, both the "evdev pointer catchall" and the "evdev tablet catchall" parts were each generating a single device, with *pointer generating one that didn't appear to function.

With two devices, I would get output like this in xinput:
```
$ xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Mouse0                                  	id=6	[slave  pointer  (2)]
&#9116;   &#8627; UC-LOGIC Tablet WP8060U                 	id=11	[slave  pointer  (2)]
```

And there are in fact two devices being detected by the system, and I'm not sure why:
```
ls /dev/input/by-id/
usb-046d_09a1_70277320-event-if00
usb-0d8c_C-Media_USB_Headphone_Set-event-if03
usb-Logitech_Gaming_Mouse_G400-event-mouse
usb-Logitech_Gaming_Mouse_G400-mouse
usb-Logitech_USB_Multimedia_Keyboard-event-if01
usb-Logitech_USB_Multimedia_Keyboard-event-kbd
usb-UC-LOGIC_Tablet_WP8060U-event-mouse
usb-UC-LOGIC_Tablet_WP8060U-mouse
```

My guess is the extra device is for handling pressure or something, and based on my prior testing, the 1st of those two, *event-mouse, is the one that controls the cursor.

---

### Post by Favux on 2012-03-16
Alright.  kernel 3.2.11-1 x86_64  X Server 1.12.0  evdev 2.7.0
> I had attempted to use the wizardpen driver, but the AUR package for it seemingly didn't have any driver included with it, so I couldn't do anything with it.
Correct, starting with evdev 2.5.99 the evdev driver is the preferred X driver.  WizardPen is no more.

To get Vendor ID and Product ID enter:
```
lsusb
```
and post the tablet line.  But clearly it is the WP8060U so the PID should be 0005.  The tablet/stylus <device name> appears to be from:
```
&#9116;   &#8627; UC-LOGIC Tablet WP8060U                 	id=11	[slave  pointer  (2)]
```
<UC-LOGIC Tablet WP8060U>.

No sure why out of:
```
usb-UC-LOGIC_Tablet_WP8060U-event-mouse
usb-UC-LOGIC_Tablet_WP8060U-mouse
```
that:
```
usb-UC-LOGIC_Tablet_WP8060U-event-mouse
```
is the stylus.  But from the "[Tablet support status]("http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status")" page when I click on through using the name to the individual tablet page it is clearly shown the tablet can come with a mouse.  So that is presumably why the kernel is supplying two input nodes.  Your tablet must not come with the mouse.  We could ask Nick about the name though, because it is confusing.  First time I've seen that output so thanks.

The DIGI*mend* media wiki just went live:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=DIGImend](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=DIGImend)  And we are still working on it.

Anyway from what I see your tablet should work out of the box with pressure.

So let's try to set things back to the "original state".  Just the video stuff in the xorg.conf and see where you are.

An initial thought is if you have the tablet plugged into a usb hub maybe plug it directly in.  Make sure the connection is firm and well seated on both ends.  You could be seeing interruptions due to power or connection problems.  When that happens and the pointer goes to the left is there anything in Xorg.0.log in /var/log?

---

### Post by Falcata on 2012-03-16
No errors in Xorg.0.log, and I've got my xorg and 10-evdev configuration files set back to the way they were before I started modifying them.  I don't see any errors in Xorg, and I'm not sure that the power is the issue, because the problem only starts after running xsetwacom to map the tablet input to the primary monitor.

And here's the output:

```
$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 413c:5115 Dell Computer Corp. Photo AIO Printer 926
Bus 001 Device 004: ID 05e1:0408 Syntek Semiconductor Co., Ltd STK1160 Video Capture Device
Bus 003 Device 002: ID 046d:c317 Logitech, Inc. Wave Corded Keyboard
Bus 002 Device 002: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 002 Device 003: ID 1a40:0101 TERMINUS TECHNOLOGY INC. USB-2.0 4-Port HUB
Bus 004 Device 002: ID 5543:0005 UC-Logic Technology Corp. Tablet WP8060U
Bus 002 Device 004: ID 046d:c245 Logitech, Inc. 
Bus 002 Device 005: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102 Flash Drive / HEMA Flash Drive 2 GB / PNY Attache 4GB Stick
Bus 002 Device 006: ID 046d:09a1 Logitech, Inc. QuickCam Communicate MP/S5500
Bus 002 Device 007: ID 0d8c:000c C-Media Electronics, Inc. Audio Adapter
```

---

### Post by Favux on 2012-03-16
OK, we have the correct PID, good.
```
Bus 004 Device 002: ID 5543:0005 UC-Logic Technology Corp. Tablet WP8060U
```
You've lost me with:
> I don't see any errors in Xorg, and I'm not sure that the power is the issue, because the problem only starts after running xsetwacom to map the tablet input to the primary monitor.
Did you mean xinput not xsetwacom for the CTM command?

---

### Post by Falcata on 2012-03-16
Oh, no, not that.  The double entries happens without the modifications, but they may not be the issue.

The problem with the jumping only starts after I run this:

xsetwacom set "device name" MapToOutput HEAD-0

---

### Post by Favux on 2012-03-16
Ahhh.  Well the xsetwacom MapToOutput parameter only works if you have your tablet on the Wacom X driver.  The Wacom X driver does not support UC-Logic tablets currently, only the evdev driver does.  Did you do a match to the Wacom driver in xorg.conf.d somewhere?

For your tablet you have to use a xinput CTM command, i.e.:
```
xinput set-prop "UC-LOGIC Tablet WP8060U" --type=float "Coordinate Transformation Matrix" 0.5 0 0.5 0 1 0 0 0 1
```
or whatever the matrix you need is.

---

### Post by Falcata on 2012-03-16
Was hoping I'd be able to avoid using those things, but I'll give them a shot.

---

### Post by Favux on 2012-03-16
I'm interested in hearing how it works for you.  Let me know if you need any help calculating the ratios.

---

### Post by Falcata on 2012-03-16
Okay, just now getting to this, and it turns out that it *is* using the evdev driver.  I don't know if this'll change anything, but I'll see.

---

### Post by Falcata on 2012-03-16
This still isn't working.  I've got the xinput commands correctly set, but it is still jumping off to the right-hand side.

This is both with the doubled entries and with them disabled by the custom xorg and evdev configurations, and in all cases the tablet starts having this 'jumping' problem after making any attempt to set its properties.

So, I'm guessing that it's something else that's the problem.  Any ideas or suggestions?

EDIT: This is a demonstration of attempting to draw a relatively straight vertical line in inkscape:

[IMG]https://lh4.googleusercontent.com/-uzqvoPIhJEU/T2QEt1hA6GI/AAAAAAAACJo/RwIm_4jAoLg/s642/AttemptedStraightLine.png[/IMG]

---

### Post by Favux on 2012-03-16
Good, nice job on the CTM.

By any chance is this happening in Gimp?  If so does it happen in another program like MyPaint?  And is that Gimp 2.6 or 2.7?

---

### Post by Falcata on 2012-03-16
This happens with everything: any app I use, or none at all.  I get it on a blank desktop.

EDIT: Also, something I forgot to mention is that this gets progressively worse over time.

---

### Post by Falcata on 2012-03-18
So, any ideas?

Or would it work if I created a fake monitor entry and used the tablet with my craptop as a thin client to log into my main system and used this fake monitor through VNC?

---

### Post by Favux on 2012-03-18
Sorry I missed your post yesterday.  Nope, no helpful ideas.

The jumping as I mentioned clearly shows that the stylus coordinates are being messed with by something.  If I understood you correctly the stylus works OK when on the combined Desktop?  It's only when you attempt to confine it to one monitor it occurs.

It is looking like there is a X Server bug.  Or a bug in how evdev interacts with the X Server in a multi-monitor setup.  Because you are seeing it in everything.  I'm guessing if you just use one monitor you don't see the bug either?

Unlike Wacom I don't know how to turn debugging on with evdev.  The evdev manual doesn't say anything about a debugging command.

Since I think the tablet worked with the CTM with X Server 1.10 and evdev 2.6 the bug was introduced recently.  At least no one with Oneiric has reported a problem.

I've forgotten, have we ruled out a hardware problem?  It works in another OS or earlier linux release?  If so probably time to file a bug report or two.

And yes I suppose it could be something to do with the video driver.  But we have too many variables already so I'm reluctant to introduce more.


Edit:  By the way this is something Nikolai at [DIGI*mend*]("http://sourceforge.net/apps/mediawiki/digimend/index.php?title=DIGImend") might be interested in.

---

### Post by barneyjoseph on 2012-04-02
Hi,

I am trying to follow this  tutorial but I've run into trouble right from the start. I am a newbie  to Ubuntu and I have Maverick installed on my computer. I have an iBall  PF1209 drawing tablet which I am trying to restrict to one monitor. My  input list looks like this.

```

xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; USB Optical Mouse                           id=9    [slave  pointer  (2)]
&#9116;   &#8627;                 TabletPF1209               id=10    [slave  pointer  (2)]
&#9116;   &#8627;                 TabletPF1209               id=11    [slave  pointer  (2)]
&#9116;   &#8627;                 TabletPF1209               id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Dell Dell USB Keyboard                      id=8    [slave  keyboard (3)]


```As you may have noticed... there is a funny ascii character next  to the tablet's device name. When I try to list out its properties: 

```

xinput --list-props "TabletPF1209 "
unable to find device TabletPF1209

```I cannot get past this stage because of the funny device name that my tablet has. So here is my question: **Can the device name be changed?**

Any help would be greatly appreciated!

Thanks,
Barney.

---

### Post by Falcata on 2012-04-02
Try inputting the ID number instead of the name.

---

### Post by barneyjoseph on 2012-04-02
So will I have to do it for all the 3 entries of the drawing tablet 10,11 & 12?
Thanks for the reply :)

Barney.

---

### Post by barneyjoseph on 2012-04-03
Thank you Falcata for the help. I've been able to restrict the tablet by using the id in the xinput. I did it for all the 3 entries. Used the Transformation Matrix method. Happy Drawings :)

Barney.

---

### Post by WG- on 2012-05-22
Unfortunately the first method failed at my Toshiba Portege M750 tablet. The second method was the solution but I don't want to keep calculating every time the correct setting when I'm either at work or at home which both have a different screen resolution.

Hence I created a small script...

```
function mapstylus()
{
    local monitorInfo="$(xrandr --current)"
    local scr0x=$(echo -e "$monitorInfo" | grep '*+' | uniq | awk '{print $1}' | cut -d 'x' -f1)
    local scr0y=$(echo -e "$monitorInfo" | grep '*+' | uniq | awk '{print $1}' | cut -d 'x' -f2)
    local scr1x=$(echo -e "$monitorInfo" | grep '* ' | uniq | awk '{print $1}' | cut -d 'x' -f1)
    local scr1y=$(echo -e "$monitorInfo" | grep '* ' | uniq | awk '{print $1}' | cut -d 'x' -f2)
    local element00=$(echo "scale=5; $scr0x / ($scr0x + $scr1x)" | bc )
    local element11=$(echo "scale=5; $scr0y / $scr1y"            | bc )

    xinput set-prop "Serial Wacom Tablet stylus" --type=float "Coordinate Transformation Matrix" $element00 0 0 0 $element11 0 0 0 1
}
```

---

### Post by PeterME on 2012-09-14
> **Falcata said:**
> This still isn't working.  I've got the xinput commands correctly set, but it is still jumping off to the right-hand side.

This is both with the doubled entries and with them disabled by the custom xorg and evdev configurations, and in all cases the tablet starts having this 'jumping' problem after making any attempt to set its properties.

So, I'm guessing that it's something else that's the problem.  Any ideas or suggestions?

EDIT: This is a demonstration of attempting to draw a relatively straight vertical line in inkscape:

[IMG]https://lh4.googleusercontent.com/-uzqvoPIhJEU/T2QEt1hA6GI/AAAAAAAACJo/RwIm_4jAoLg/s642/AttemptedStraightLine.png[/IMG]
I'm having a very similar problem. And I'm running Ubuntu 12.04 with kernel upgraded to 3.4 to get the drivers. No proprietary graphics card driver.

---

### Post by Favux on 2012-09-17
Hi PeterME,

Welcome to Ubuntu forums!


Sorry for the slow response.

Yes that's a known issue and I should/would have done an update about it.  I think it is a recent issue but I'm not sure which X Server it started with.  Oh well this post will have to do.  Anyway Falcata did contact Nick at DIGI*mend*:  [http://sourceforge.net/mailarchive/forum.php?thread_name=20120602024936.476a0614%40gmx.com&forum_name=digimend-users](http://sourceforge.net/mailarchive/forum.php?thread_name=20120602024936.476a0614%40gmx.com&forum_name=digimend-users)

As you can see Nick reported the bug to Xorg on bugzilla:  [https://bugs.freedesktop.org/show_bug.cgi?id=49347](https://bugs.freedesktop.org/show_bug.cgi?id=49347)  Peter found and fixed the bug and committed it on 5-16-12:  [http://cgit.freedesktop.org/xorg/xserver/commit/?id=749a593e49adccdf1225be28a521412ec85333f4](http://cgit.freedesktop.org/xorg/xserver/commit/?id=749a593e49adccdf1225be28a521412ec85333f4)  Despite that it isn't in X Server 1.12.2 although it was released on 5-29-12.  Instead the fix appears to be in X Server 1.13.0

Falcata successfully used the patch (also attached below) provided by Nick to fix the problem on his Arch X Server.


**Lauchpad bug reports**:  I suggest anyone encountering this problem post on one of these reports, or at least click the "affects me too" button.  Zachary posts the patch on the first one.  That might increase the priority.
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1005321](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1005321)
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/990466](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/990466)


**[SIZE="3"]CTM Broken for xf86-input-evdev[/SIZE]**
You cannot apply a CTM to a input tool that uses xf86-input-evdev without getting the associated cursor dancing around and so spurious lines in Gimp, Inkscape, etc.  This is fixed in X Server 1.13.0.  Meanwhile you would need to apply the attached patch.

---

### Post by PeterME on 2012-09-18
Thanks, if this works I'll be very grateful :) But as I'm new to Linux I have some trouble working out how to apply the patch.. I tried !patch after cd-ing to the patch file directory but it just asked for the file to patch. What's the name of the file? Or am I doing this all wrong? Tried to search for xf86-input-evdev but no hits.

---

### Post by Favux on 2012-09-18
I haven't actually tried it because as I understand it the patch needs to be applied to the X Server and that is something I don't want to do.  I included the patch in case there is someone who knows how and would want to make a PPA with the patch.  If someone does do a PPA they'd probably post it on one of the bug reports I link you to.  And here would be nice too.

Ubuntu renames things so the Ubuntu package for xf86-input-evdev is xorg-xserver-input-evdev.  And the package you would want is xorg-server (the X Server), I think.  You'd need to download the appropriate xorg-server package deb for your release and your install type, 32 or 64 bit.  Then you would need to open it up and install the patch, to the Debian patches I suppose, and tell the deb packaging script the new patch is there so it applies it.  Then close the deb back up, after relabeling it to something appropriate, and then apply the deb to your install.  There are Ubuntu wiki pages telling you how to do that kind of thing but it gets pretty involved.

Which is why I don't want to do it. :)  Unless you know your way around Ubuntu I'd wait for a PPA that has your X Server with the patch applied.  Maybe the xorg-edgers team?  It's even possible they have a X Server PPA with the patch already.  They deal with bleeding edge releases/updates.  Or for Ubuntu to backport the support to Precise if they decide to.  Which is safer.  I haven't check if Quantal has the patch but installing Quantal Beta 2 when it is out might be the quickest thing to do.

---

### Post by PeterME on 2012-09-18
[xorg in quantal]("https://launchpad.net/ubuntu/quantal/+source/xorg-server"): it seems like Quantal is running 1.13 so it should be fixed. Guess I'll wait for that then.

---

### Post by Favux on 2012-09-18
Looks like you'll be good with Quantal's 1.13.0.  Nick just told me the fix first appears in 0.13.0.  Updated post above to reflect that.

---

### Post by robjoski on 2012-09-24
No, it's still not fixed with Xserver 1.13. I think the commit that "fixed" it is wrong:
[http://cgit.freedesktop.org/xorg/xserver/patch/dix/getevents.c?id=749a593e49adccdf1225be28a521412ec85333f4](http://cgit.freedesktop.org/xorg/xserver/patch/dix/getevents.c?id=749a593e49adccdf1225be28a521412ec85333f4)
I'm pretty sure this is the offending code.

```

    int has_x, has_y; 

    has_x = valuator_mask_fetch_double(mask, 0, &ox); 
    has_y = valuator_mask_fetch_double(mask, 1, &oy); 

    if (!has_x && !has_y) 
        return; 
    if (!has_x || !has_y) {

```Try replacing it with this (from the [original patch]("https://bugs.freedesktop.org/show_bug.cgi?id=49347")):
```

    if (!valuator_mask_isset(mask, 0) || !valuator_mask_isset(mask, 1)) {

```

---

### Post by Favux on 2012-09-24
Hi robjoski,

Thanks for the heads up.  Boy I sure hope you are wrong about that.  It would be (insert your selection of choice words here) if it is still broken in 13.  Looking at it again it looks like maybe only Zachary is claiming the commit works for him.  Nick maybe was running something else:  [https://bugs.freedesktop.org/attachment.cgi?id=61690](https://bugs.freedesktop.org/attachment.cgi?id=61690)  'cause he backported it.

---

### Post by robjoski on 2012-09-24
> **Favux said:**
> Hi robjoski,

Thanks for the heads up.  Boy I sure hope you are wrong about that.  It would be (insert your selection of choice words here) if it is still broken in 13.  Looking at it again it looks like maybe only Zachary is claiming the commit works for him.  Nick maybe was running something else:  [https://bugs.freedesktop.org/attachment.cgi?id=61690](https://bugs.freedesktop.org/attachment.cgi?id=61690)  'cause he backported it.

Even if he backported the patch for 12.04, neither Ubuntu or upstream have applied that version of the patch. There haven't been any upstream changes indicating it was fixed aside from the dubious commit in May - see [http://cgit.freedesktop.org/xorg/xserver/log/dix/getevents.c](http://cgit.freedesktop.org/xorg/xserver/log/dix/getevents.c).
The commit in May appears to discard the code that does the transformation. We still need someone to get the fix I proposed earlier upstream.

---

### Post by Favux on 2012-09-24
It would be a good thing if you opened a bug report on Bugzilla then with your proposed patch and referring to the previous bug report.  And if it lets you cc Peter Hutterer regarding the problem with the commit.  If that doesn't get prompt attention I can contact him and Nick directly but I'd rather not go that route unless I had to.


It is looking more like someone needs to do a PPA for Precise.  Have you thought about adding an entry to the main Launchpad bug report?

---

### Post by robjoski on 2012-09-24
I'm going to test my patch before I submit it anywhere. I've been in situations before where I submitted patches that didn't work due to not being tested :P

I'll see about Bugzilla, I don't remember whether I have an account already. In the meantime, I'm compiling away!

---

### Post by robjoski on 2012-09-25
Good thing I checked... My fix still didn't work! :(

---

### Post by Favux on 2012-09-25
Bummer.  This is in Quantal?

---

### Post by robjoski on 2012-09-25
Yes, Quantal. It took forever to build, too... 
I might try a few more things with the source code, but knowing my proficiency in C, it's probably not worth the compile time :/

---

### Post by PeterME on 2012-09-28
Works for me in Quantal Beta 2. No problems whatsoever. Mapped all the three screen to Ctrl+1,2,3 so now I can even change between them, perfect!

---

### Post by Favux on 2012-09-28
Hi PeterME,

Outstanding!  That's what I wanted to hear.  :)

---

### Post by robjoski on 2012-10-01
PeterME, are you rotating though? The Coordinate Transformation Matrix shouldn't have problems if you're multi-screen, but not rotating anything. The jumping problem is still there when you use the CTM to rotate one screen.

---

### Post by nomux on 2012-12-12
Are there any news about this Bug. It affects ubuntu 12.10 with xserver 1.13.0 and dual monitor setup with touchscreen too

---

### Post by Favux on 2012-12-14
If I recall correctly someone submitted a patch to fix it for rotation to the original bug report.  Have to check the bug report and see if there was a response.


Edit:
Looks like the fix for rotation CTM was committed:  [https://bugs.freedesktop.org/show_bug.cgi?id=49347](https://bugs.freedesktop.org/show_bug.cgi?id=49347)

---

### Post by asgard2 on 2013-02-01
can anyone tell me, why he does not finde the output?

> $ xrandr
Screen 0: minimum 8 x 8, current 3200 x 1080, maximum 8192 x 8192
VGA-0 disconnected (normal left inverted right x axis y axis)
LVDS-0 connected 1280x800+1920+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+
HDMI-0 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 477mm x 269mm
   1920x1080      59.9*+   60.0  
   1680x1050      60.0  
   1280x1024      75.0     60.0  
   1280x960       75.0  
   1280x720       75.0  
   1152x864       75.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   640x480        75.0     59.9  

$ xsetwacom set "Wacom Bamboo Connect Finger touch" MapToOutput LVDS-0
Unable to find an output 'LVDS-0'.


---

### Post by asgard2 on 2013-03-21
In tried this command:  
```
$ xinput set-prop "Wacom Bamboo Connect Finger touch" --type=float "Coordinate Transformation Matrix" 0.4 0 0 0 0.740741 0 0 0 1
```  

But it is not working, does anyone know why?
[[IMG]http://www0.xup.in/tn/2013_03/13571317.png[/IMG]]("http://www.xup.in/dl,13571317/Bildschirmfoto_-_21.03.2013_-_11:26:24.png/")

I created a new thead, because it is related to a newer Ubuntu Version 12.10.
[http://ubuntuforums.org/showthread.php?t=2128247](http://ubuntuforums.org/showthread.php?t=2128247)

---

### Post by Favux on 2013-03-22
Hi asgard2,

I'd like to point out touch is in Relative Mode, not Absolute Mode like the Pen.  So it really can't be confined to one screen.

---

### Post by asgard2 on 2013-03-23
oh, sorry.
I choose the wrong xinput.
```
xinput set-prop "Wacom Bamboo Connect Pen stylus" --type=float "Coordinate Transformation Matrix" 0.4 0 0.6 0 0.740741 0 0 0 1
```
is correct.

Thanks.

---

### Post by Favux on 2013-03-24
Assuming the following is correct.

Left monitor - HDMI-0
1920 x 1080

Right monitor - LVDS-0
1280 x 800

And you are trying to confine the Pen to the right monitor, then what you have should be correct:
```
xinput set-prop "Wacom Bamboo Connect Pen stylus" --type=float "Coordinate Transformation Matrix" 0.4 0 0.6 0 0.740741 0 0 0 1
```
What happens when you apply it?  Nothing?

What release of Ubuntu are you using?
```
Xorg -version
```

Also I noticed you started another thread and called it "wacom bamboo pen with twin view on Ubuntu 12.10".  (So it looks like Quantal is the release but I'm double checking and trying to get the kernel and X Server.)  Anyway with TwinView are you indicating you are actually using the NVidia proprietary drivers?

---

### Post by asgard2 on 2013-03-25
> **Favux said:**
> Assuming the following is correct.

Left monitor - HDMI-0
1920 x 1080

Right monitor - LVDS-0
1280 x 800

And you are trying to confine the Pen to the right monitor, then what you have should be correct:
```
xinput set-prop "Wacom Bamboo Connect Pen stylus" --type=float "Coordinate Transformation Matrix" 0.4 0 0.6 0 0.740741 0 0 0 1
```
What happens when you apply it?  Nothing?


If I try this, it is located to the right monitor, but I have not the full height. The lower part of the screen is unreachable.

For the right monitor 
```
alias setwacomright='xinput set-prop  "Wacom Bamboo Connect Pen stylus" --type=float "Coordinate  Transformation Matrix" 0.4 0 0.6 0 1 0 0 0 1'
```
is correct.

But I did not found the correct configuration if I want to change to the left one.

```
xinput set-prop "Wacom Bamboo Connect Pen stylus" --type=float "Coordinate Transformation Matrix" 0.6 0 0 0 1 0 0 0 1
```

Same problem here, the lower part of the screen is unreachable.

> **Favux said:**
> 
What release of Ubuntu are you using?
```
Xorg -version
```

Also I noticed you started another thread and called it "wacom bamboo pen with twin view on Ubuntu 12.10".  (So it looks like Quantal is the release but I'm double checking and trying to get the kernel and X Server.)  Anyway with TwinView are you indicating you are actually using the NVidia proprietary drivers?

Yes, I installed the NVidia proprietary driver.

```
$ Xorg -version

X.Org X Server 1.13.0
Release Date: 2012-09-05
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.2.0-32-generic x86_64 Ubuntu
Current Operating System: Linux asgard 3.5.0-26-generic #42-Ubuntu SMP Fri Mar 8 23:18:20 UTC 2013 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-26-generic root=UUID=cbf965d3-fafc-4774-8873-972fa48a5c12 ro quiet splash
Build Date: 27 November 2012  07:44:35AM
xorg-server 2:1.13.0-0ubuntu6.1 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.26.0
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.


```

---

### Post by Favux on 2013-03-25
> **asgard2 said:**
> 
For the right monitor 
```
alias setwacomright='xinput set-prop  "Wacom Bamboo Connect Pen stylus" --type=float "Coordinate  Transformation Matrix" 0.4 0 0.6 0 1 0 0 0 1'
```
is correct.
Interesting.  So the Coordinate Transform Matrix does work, you just needed the correct one.

> **asgard2 said:**
> 
But I did not found the correct configuration if I want to change to the left one.

```
xinput set-prop "Wacom Bamboo Connect Pen stylus" --type=float "Coordinate Transformation Matrix" 0.6 0 0 0 1 0 0 0 1
```

Same problem here, the lower part of the screen is unreachable.
OK, try this for the left monitor and let me know what happens.
```
xinput set-prop "Wacom Bamboo Connect Pen stylus" --type=float "Coordinate Transformation Matrix" 0.6 0 0 0 1.35 0 0 0 1
```
We're checking if the new Xorg compatible Nvidia drivers handle the y-axis scaling backwards.

> **asgard2 said:**
> 
Yes, I installed the NVidia proprietary driver.
The nvidia 302, which came out in May 2012, was finally compatible with RandR 1.2/1.3. Supposedly compatibility was coming with RandR 1.4 but that was delayed. But Nvidia beat RandR 1.4 to the punch. 

Alright, so definitely Quantal with:
```
X.Org X Server 1.13.0

Current Operating System: Linux asgard 3.5.0-26-generic #42-Ubuntu SMP Fri Mar 8 23:18:20 UTC 2013 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-26-generic root=UUID=cbf965d3-fafc-4774-8873-972fa48a5c12 ro quiet splash

xorg-server 2:1.13.0-0ubuntu6.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support))
```
I'm not aware in any big changes in xinput syntax with Quantal.  So more likely the Nvidia thing.

Also now that I know it is Nvidia, with MapToOutput why don't you try using HEAD-0, HEAD-1, etc. instead of say LVDS-0.  For example:
```
xsetwacom set "Wacom Bamboo Connect Finger touch" MapToOutput HEAD-1
```
I'm curious to hear what happens.

---

### Post by asgard2 on 2013-03-25
```
xinput set-prop "Wacom Bamboo Connect Pen stylus" --type=float "Coordinate Transformation Matrix" 0.6 0 0 0 1.35 0 0 0 1
```
is equal to
```
xinput set-prop "Wacom Bamboo Connect Pen stylus" --type=float "Coordinate Transformation Matrix" 0.6 0 0 0 1 0 0 0 1
```

and 
```
xsetwacom set "Wacom Bamboo Connect Finger touch" MapToOutput HEAD-1
```
changes nothing.

```
$ xsetwacom set "Wacom Bamboo Connect Finger touch" MapToOutput HEAD-1
> nothing happened
$ xsetwacom set "Wacom Bamboo Connect Finger touch" MapToOutput HEAD-0
> nothing happened
$ xsetwacom set "Wacom Bamboo Connect Finger touch" MapToOutput LVDS-0
Unable to find an output 'LVDS-0'.
$ xrandr
Screen 0: minimum 8 x 8, current 3200 x 1080, maximum 8192 x 8192
VGA-0 disconnected (normal left inverted right x axis y axis)
LVDS-0 connected 1280x800+1920+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+
HDMI-0 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 477mm x 269mm
   1920x1080      59.9*+   60.0  
   1680x1050      60.0  
   1280x1024      75.0     60.0  
   1280x960       75.0  
   1280x720       75.0  
   1152x864       75.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   640x480        75.0     59.9  
$ xsetwacom set "Wacom Bamboo Connect Finger touch" MapToOutput HDMI-0
Unable to find an output 'HDMI-0'.
```

```
 xsetwacom set "Wacom Bamboo Connect Pen stylus" MapToOutput HEAD-0

```

Is working, but not correct. The lower part of the screen is unreachable, whatever is selected - right/left.

---

### Post by Favux on 2013-03-25
My fault, made a copy paste error, I meant "Pen stylus" not "Finger touch".  So despite the Nvidia driver now supplying information when you query **xrandr** xsetwacom is still using the Xinerama HEAD extensions.  The Xinerama HEAD extension was the work around the developers came up with to deal with Nvidia not being compatible with Xrandr.  Now that it sort of is it looks like they might be able to change it.

My guess is that Nvidia is not scaling y-axis the same as the Xorg drivers.  It may have something to do with what Nvidia thinks is the primary monitor.  Is HEAD-0 the right monitor?

---

### Post by asgard2 on 2013-03-25
0 should be the right screen and 1 the left.
But the problem is with both screens if I use MapToOutput, the lower part of the screen is unreachable.

---

### Post by Favux on 2013-03-25
> **asgard2 said:**
> 0 should be the right screen and 1 the left.
OK, it appears it is treating the right monitor as the "primary" or HEAD-0 monitor and the left monitor as HEAD-1.  I wonder how it is determining that.  The physical connections to the video card?
> **asgard2 said:**
> 
But the problem is with both screens if I use MapToOutput, the lower part of the screen is unreachable.
There seems to be a bug with how the Nvidia driver implements y-axis scaling with the RandR.  Since it is still relatively early days for the Nvidia driver being compatible with RandR I guess that isn't too surprising.

I think I have a handle on what is happening, maybe.  The MapToOutput results tell the story I think.  Instead of using the largest y-axis (in your case 1080) like the other Xorg drivers it is using the "primary" or right monitor's (HEAD-0) y-axis, i.e. 800.  So the bug is in the code where it selects the appropriate or maximum y-axis.

When MapToOutput is doing the CTM scaling for the y-axis you are getting:
```
Right:  800/1080 = .740741 for the scaling and the bottom 25% of the screen isn't covered

Left:  800/800 = 1 Then remember it is applying the scaling to 800 or 1 x 800  But that is only 75% of the left monitor's 1080 y-dimension.  So the bottom 25% of the screen isn't covered.
```
The fact that we can use xinput to set the CTM scaling for the right monitor to 1 and it fits seems to confirm the idea.  What I don't understand is why setting the left monitor's y-scaling to 1.35 doesn't work.  Why would anything over 800 get chopped off?


I think you probably need to file a bug report with Nvidia against their driver.  But first I would suggest you look carefully through the settings in the Nvidia control panel and see if there is something relevant there.  There may even be a new setting or two that applies.  Please post if you find something.

---

### Post by ragtag on 2013-06-21
I updated the script posted a few pages ago. Save it as waspect and make it executable "chmdo a+x waspect". You can throw it into /usr/local/bin if you want to make it available systemwide.

It's not tested very much but seems to work.

To run it type waspect (if it's in path), or ./waspect if you're in the same folder as the script. This will match the aspect of the tablet to your screen(s). You can also run "waspect first" or "waspect second" to map the tablet to one of your screens. I've only put in support for two screens, so if you have more you're on your own. :)

```

#!/bin/bash
#
# Matches the shape of the active area on your Wacom tablet, to your screen resolution.
#
# Usage: waspect [first|second]
# 
#  Used with no argument it matches the aspect ratio to the resolution of your screen(s).
#  Used with either first or second, it will match the aspect ratio of the tablet to the first or second screen.
#
# Modified version of Wacom Aspectratio script 0.1 \(ReasonNL\)


if [ "$1" == "-h" ]
then
    echo "Usage: waspect [first|second]"
    echo "waspect matches the active area of your wacom tablet to your screen(s) resolution."
    echo "Use first or second option, to match you tablet to one of two screens."
    echo "The script only supports one or two screens."
    exit 0
fi

# Config active tablet area position
positionX=center    #left, center, right
positionY=top         #top, center, left

# Start script
precision=10000

# Maps to both
resolution=`/usr/bin/xrandr -q  | grep "Screen 0" | grep "current [0-9]\+ x [0-9]\+" -o | tr -d "current "`
mapto=-1
count=0
screens=`xrandr -q | grep "connected [0-9]\+x[0-9]\+" -o | tr -d "connected " | sed ':a;N;$!ba;s/\n/ /g'`
screens=`xdpyinfo -ext XINERAMA | grep "head" | cut -d\  -f 5 | sed ':a;N;$!ba;s/\n/ /g'`
screencount=`echo $screens | wc -w`
for s in ${screens[*]}
do
    if [[ "$1" == "first" && $count == 0 ]]
    then
        mapto=0
        resolution=$s
    elif [[ "$1" == "second" && $count == 1 ]]
    then
        mapto=1
        resolution=$s
    fi
    let count+=1
done

resX=`echo $resolution | grep "^[0-9]\+" -o`
resY=`echo $resolution | grep "[0-9]\+$" -o`
resRatio=$(((resX*precision)/resY))
if [[ $mapto -eq -1 && $screencount -eq 1 ]]
then
    echo Matching aspect ratio of the tablet to the screen at resolution $resolution
elif [ $mapto -eq -1 ]
then
    echo Matching aspect ratio of the tablet to both screens at resolution $resolution
elif [ $mapto -gt -1 ]
then
    echo Matchin aspect ratio of the tablet to the $1 screen at resolution $resolution
fi
xsetwacom --list | while read line; do
    device=`echo $line | grep "id: [0-9]\+" -o | tr -d "id: "`
    xsetwacom set "$device" ResetArea
    if [ $mapto -gt -1 ]
    then
        xinput map-to-crtc "$device" "HEAD-$mapto"
    else
        xsetwacom set "$device" MapToOutput "$resolution+0+0"
    fi
    area=`xsetwacom get "$device" Area | grep "[0-9]\+ [0-9]\+$" -o`
    areaX=`echo $area | grep "^[0-9]\+" -o`
    areaY=`echo $area | grep "[0-9]\+$" -o`
    # echo Area is $areaX by $areaY
    if [ "$areaX" != "" -a "$areaY" != "" ]; then
        if [ $resRatio -gt $precision ]; then
            newAreaX=$areaX
            newAreaY=$(( (areaX*precision)/resRatio ))
        elif [ $resRatio -lt $precision ]; then
            newAreaX=$(( (areaY*resRatio)/precision ))
            newAreaY=$areaY
        else
            if [ $areaX -gt $areaY ]; then
                newAreaX=$areaY
                newAreaY=$areaY
            else
                newAreaX=$areaX
                newAreaY=$areaX
            fi
        fi
        newTop=0
        newLeft=0
        if [ $areaX -gt $newAreaX ]; then
            if [[ $positionX == center ]]; then
                newLeft=$(( (areaX-newAreaX)/2 ))
            elif [[ $positionX == right ]]; then
                newLeft=$(( areaX-newAreaX ))
            fi
            newAreaX=$((newAreaX+newLeft))
        fi
        if [ $areaY -gt $newAreaY ]; then
            if [[ $positionY == center ]]; then
                newTop=$(( (areaY-newAreaY)/2 ))
            elif [[ $positionY == bottom ]]; then
                newTop=$(( areaY-newAreaY ))
            fi
            newAreaY=$((newAreaY+newTop))
        fi
        xsetwacom set "$device" Area "$newLeft $newTop $newAreaX $newAreaY"
        # echo Area of $line set to `xsetwacom get "$device" Area`
    else
        echo $line doesn\'t have an area
    fi
done

```

I've run it on Ubuntu 12.4 64bit, with Nvidia propriatary drivers, and two screens at 1600x1200 and 2560x1440.


It's all a bit quick and hacky, so let me know if it doesn't work as expected.

---

### Post by solars on 2013-11-10
Hi there, I've got a couple of questions:

Got a Sony Vaio Fit Multi-Flip (can invert the screen and has a touch display) which I want to setup, so far it's working, but:

**Is this still the preferred way to configure under 13.10 or are there now any tools that help?**

I've got the following setup:

LEFT External Monitor 1680 x 1050
RIGHT Laptop Touch Display Inverted 1920 x 1080

Given the calculations above I get the matrix:
-0.53333333333333333333 0 1
0 -1.02857142857142857142 1.02857142857142857142
0 0 1

I don't seem to have a wacom device, xwacom --list devices returns nothing, xinput returns among others:
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; N-trig DuoSense Pen                     	id=18	[slave  pointer  (2)]
&#9116;   &#8627; N-trig DuoSense                         	id=19	[slave  pointer  (2)]

which seems to be my touch device.

I then used:
xinput set-prop "N-trig DuoSense Pen" --type=float "Coordinate Transformation Matrix" -0.53333333333333333333 0 1 0 -1.02857142857142857142 1.02857142857142857142 0 0 1

to configure the stylus on the right (laptop) screen.
it works, and is accurate on the top/right side - however, if I move the pen to the bottom/left edge it's off around 1 cm to the left and 1cm to the bottom.

[B]can anyone spot what I missed?
[/B]
Thanks a lot!

---

### Post by Favux on 2013-11-10
Hi Solars,

Correct, it is an N-Trig digitizer not a Wacom digitizer.  The Pen should be on the Wacom X driver however.  The 50-wacom.conf in xorg.conf.d has this match:
> MatchProduct "HID 1b96:0001|N-Trig Pen"
Run **lsusb** in a terminal and post the output, at least the N-Trig line.  Let's see if the Product ID differs and is for a new N-Trig digitizer.  As you can see 'N-Trig Pen' has changed to 'N-trig DuoSense Pen' which is why it isn't matching.  Did it come with a Pen/Stylus?  Sounds like it did.

Multi-touch should be on the second node:
> &#9116; &#8627; N-trig DuoSense id=19 [slave pointer (2)]
and be through the evdev X driver.

Theoretically you should be able to use the Gnome Wacom applet in System Settings to set the Pen to the monitor you want if it is on the Wacom X driver.

Also it sounds like you may need to calibrate the stylus.  When the Multi-Flip is not connected to another monitor is calibration good?  There should be calibration in your version of the Wacom applet.  Otherwise you can use xinput_calibrate (Calibrate Touchscreen in the Software Center).  You can apply the calibration either through a custom xorg.conf.d .conf file or a script.

---

### Post by solars on 2013-11-10
Hi there, thanks for your answer!

lsusb returns **Bus 002 Device 005: ID 1b96:0f04 N-Trig**
Stylus is included, yes, one from Sony with 2 buttons

Do you mean the section "Wacom Tablet" in gnome-control-center?
If I open it it says No tablet detected.

The calibration is good if not connected to another monitor, yes
If I invert the display though, the movement is inverted though.

I used xinput_calibrate for the standalone use and the matrices I posted for the connected monitor.
But as I've mentioned, it's off by about 1cm in x and y direction on the bottom left corner, not sure if the calculation is wrong, but I checked it.

How can I enable multi-touch? Does this only work through this wacom applet?
I'm now in a different window manager (i3) not sure if it would be different in unity for the wacom app?
I can start all the gnome stuff anyways..

Thanks,
Christoph

---

### Post by Favux on 2013-11-10
There isn't a match so both the stylus and touch are likely on evdev.  You can verify that by running:
```
xinput list-props ID#
```
Using the current (can change) ID# of both nodes.

Let's try to put the stylus on the Wacom driver.  We'll be bad and modify the 50-wacom.conf rather than create the user xorg.conf.d and add a custom .conf to it.  For an explanation see:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xorg.conf.d](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xorg.conf.d)
```
gksudo gedit /usr/share/X11/xorg.conf.d/50-wacom.conf
```
In 13.10 you may need to install the 'gksu' package first.  Change:
```
# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
	Identifier "Wacom N-Trig class"
	MatchProduct "HID 1b96:0001|N-Trig Pen"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
	Option "Button2" "3"
EndSection
```
to read:
```
# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
	Identifier "Wacom N-Trig class"
	MatchProduct "HID 1b96:0001|ID 1b96:0f04|N-Trig Pen|N-trig DuoSense Pen"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
	Option "Button2" "3"
EndSection
```
Then either log out and in or restart.  I'm not sure 'ID 1b96:0f04' will actually match so if you could try that alone at some point and report if it works that would be good.  Post **xinput list** to check if the stylus is now on the Wacom driver and check if Wacom Tablet sees it now.

The Wacom X driver won't work for N-Trig touch.  Multi-touch, if enabled, should be automatic through the evdev driver.  See:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Multitouch](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Multitouch)

Edit:  Thinking a bit I wonder if we shouldn't move this to a new thread.  You've got a new N-Trig digitizer and a new thread about your model Vaio would probably be a good thing.  Plenty of information already to copy over to it.

---

### Post by solars on 2013-11-10
I will create a new thread once I figured out what can be done successfully :)

The device properties was: [https://gist.github.com/anonymous/cd1c294a34ee81e4dc9f](https://gist.github.com/anonymous/cd1c294a34ee81e4dc9f)

Sso I changed the configuration and restarted X, the output includes now:
  &#8627; N-trig DuoSense Pen stylus              	id=18	[slave  pointer  (2)]
&#9116;   &#8627; N-trig DuoSense Pen eraser              	id=19	[slave  pointer  (2)]
&#9116;   &#8627; N-trig DuoSense Pen pad                 	id=20	[slave  pointer  (2)]
&#9116;   &#8627; N-trig DuoSense                         	id=21	[slave  pointer  (2)]

The wacom settings are also working - I'm not sure how to continue now to set this up in the right/easiest way.
Is there a way to configure the inverted mode and calibrate it? Or do I still need the CTM stuff?
I noticed I can map it to a specific screen, but it still seems to be as it was before (touch pointer across both screens, inverted)

The output

---

### Post by solars on 2013-11-10
Ah! Now this worked:
xsetwacom set "N-trig DuoSense Pen stylus" MapToOutput eDP1

It's limited to the laptop screen now (didn't work through the wacom settings)
The axis are still inverted though:
 xinput set-prop 18 "Evdev Axes Inversion" 1                             
property 'Evdev Axes Inversion' doesn't exist, you need to specify its type and format

---

### Post by solars on 2013-11-10
ok I understood, I think it is working now through xsetwacom!

And: xsetwacom --set 18 Rotate half 
works like a charm :)

---

### Post by Favux on 2013-11-10
Sounding good.  When on xinput list you see stuff like stylus, eraser, and pad appended you know it is on the Wacom X driver because that is what is doing that.
```
N-trig DuoSense Pen stylus
```
For touch you'll probably need a xinput CTM command for evdev as I don't think the old axis swap stuff works.  At least it was broken for a while anyway.

Does the Multi-Flip use an accelerometer to change orientation?

---

### Post by solars on 2013-11-10
According to: [http://presscentre.sony.eu/content/detail.aspx?ReleaseID=8815&NewsAreaId=2](http://presscentre.sony.eu/content/detail.aspx?ReleaseID=8815&NewsAreaId=2) it does have one

Digitizer stylus, 8 Megapixel Rear Camera powered by &#8216;ExmorRS for PC&#8217; sensor with Auto-Focus; Front facing HD web camera powered by &#8216;Exmor R for PC&#8217;; WLAN IEEE 802.11a/b/g/n; USB 3.0 with USB charge (x1); USB 3.0 (x1); Bluetooth® standard Ver. 4.0 + HS; HDMI out; SD memory card slot; stereo speakers with ClearAudio+ mode ; Sensors (NFC, **Accelerometer**, Gyro, Digital Compass);Backlit Keyboard; HDMI to VGA adapter (optional); AC powered Ethernet to Wi-Fi Router(optional)

How can I find out if it is used, and if so, how can I automate the flipping? I.e. execute a xrandr and xsetwacom etc script?

What is the difference between these devices:
&#9116;   &#8627; N-trig DuoSense Pen stylus              	id=18	[slave  pointer  (2)]
&#9116;   &#8627; N-trig DuoSense Pen eraser              	id=19	[slave  pointer  (2)]
&#9116;   &#8627; N-trig DuoSense Pen pad                 	id=20	[slave  pointer  (2)]
&#9116;   &#8627; N-trig DuoSense 

I'm not sure how the wacom stuff works, the stylus is obvious, but what can I do with the eraser and pad settings? I suppose this needs to be supported by the software I use to draw? Or is this the mode if a button on the stylus is pressed?

What do you mean with "For touch you'll probably need a xinput CTM command as I don't think the old axis swap stuff works. At least it was broken for a while anyway." the last device above?
Edit: Right, for the last one this doesn't seem to work

---

### Post by Favux on 2013-11-10
Looking at it at the Sony web site it does not appear to use a hinge switch signal because I don't think orientation changes when you go from laptop to tablet mode.  In Windows is it the accelerometer it is using to change orientations?  I'm wondering if we can come up with a script for that.  Something like method 2 in the old [Rotation HOW TO]("http://ubuntuforums.org/showthread.php?t=996830") or the new [Rotation HOW TO]("http://forums.linuxmint.com/viewtopic.php?f=42&t=110395").  I have a sample accelerometer script.  You definitely need to start another thread.  :)

You probably will find the accelerometer file that is changing state, assuming there already is a kernel driver for it, in /sys/devices/platform or maybe /sys/devices.  That's what we would need to check out.

Eraser and pad are spurious in you case.  At least up to now no N-Trig stylus has had an eraser.  Xournal can assign the eraser to one of the stylus side buttons.  Probably other app.s too.

Before the introduction of the CTM method the evdev driver used another method to change device orientation.  So your touch is now identified as "N-trig DuoSense" and that will need some xinput command(s) because it is on evdev.  Check that with list-props.

---

### Post by solars on 2013-11-10
Do I then need a CTM like the one I posted? Or is this possible in an easier way, without calculations based on the two resolutions
(as the mapping to a monitor seems to work with the touch device as well)?

I couldn't find any files about the rotation/accel :( But there are many, not sure what to look for or how to grep

---

### Post by Favux on 2013-11-10
Yes, for touch you'll need a CTM.  xrotate.py in Magick Rotation can act as a standalone script for Wacom and evdev devices when you are using the Multi-Flip unconnected.

What's the output of **lsusb**?  The accelerometer should be in there and  you can grep a keyword(s) from that line.

---

### Post by solars on 2013-11-10
Alright I'll have a look at the script and see if I can fix the matrix

The output is: [https://gist.github.com/anonymous/8176194afb5446806319](https://gist.github.com/anonymous/8176194afb5446806319)
Do you know which one could be the accel?

---

### Post by Favux on 2013-11-10
Doesn't look like the accelerometer is in there.  Maybe no kernel driver?

Try:
```
lsusb -vvvv
or
sudo lsusb -vvvv
```
Might need to add **| less** to the commands.  Also try:
```
lspci -vv
and
cat /proc/bus/input/devices
```

See the appendix at the bottom for just rotating the Flip.

---

### Post by solars on 2013-11-10
Created a draft thread here: [http://ubuntuforums.org/showthread.php?t=2187064&p=12844095#post12844095](http://ubuntuforums.org/showthread.php?t=2187064&p=12844095#post12844095)

The output of the above commands is here:
[https://gist.github.com/anonymous/584ff258e83c018797a9](https://gist.github.com/anonymous/584ff258e83c018797a9)

I don't see anything relevant there.. I suppose Lid Switch is closed/open

The rotation you are referring to (only 1/-1/0) is for the case when no external monitor is connected, right?
If I use one, I need to calculate it I assume

---

### Post by ArtMonkey on 2014-01-02
Hi. I left a post here [http://ubuntuforums.org/showthread.php?t=2196609](http://ubuntuforums.org/showthread.php?t=2196609)  But had no replies.

Basically, I need to disable my Aiptek (Waltop) graphics tablet on my right (dvi) monitor and leve it working on my left monitor. 

Any ideas???  I tried a few things with no luck. I saw a similar post where someone managed this with VGA. - [http://ubuntuforums.org/showthread.php?t=1664435](http://ubuntuforums.org/showthread.php?t=1664435)

Thanks for any help. Here's hoping ;)

Steve

---

