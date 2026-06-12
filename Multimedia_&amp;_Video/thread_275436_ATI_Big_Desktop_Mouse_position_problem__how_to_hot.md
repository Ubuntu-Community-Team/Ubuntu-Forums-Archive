---
title: "ATI Big Desktop Mouse position problem | how to hotkey a position fix?"
date: 2006-10-11
forum: Multimedia &amp; Video
---

### Post by lokalhost on 2006-10-11
RE: Mouse position offset issue with ATI fglrx driver on dual screen big desktop setup.

Judging from all the different threads I've come across to solve this annoyance, I'm not the only one that has not come to a resolution.

Background:
Dual Head Configuration : 
[LIST]
[*]**HW Cursor** on second screen is pixelated block; looks ugly and created difficulty in selecting with mouse.
[*]**SW Cursor** on both screens corrupts display where mouse pointer is whenever a mouse click/scroll event occurs (more annoying than the HW cursor bug on secondary screen
[/LIST]

Big Desktop Configuration :
HW Cursor works almost properly!  No display corruption, proper pointer(etc) on second screen; **HOWEVER**, when using the mouse in the second screen; if the second screen has a resolution that is different than the main screen (eg, wide screen laptop + 19" lcd) then the mouse position vs mouse displayed position becomes skewed vertically.

So far, the easiest/fastest method of recalibrating the mouse is to reposition the pointer to the very top of the display.  I've been living with this, but the annoyance factor of doing this _alot_ is growing.  What I'd like to do is have a hotkey that repositions the mouse to the top of the screen to re-calibrate, then reposition the pointer to the middle of the display.  Ideally, the pointer would return to the position I started with but I'm looking for an easy improvement..

I have not done an exhaustive search, but the search I did looking for a way to script the pointer location came up blank.

Anyone have some pointers on how to do this, or locations to look for appropriate documentation?  I have some extra buttons on the mouse I'd like to map to a re-calibration fix and help save me from some extra mouse motions.

ps, of course, if someone has come up with a fix for the pointer problem then I'm all ears :)

Thanks in advance.

---

### Post by papalagi on 2006-11-04
unfortunately i have the same problem

 i'm running a big desktop with the laptop monitor 1280x800 and, on the right ,a flat 1280x1024 and i need to recalibrate the cursor moving to the top when i switch from the big to the small one

 i wonder if it's possible to configure two 1280x1024 displays, with the left monitor scrolling on a virtual desktop as i have in win2000

 did you find any fix yet for the cursor issue?

 ciao

---

### Post by gandalf.come on 2007-01-11
I have a notebook (Acer 4600,ati x700 mobility) and also want to do dual screen setup. Same problem as you guys: Mouse jumps on one of the monitors (offset). Did you figure anything out. does it work with the opensource radeon drivers?
Help greatly appreciated.

---

### Post by Paul Paul on 2007-01-18
Same problem in Debian/Gnome.

On my left is my laptop screen, 1280x800 and on my right is my LG Wide Screen is 1680x1050. Everything works except the mouse offset as it move from one screen to another. Here's why:

Moving the mouse from the right wide screen to the left small screen works perfectly (no offset) so long as the mouse traverses within the top 800 pixels. In other words, both monitors were 800 in height everything would work just fine.

When the mouse traverses in the bottom 250 pixels (the difference between the two monitor's height) the mouse becomes offset by the amount of the additonal pixels during the traverse.

The problem also happens when one moves the mouse below the small screen's bottom border (offsets according to the distance below the edge, up to the 250 extra pixels).

It would be much more acceptable if the smaller (left) screen would scroll as I've seen it do in Clone mode. ... or even do some scaling (shrink). I wouldn't even mind if I could simply just not see the extra 250 pixels on the small monitor. Anything but that annoying offset. ](*,) 

It would also be nice if I could bind the primary desktop to the wide screen (right) instead of the left small screen (laptop). Anyone know how to do this (i.e. actually has it working)? Post your xorg.conf.

BTW, is this an ati driver problem, or something else?

PS I'm using an Acer Aspire 5100 (5102wmli) wih fglrx driver.

---

### Post by Dietmar on 2007-01-22
Hi,

I'd the same problem with the cursor offset and found the same workaround with moving the mouse to the top of the bigger screen and then to the other smaller screen, but this is very annoying.

I tried the fglrx 8.33 driver to have 3d acceleration and I wanted to try beryl out (beryl doesn't work with my ati x700 pcie card - I see the splash screen and then everything is white on both screens. Single head doesn't change anything - same effect). Xgl is installed.

With radeon driver the cursor problem doesn't occur - I've two screens (1024x768 and 1920x1200) and the smaller is with a virtual desktop 1920x1200. When I move from the bigger to the smaller screen there's no offset.

Dietmar

---

### Post by Paul Paul on 2007-01-22
Sorry if I'm a little new at this but is the "radeon driver" different from the fglrx driver? I thought those are two of the same. If not, where do I find the radeon driver?

Also what is a "virtual desktop" and if you are running it in 1920x1200 on the smaller 1024x768 monitor than what happens? Does it scale or pan? 

I'm running Gnome and I have "Workspaces". Are these the same as "virtual desktops"? Can each workspace have a different resolution? I'm such a noob.

---

### Post by Dietmar on 2007-01-24
The radeon driver is the opensource driver which comes with xorg.
fglrx is the driver which you can download directly from atis homepage (it's a proprietary driver).

Gnome workspaces are also virtual but with virtual desktop its e.g. if the screen only displays 1024x768 but I define a virtual desktop of 1920x1200, then only the 1024x768 sized part of the desktop is visible and I can move to the invisible parts by moving the mouse on that screen around. That works with radeon driver.

Here is the excerpt from my xorg.conf (now I'm using the fglrx driver despite of the cursor error and that my screen with dvi and dsub only works with dsub, because scrolling seems to be a bit better with fglrx driver). I've posted the cursor problem and that dvi doesn't works for me to the ati feedback form. Maybe I get a solution or its assigned as a bug.

Section "Device"
  BoardName    "Radeon X700 PRO (RV410) (PCIE)"
  BusID        "5:0:0"
  Driver       "radeon"
  Identifier   "Device[0]"
  Option	"MergedFB" "true"
  Option	"MonitorLayout" "LCD,CRT"
  Option	"CRT2Hsync" "30-65"
  Option	"CRT2VRefresh" "50-75"
  Option	"OverlayOnCRTC2" "true"
  Option	"CRT2Position" "LeftOf"
  Option	"MetaModes" "1920x1200-1024x768"
  Screen       0
  VendorName   "ATI"
EndSection

Section "Screen"
  DefaultDepth 24
  SubSection "Display"
    Depth      15
    Modes      "1920x1200" "1280x1024" "1280x960" "1280x800" "1152x864" "1280x768" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480" 
  EndSubSection
  SubSection "Display"
    Depth      16
    Modes      "1920x1200" "1280x1024" "1280x960" "1280x800" "1152x864" "1280x768" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480" 
  EndSubSection
  SubSection "Display"
    Depth      24
    Modes      "1920x1200" "1280x1024" "1280x960" "1280x800" "1152x864" "1280x768" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480" 
  EndSubSection
  SubSection "Display"
    Depth      8
    Modes      "1920x1200" "1280x1024" "1280x960" "1280x800" "1152x864" "1280x768" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480" 
  EndSubSection
  Device       "Device[0]"
  Identifier   "Screen[0]"
  Monitor      "Monitor[0]"
EndSection

Section "ServerLayout"
  Identifier   "Layout[all]"
  InputDevice  "Keyboard[0]" "CoreKeyboard"
  InputDevice  "Mouse[1]" "CorePointer"
  InputDevice  "Mouse[3]" "SendCoreEvents"
  InputDevice  "Mouse[5]" "SendCoreEvents"
  InputDevice  "Mouse[7]" "SendCoreEvents"
  Option       "Clone" "off"
  Option       "Xinerama" "off"
  Screen       "Screen[0]"
EndSection


Section "DRI"
    Group      "video"
    Mode       0660
EndSection

Section "Extensions"
  Option       "DAMAGE" "false"
  Option	"Composite" "false"	
EndSection

A virtual desktop can be defined in the screen section with Virtual (but with the former configuration of the metamodes it wasn't necessary).

SubSection "Display"
    Virtual    1920 1200
     Viewport   0 0
    Depth      16
    Modes      "1920x1200" "1024x768"
#    Modes      "1920x1200" "1900x1200" "1600x1200" "1680x1050" "1600x1024" "160
0x1000" "1400x1050" "1280x1024" "1440x900" "1280x960" "1366x768" "1280x800" "115
2x864" "1280x768" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480"
 EndSubSection

The smaller screen is only capable of displaying 1024x768 - with radeon it pans and with fglrx driver only the 1024x768 range is visible and the rest is not reachable. Would be not a problem for me because with panning when entering the smaller screen then the window which I display on that screen sometimes moves to a non visible range an I've to move the mouse around to make it visible again. The offset is annoying, because I often have to move back to the bigger screen to fix it.

---

### Post by roongpatoong on 2007-01-26
> **Paul Paul said:**
> Same problem in Debian/Gnome.

It would also be nice if I could bind the primary desktop to the wide screen (right) instead of the left small screen (laptop). Anyone know how to do this (i.e. actually has it working)? Post your xorg.conf.

I am using the fglrx driver with Big Desktop and I have my laptop as my secondary monitor (different resolutions too!) and everything is great ... except gaming.

I have attached my xorg.conf file for you or anyone that wants to see a working config.

My main monitor is a 19" CRT at 1600x1200 and off to the right side I have my laptop screen at 1400x1050.

I also tried the aticonfig dual-head setup but had the 'big square instead of cursor' issues on my CRT monitor. Gave up trying when it wasn't even fixed in the very latest ATI/AMD driver release.

pAntZ

---

### Post by henkiekarel on 2007-07-26
I had the same problems (mouse offset) with the fglrx driver included with Debian/etch  ( 8.28.8 ).

With me, the newest fglrx driver ( 8.39.4 at this moment) locks up my laptop when starting X.

I reverted to fglrx driver 8.36.5 for now, because that one does not have the mouse offset problem. When you go out of bounds on the smaller screen (my laptop screen) the mouse simply continues to travel on in space you can't see (which you notice by the fact that if you move the mouse back up again, it takes a moment before you see it again). This is not very elegant, BUT it prevents mouse offsetting from happening.

Hope it helps. For any questions mail me at henkiekarel NOSPAMPLEASE at sxw dot nl

---

### Post by riviereg on 2007-08-01
I get the same problem with ATI X300 and 8.39.4 ... 

How do you use HW cursor ?

---

### Post by sirwalken on 2007-08-08
hi i also have a ati tv wonder that i installed, 
and since i get a blurry square, or i cant see what i'm doing
 until i rotate the model, or zoom around a little.
( i work in 3d )the tv wonder sucks so if i uninstall it and reinstall nividea...?
(that probably won't work)
then i can give the tv wonder to an enemy i have :)
graaagghhh! 
here you can see the square bit, i selected the head area and moved the dragon,
but it retains the area under the "first click".
[IMG]http://aycu19.webshots.com/image/25378/2005495937969468309_rs.jpg[/IMG]

---

